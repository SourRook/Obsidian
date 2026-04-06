---

Metric engine overview

The goal of the metric engine is to **translate complex, multimodal neural and physiological data into insights** that help individuals better understand and eventually modulate their internal state by changing their behaviour.

The engine has four key functions:

- Unveil the internal states that exist within each individual (systems identification)

- Characterise how those states evolve under different conditions (future state prediction)

- and eventually support informed action through modulating their behaviour or changing their environment (control).

At its core, the metric engine exists to answer a simple question:

> “What is happening inside me, how does it change, and what can I do about it?”

---

## What the metric engine does

Under the hood, the metric engine transforms raw multimodal data into interpretable summaries (metrics) that describe how an individual’s internal state evolves over time.

Specifically, it:

- computes **features** from raw signals for different recording modalities,

- uses these features to identify recurring **states** of the organism,

- tracks **trajectories** through state space and **transitions** between states,

- and summarizes regularities in these dynamics as **metrics**.

At the lower levels the metrics are designed to describe an individuals state without making clinical or causal claims (Tier 1). At the higher levels (Tiers 2-3) these metrics capture patterns in how internal states relate to observable behaviors and features in the environment.

---


## Metrics tiered structure

The metric engine outputs different classes of insights organised into tiers, based on the **complexity of the insight**, the **amount of data required**, and the **granularity at which behaviour and internal state can be characterised**.

- **Tier 1 insights are purely descriptive.**
    
    These metrics summarise observed features, states, trajectories, and transitions without making claims about causality or intervention. They describe _what is happening_ and _what patterns recur_, but not _why they occur_ or _how to change them_.
    

- **Tier 2 insights introduce explanatory structure.**
    
    At this level, metrics characterise conditional relationships between internal states, behaviour, and environmental context. This is where we begin to ask _under what conditions_ certain patterns arise.
    

- **Tier 3 insights focus on control.**
    
    - These metrics describe how actions, interventions, and environmental perturbations influence a person’s internal state and state trajectories. At this tier, we begin to model how individuals can most effectively adjust their behaviour and environment to intentionally shift themselves towards a desired state (or away from undesirable ones).
    

In general:

- **Lower tiers require less data**, are cheaper to compute, and can be derived from short or sparse recordings.

- **Higher tiers require more data**, longer observation periods, and repeated exposure to relevant behaviours or interventions, since both causal relationships and control policies must be learned over time.

This tiered structure ensures that the system can deliver meaningful insights to participants across varying levels of data availability.

# Terminology

---

  

Before exploring the tiered system, we first define the core terminology used throughout this document, including what we mean by features, states, trajectories, and metrics.

## Feature

A feature is a statistical summary designed to captures a specific aspect of the structure of a raw signal recorded over a predfined window.

Examples:

- EEG feature: The oscillatory power of a band-limited EEG signal

- Pupillometry feature: Peak frequency of eye saccades

- Biometric feature: heart-rate variability

- audio feature: speech rate

- video feature: motion energy

Key property:

A feature is well-defined on its own but only becomes meaningful when _conditioned_. A feature is conditioned by comparing how it changes across time (e.g. relative to a baseline), or between conditions (e.g. task or rest), or against a reference population (e.g. healthy young participants vs old).

---

## Conditioning

**Conditioning** refers to the context in which a feature is interpreted, such as a task, time period, or reference baseline.

Conditioning does not change how a feature is computed; it changes how it is understood.

Examples:

- EEG feature conditioned: The band-limited EEG power _in alpha relative to theta_

- pupillometry feature: The frequency of eye saccades _during task compared to rest_

- heart-rate variability _in the morning compared to evening_

- audio feature: speech rate d_uring a work meeting compared to socialising_

- video feature: motion energy _after 30 minutes of intense exercise_

---

## Feature space

**Feature space** is the multidimensional space formed by combining multiple features within or across modalities. Each point in feature space represents the organism’s configuration at a particular moment in time.

---

## Trajectory

A **trajectory** is the time-ordered sequence of points traced through feature space.Trajectories describe how a person’s features evolve over time.

