**NeuroSentinel Real-Time EEG Monitor**  
Developer README

# **What is the neurosentinel toolbox?**

Neurosentinel is a library that monitors EEG signal quality in real-time. You feed it chunks of raw EEG data and it tells you when there is a change in signal quality, for instance when there is evidence of electrical interference from a power outlet (60 Hz line noise), or when channels have abnormal amplitudes, or when electrode contact is poor.

It is designed to run continuously during a recording session and alert you the moment quality degrades, so that an operator can take corrective action.

# **How It Works**

The library watches four signal quality metrics simultaneously:

| Metric | What it measures | Bad detection threshold |
| :---- | :---- | :---- |
| Line noise | 60 Hz oscillatory power above the noise floor after removing the EEG aperiodic component | Value \> 4 dB above background power spectral density. |
| Kurtosis | Non-neural signal artefacts typically have amplitude distributions with a positive skew | Value \> 5  |
| RMS amplitude | Flat electrodes / electrodes with no gel | Value \< 10e-3 |
| Max amplitude | Peak-to-peak swings (too high \= muscle artifact/movement) or poor impedance | Value \> 200 uV |

For each metric, the library:

* Computes the metric on a sliding window of recent data (e.g. the last 4 seconds)  
* Smooths it with an EWMA (exponentially weighted moving average)  
* Uses hysteresis thresholds: one upper threshold to enter a 'noise detected’ state, and a lower one to exit it. This prevents rapid flickering which can trigger alerts when the metric is hovering around a threshold.  
* Requires the condition to persist for multiple consecutive steps before raising an alert  
* Enforces a cooldown so the same alert is not repeated every second.

# **File Structure**

| File | What it does |
| :---- | :---- |
| config.py | All tunable settings in one place (window sizes, thresholds, EWMA smoothing parameter) |
| engine.py | This is the main class you interact with: RealtimeMonitor |
| metrics.py | Pure functions that compute each of the metrics from a data window |
| alerts.py | State machine: tracks good/bad state, applies EWMA and hysteresis |
| ewma.py | Simple online exponential moving average |
| example.py | End-to-end simulation you can run to see it in action |

# **Installation**

Install the required dependencies:

| pip install numpy scipy fooof matplotlib |
| :---- |

The library itself is a local package — no separate install step is needed. Just make sure the neurosentinel/ folder is on your Python path.

# **Quickstart**

Here is the minimal code to start monitoring:

| from neurosentinel._realtime import RealtimeMonitor, RTConfig<br><br><br># 1. Create a config (or use all defaults)<br><br>cfg = RTConfig(sfreq=500.0, n_channels=64)<br><br># 2. Create the monitor<br><br>monitor = RealtimeMonitor(cfg)<br><br># 3. In your data acquisition loop, feed chunks as they arrive<br><br>while recording:<br><br>    chunk = get_next_chunk()   # shape: (n_channels, n_new_samples)<br><br>    timestamp = current_time_in_seconds()<br><br>    states = monitor.update(chunk, timestamp)<br><br><br>    for state in states:<br><br>        if state.message:      # only set on state transitions<br><br>            print(f'{state.metric}: {state.message}') |
| :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

# **Understanding the Output**

Every call to monitor.update() returns a list of WindowState objects — one per metric that was evaluated on this chunk. Each WindowState has:

| Field | Type | Meaning |
| :---- | :---- | :---- |
| metric | str | Which metric: 'line\_noise', 'kurtosis', 'rms', or 'max\_amp' |
| state | str | 'good' or 'bad' |
| value | float | The EWMA-smoothed value of the metric right now |
| timestamp | float | The timestamp you passed in to update() |
| message | str or None | Human-readable alert text. Only set when the state just changed. None otherwise. |

The **message** field is your alert signal. It is **None** on every normal step. It is only populated when the state transitions from good to bad, or from bad back to good. Check state.message is not None to detect events.

# **Configuration Reference**

All settings live in RTConfig in config.py. Pass a customised config to RealtimeMonitor:

| cfg = RTConfig(<br><br>    sfreq=1000.0,              # Your EEG sampling rate in Hz<br><br>    n_channels=128,            # Number of EEG channels<br><br>  <br>    # How much data to analyse at once (per metric)<br><br>    line_noise_window_sec=4.0, # Use last 4 seconds for line noise<br><br>    line_noise_step_sec=1.0,   # Re-evaluate every 1 second<br>  <br><br>    # EWMA smoothing: higher beta = smoother but slower to respond<br><br>    ewma_beta_line_noise=0.85,<br><br><br>    # Hysteresis: enter bad state above 'enter', recover below 'exit'<br><br>    line_noise_enter=4.0,      # dB above aperiodic fit<br><br>    line_noise_exit=3.5,<br> |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

## **Key Thresholds by Metric**

| Setting | Default | Description |
| :---- | :---- | :---- |
| line\_noise\_enter / exit | 4.0 / 3.5 dB | FOOOF peak height above aperiodic background at 60 Hz |
| kurtosis\_enter / exit | 5.0 / 4.0 | Mean absolute excess kurtosis across channels |
| rms\_enter / exit | 1e-3 / 1e-3 uV | Mean RMS — bad when too LOW (dead channels) |
| max\_amp\_enter / exit | 200 / 150 uV | Mean peak-to-peak amplitude across channels |
| impedance\_bad\_threshold\_kohm | 30.0 kOhm | Median electrode impedance |

# **How Each Metric Is Computed**

## **Line Noise (line\_noise\_db)**

Uses the FOOOF (fitting oscillations and one over f) algorithm to separate the periodic (neural) and aperiodic (1/f noise floor) components of the power spectrum. The metric is the height in dB of the peak detected in the 58-62 Hz band above the fitted aperiodic background. A high value means there is a strong 60 Hz signal that is not explained by normal brain activity.

## **Kurtosis (channel\_kurtosis)**

Computes the excess kurtosis of each channel's time series and averages across channels. High kurtosis means there are rare but very large spikes — a sign of eye blinks, muscle artifacts, or amplifier saturation.

## **RMS Amplitude (channel\_rms)**

Root mean square amplitude per channel, averaged. This is a baseline sanity check: if RMS drops very low it usually means one or more channels has gone flat (broken wire, disconnected electrode).

## **Max Amplitude (channel\_max\_amplitude)**

Peak-to-peak range per channel, averaged. Excessive amplitude usually indicates muscle artifact or electrode pop.

# **Running the Example**

The file example.py runs a 60-second simulation with synthetic EEG. It adds a 60 Hz line noise signal that toggles on and off every 2 seconds, then plots the raw signal, the EWMA-smoothed line noise metric, and a per-channel RMS heatmap.

| python example.py |
| :---- |

This produces example\_output.png in the same folder — a three-panel figure showing the raw signal, the EWMA line noise trace with alert thresholds, and the per-channel RMS heatmap over time.

# **Practical Tips**

* Start with the defaults — they are calibrated for a 500 Hz, 128-channel EEG system with typical impedances.  
* If you are getting too many false alarms, increase min\_steps\_to\_enter (e.g. to 3-4) or raise the enter threshold slightly.  
* If alerts are too slow to fire, lower ewma\_beta (e.g. 0.5) for faster response to changes.  
* Call monitor.reset() between recording blocks or subjects to clear all internal state.  
* The monitor keeps an internal circular buffer of recent samples. You do not need to manage windowing yourself — just keep feeding chunks.  
* Chunk size does not matter — you can pass one sample at a time or a second of data at once.

# **Architecture Summary**

Data flows through the system in this order:
Your EEG device

    |

    v  chunk = (n_channels, n_new_samples)

RealtimeMonitor.update(chunk, timestamp)

    |

    +--> Circular buffer (stores recent samples)

    |

    +--> metrics.py  (compute raw scalar per metric from window)

    |

    +--> AlertEngine.update(metric, raw_value, timestamp)

              |

              +--> EWMA smoothing

              +--> Hysteresis state machine

              +--> Persistence counter

              +--> Cooldown check

              |

              v

         WindowState (metric, state, value, timestamp, message)

**
```

When you create a `RealtimeMonitor`, it allocates a fixed-size numpy array `_buf` shaped `(n_channels, capacity)` where capacity is the largest window across all metrics (e.g. 10s × 1000 Hz \= 10,000 samples). This is a ring buffer meaning that it never grows, it just overwrites old data. `_write_pos` tracks where the next chunk gets written, and `_n_filled` tracks how many samples have been written so far (capped at the buffer capacity).

**`update(chunk, timestamp)`**

This is the only method you call in your loop. Every time you call it:

1. The chunk gets written into the ring buffer via `_append()`  
2. For each metric, the counter increments by however many new samples arrived  
3. If the metric's window hasn't filled yet (`_ready` is False), skip it  
4. If the step counter hasn't reached the threshold yet, re-emit the last known state with the updated timestamp  
5. If the step counter fires, grab the latest N samples from the buffer, compute the metric function, pass the scalar to the alert engine, reset the counter

So if `step_sec=1.0` at 1000 Hz, each metric fires once every 1000 samples regardless of chunk size.

---

**`_get_latest(n_samples)`**

Extracts the most recent N samples from the ring buffer. Because it's circular, the "latest" data might wrap around ( e.g. the last 5000 samples might span the end and beginning of the array). It handles that with the `concatenate` branch.

---

**The alert engine (in `alerts.py`)**

The current state of the system is defined and set by the engine when it calls `self._alert_engine.update(name, scalar, timestamp)`. When this happens:

* The raw scalar gets fed into an **EWMA** to smooth the feature scalar over all samples in the ring buffer (i.e. this context window).  
* The smoothed value is compared against **hysteresis thresholds** — a high threshold to enter "bad", a lower one to exit, preventing rapid flickering  
* A **persistence counter** requires the condition to hold for `min_steps_to_enter` consecutive steps before raising an alert  
* A **cooldown** prevents the same alert from firing repeatedly

It returns a `WindowState` with the metric name, current state (`"good"` or `"bad"`), the smoothed value, timestamp, and a message only when state transitions occur.

# **Future fixes:**

Currently the EWMA doesn't know anything about time. It just sees a sequence of scalars, one per step. So the effective time constant depends entirely on how often steps fire.

With `beta=0.85` and `step_sec=1.0`, each update represents 1 second, so the EWMA has a time constant of roughly:

```
τ = step_sec / (1 - beta) = 1.0 / 0.15 ≈ 6.7 seconds
```

But if you change to `step_sec=0.5` (fires twice per second), the same `beta=0.85` now gives:

```
τ = 0.5 / 0.15 ≈ 3.3 seconds
```

Same beta, half the time constant — the EWMA reacts twice as fast just because steps are more frequent.

This means **beta and step\_sec are coupled**. If you change one you should adjust the other to maintain the same effective smoothing. The correct way to set beta for a desired time constant `τ` is:

```py
beta = 1 - (step_sec / tau_desired)
# e.g. tau=10s, step=1s → beta = 1 - 0.1 = 0.90
# e.g. tau=10s, step=0.5s → beta = 1 - 0.05 = 0.95
```

Ideally `RTConfig` would expose `ewma_tau_sec` instead of raw `beta`, and compute beta internally from tau and step\_sec so users don't have to think about the coupling. This functionality will be added in future patches.