---

## State (observable state / organism state)

A **state** is a recurring configuration of brain-body signals, corresponding to groups of similar points in high-dimensional feature space.

States are identified by the repeated occupation of similar feature configurations over time. In practice, they can be identified through a variety of data-driven methods, such as clustering (e.g. agglomerative hierarchical clustering), or probabilistic models (e.g., hidden Markov models).

**Important:**

A state refers to an observed pattern in the organism, not a hidden variable or latent state as in a computational model.

---

## Transition

A **transition** is a change from one state to another, occurring as the organism moves from one group of similar points in feature space to a different group over time. Transitions may be abrupt, where the state changes quickly, or gradual, where the organism moves smoothly along a trajectory before entering a new state.

Patterns of transitions can be summarized using transition matrices, which describe how frequently the organism moves between different recurring states. Statistics of these transition matrices will form the basis for many of the metrics described in _Tier 1B_.

---

## Metric

A **metric** is a quantitative summary that describes properties of features, states, or transitions.

Metrics capture how often states occur, how long they last, how variable they are, or how they differ across behavioural and environmental conditions.

Metrics are the primary outputs returned to participants

---

## Normative distribution

A **normative distribution** is a population-level reference that describes how a feature or metric varies across many individuals. Norms are optional and are not required for interpreting within-person patterns or trajectories.

---

# 3 tier system for insights

---

The insights are structured into **three tiers**, with Tier 1 split into two.

### Tier 1A — State Snapshot (instantaneous description)

- Single-time or short-window descriptions of the brain and/or body.

- No causality (i.e. no statements such as state X is caused by Y environmental factor).

- No prescriptions (i.e. no statements like if you take a certain action you can increase your dwell time in state A)

  

Examples:

- current arousal state as measured by galvanic skin response (EDA)

- current attentional state as measured by dwell time in default mode network (EEG)

- current metabolic state as measured by motion energy (video)

- Predicted age from wearable devices (PpgAge)

  

### How a single state snapshot is valuable to participants

Lets think about what uncertainty this level of insight resolves

Level 1A answers:

> “What is happening inside me right now?”

This is a _state uncertainty_ problem. In everyday life, people routinely misattribute or misread their internal state:

- “Am I tired or just bored?”

- “Am I stressed or just focused?”

- “Am I disengaged or overloaded?”

- “Why does this feel hard right now?”

Level 1A can be thought of as reducing **interpretive ambiguity in the moment**. This has two downstream uses to participants:

1. **Self-calibration**
    
    - It provides an empirical reference for what the subject is experiencing internally.
    
    - This can be valuable when subjective awareness of internal state is degraded (for instance when someone is tired).
    

1. **Action gating**
    
    - Many actions we choose to take are only appropriate in certain states.
    
    - These information snapshots can help participants _avoid obviously bad decisions._
    
    - You do not need to know what caused a certain state to decide:
        
        - “This is not a good moment to push harder.”
        
        - “This is a good moment to start a demanding task.”
        
    

  

Other reasons to provide Tier 1A metrics to participants:

1. **Trust building between Constellation and participants**
    
    - If the system can correctly reflect how someone feels _right now_, they are more likely to trust our system and continue providing data in hope of receiving richer and more complex insights.
    

1. **Cost**
    
    - A single snapshot requires no subject history or context and doesn’t require a reference population / normative distribution so it can be deployed at low cost to first-time users coming to our working lab for a single day.
    

1. **Population coverage for foundation models (critical)**
    
    - Level-1 snapshot sessions are high-throughput, allowing us to collect data from many individuals over short time scales. This enables us to expose our foundation-model to many more uncommon phenotypes.
    
    - As our data collection scales, it will become important to identify which regions of the human state distribution are underrepresented in our data, and reorient data collection toward phenotypes that continue to improve model performance. Because Tier 1A insights can be generated from short, high-throughput sessions, a well-performing metric engine at this tier enables rapid iteration: we can quickly recruit participants, assess which types of states or phenotypes are missing, and adapt recruitment strategies accordingly.
    

  

---

## Tier 1B — Recurring states (across multiple sessions or days)

  

Tier 1A metrics cannot distinguish whether an observed state reflects a transient fluctuation or part of a longer-term trend. Without historical context, participants receiving snapshot insights may be vulnerable to over-interpretation. This can lead to questions such as:

- “Is this how I always am?” in response to an insight indicating low arousal.

- “I know I can be like this, but what I care about is whether I am improving or getting worse over time,” in response to an insight suggesting atypical memory encoding inferred from irregular eye-movement patterns.

These questions cannot be answered from a single snapshot alone. However, by collecting multiple snapshot measurements over time, we can build a clearer picture of how frequently certain states occur and whether their prevalence are changing over time

### What Tier 1B adds beyond Tier 1A

Tier 1A answers:

> “What state am I in right now?”

Tier 1B answers:

> “How frequent are these states and how do they change over time?”

  

Tier 1B aggregates many Tier 1A snapshots to reveal a kind of personal “weather report” for the brain and body.

By combining snapshots over time, Tier 1B reveals:

- **Baselines**: what is typical _for this person_
    
    _e.g., on an average day, you spend approximately 45 minutes in low-mood states._
    

- **Ranges and persistence**: whether certain states are brief or long-lasting
    
    _e.g., low-mood states below a defined threshold occur roughly once every X hours or days and typically last X minutes._
    

- **Recurrence and ordering**: common sequences and periodicities of states
    
    _e.g., this low-mood state often follows prolonged periods of high arousal, or tends to occur at similar times across days._
    

  

---

## A few reasons why this is valuable to participants (as distinct from 1A)

A single snapshot is difficult to interpret or potentially alarming without context (e.g., _“Why was my attention so low just now, and is this a problem?”_). Tier 1B metrics allows us to communicate whether a given state is common or rare for an individual, whether it is short-lived or persistent, and how today compares to their typical range of variation across days or weeks.

**People often sense that there are recurring patterns in their thoughts, emotions, and experience of the world, but it can be difficult to verify these impressions objectively**. Memory is also biased toward recent events, which can distort how patterns are perceived over time. Insights at this level help illuminate the objective structure of a person’s experience, providing a clearer picture of what is actually occuring and when.

**With this information, individuals can draw on their own knowledge of their environment and behaviour to attribute causes**_._ For example, a participant in one of our living labs may come to realise that their low-mood states occur more frequently at certain times of the day, and that this tends to coincide with when they are interacting with a particular person at work or on days when they have slept poorly.

Insights at this Tier therefore supports soft agency because having more precise knowledge of their internal state expands the space of possible actions and decisions that a person can take.

  

- “These states usually last ~30 minutes.”

- “This transition often happens once per day.”

- “This state tends to follow that one.”

This allows _soft agency_:

- choosing when to schedule demanding tasks,

- knowing when to wait things out.

  

Knowledge that our thoughts and emotions are constantly changing can lead us to peace by letting go of clinging. _"Whatever has the nature to arise will also pass away"._

  

Importantly, Tier 1B can deliver meaningful insights without relying on population-level normative data, as all comparisons are anchored to an individual’s own historical patterns. Population-based comparisons may be introduced later as the dataset scales, but they are not required at this tier.

  

---

## Concrete examples of Tier 1B insights

### Example 1: State variability

> “Across the last five sessions, your attention steadiness shows two modes: one highly stable and one highly variable. You spend about 60% of time in the stable mode.”

---

### Example 2: State persistence

> “When you enter a low-valence state, it typically persists for 20–40 minutes before resolving. Short dips (<10 minutes) are uncommon for you.”

---

### Example 3: State periodicity

> “Your sustained attention is most stable during the first half of the day and becomes more volatile later. This pattern appears consistently across sessions.”

---

### Example 4: State transition structure

> “You often move directly from a high-engagement state into a low-energy state, rather than transitioning gradually.”

---

### Example 5: Baseline comparison between states

> “Compared to your own baseline, you show higher-than-usual variability between states today compared to yesterday.”

---

  

Tiers 2 and 3 are outlined here for completeness; however, at this stage of the company, our primary focus will be on Tier 1 insights, as these can be developed and deployed quickly using existing open-source methods and software, and with relatively small amounts of data from our working labs.

## Tier 2 — Future state prediction

**Question answered:**

> “Under what conditions do these states arise?”

- Identification of **drivers, contexts, and early warnings**.

- Conditional structure (“when X + Y, Z is more likely”).

- Still careful about causality.

---

## Tier 3 — Control

**Question answered:**

> “What actions reliably move me from an undesirable state to a better one?”

- Personalized intervention policies.

- Timing matters.

- This is where autonomy is materially expanded.

# Metrics Catalogue

---

In this section, we systematically enumerate a set of viable metrics for each modality (e.g., neural, audio, biometric, video). For each metric, we describe how it is derived analytically, the estimated computational cost, the amount of data required to compute it reliably, and the expected timeline for developing deployable code—depending on whether the metric can be implemented using existing third-party software or requires in-house development.

Multimodal metrics—that is, metrics that combine information across multiple sensors, such as states and state trajectories defined jointly across neural and audio recordings—are addressed separately in the final section (_Multimodal Metrics_).

  

### Some brain storm ideas for simple / tractable metrics…

- **Focus steadiness**: “How stable was my attention today?” (stable vs scattered; lapses vs sustained)

- **Switching cost**: “When I multitask, do I degrade?” (not why; just that it happens)

- **Mental fatigue curve**: “How does my cognitive stability change over the day/session?”

- **Working memory strain**: “When does keeping things in mind start to wobble?”

### More ambitious (still Tier 1 feasible if framed descriptively)

- **Your personal focus “signature”**: “You have two distinct focus modes that you switch between; here’s what they look like.”

- **Early drift signature**: “There’s a detectable ‘on-ramp’ into lapses before you notice.”

- **Cognitive style fingerprint**: “You are fast-and-variable vs slow-and-stable (today/this week).”

- **Recovery responsiveness**: “Your focus rebounds quickly after breaks—more than you think / less than you think.”

  

### Emotional / affective insights people will value

### Simple

- **Arousal / stress load**: “How activated was my body today?” (with recovery speed)

- **Emotional volatility**: “How often did I fluctuate vs stay steady?”

- **Recovery dynamics**: “When I get activated, how long until I settle?”

### More ambitious

- **Mismatch awareness**: “Your body shows high activation even when your behavior looks calm (or vice versa).”

- **Hidden reactivity**: “Your physiology spikes in situations you don’t report as stressful.”

- **Emotional inertia**: “Once you enter low-valence patterns, you tend to stay there longer than you expect.”

- **Social-load imprint**: “Your signals look markedly different during speaking vs listening.”

(We can call this “social activation profile” rather than “anxiety.”)

- **Social**: speaking/listening balance, interruption tendency, conversational pace variability
    
    _People rarely see quantified versions of how they show up socially._
    

- **Environmental sensitivity profile**: “Your internal state is unusually sensitive to noise/light/number of people in the room (as measured by your signals).”
    
    _This feels like discovering a personal operating constraint._
    

- **Self-regulation bandwidth**: “How quickly can you shift from activated to calm within the session?”
    
    _Participants find this empowering even without prescriptions._
    

- **Cognitive–body coupling style**: “For you, cognitive strain shows up more in eye signals than physiology (or vice versa).”
    
    _This emphasise the importance/ uniqueness of having multimodal recordings that can help motivate more invasive / recording sessions ._
    

- **State repertoire size**: “You occupy a small set of stable states vs many fleeting states.”
    
    _This is could resonate with people with ADHD._
    
      
    
    The goal here is to impress people and thus increase the likelihood that someone will be willing to tolerate (a) more modalities and (b) longer term recordings. So it could be valuable to pick a small number of insights that showcase the possibilities of what we can do with more multi modal data.
    
      
    
    Plan:
    
    Record neural and physioligcal data from eye tracking (puppillometry), neural (EEG) and biometric data ( smartwatch).