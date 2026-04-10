# Constellation Context

*Last updated: 08 April 2026*
*Point Claude here for any work-related conversation.*
---

## The Company
Bioligical agents persist within a narrow range of physiological states (temperature, pH, glucose) that have emerged through the coarse of evolution to support survival and reproduction. In order to maintain these states, an agent must resist a natural tendency to disorder and thus minimize the long-term average of surprise associated with sensory exchanges with the external world.

Surprise is determined by the quality of predictions with respects to sensory inputs (sensations). Therefore to act in ways that reduce this uncertainty requires an internal generative model of the world.

This is, in order to remain within dynamic equillibrium an organism must construct generative models of the exteroceptive, proprioceptive, and interoceptive signals. 
Exteroception (sensory signals about the external environment)
Proprioception (sensory signals about the mechanical state of the body)
Interoception (sensory signals about the internal physiological condition of the body)

The goal of this company is to build a foundation model of human state trained on exteroceptive, proprioceptive, and interoceptive signals, and to learn the continuously evolving latent states that give rise to behaviour. To achieve this, we are collecting longitudinal, multimodal data from individuals in naturalistic (“in-the-wild”) environments. This includes continuous measurements of sensory, behavioural, neural, and physiological systems using a range of modalities—including audio, video, electroencephalography, photoplethysmography, electrodermal activity, eye tracking, and pupillometry. .

There are many potential applications of such a model. The ability to predict how an organism will behave in relation to its environment could enable, for example, the prediction of individual responses to cancer therapies, the identification of optimal targets for deep brain stimulation in depression, the design of personalised treatment strategies for treatment-resistant psychiatric conditions, and the estimation of disease risk years in advance. Each of these applications depends on accurately characterising an individual’s underlying state and modelling how it evolves over time in response to a changing environment.

**Founded:** 2025
**Location:** San Francisco
**Stage:** Early-stage, scaling data collection infrastructure

---

## My Role

I am a founding neuroscientist at Constellation, working alongside Mehdi Azabou (CTO) and Avery Krieger (CEO). My work operates across software engineering, computational neuroscience, and data science. My main objective and sole focus at this current stage is **scaling data collection**. This can be deconstructed into two components, (1) automatic data collection (2) validating and monitoring data collection quality and (3) increasing participant throughput. This falls under two aims:

Aim 1. EEG quality control and real-time monitoring (MVP completed)
Training a foundation model of human state requires large volumes of high-quality neural data, which in turn requires automating both data collection and quality control. To address this, I am building a real-time system that detects and diagnosises various sources of noise and artefacts in EEG recordings and surfaces actionable alerts to a monitoring dashboard. The alerts allow non-expert operators to diagnose and correct issues during acquisition that would otherwise require a technical operator such as myself, thus removing the dependency on highly trained EEG specialists. Eventually this system will also enable us to remotely deploy our collect data  across many recording states sites and for large volumes of participants.

Aim 2. EEG Metrics and behavioral Insights engine (currently in development)
Scaling data collection also requires a high throughput of participants. The most sustainable strategy is to provide individuals with "metrics" from their recording sessions, in order to motivate them to return for multiple sessions. To this end, I am developing a system that processes EEG recordings and extracts interpretable metrics related to cognitive, behavioural, and mental state, which can be returned to participants as insights. The goal is to create a feedback loop in which data collection generates value for the individual, thereby improving retention.

---

## The Team

| Person | Role | Focus |
|--------|------|-------|
| **Avery Krieger** | CEO | Drosophila neuropeptide neuroscientist. Oversees the grand vision for the company, fundraiser, investor-facing. My direct manager |
| **Mehdi Azabou** | CTO | Eminent neuroAI researcher. Software stack for multi-modal streaming, recording, syncing and storage. AI training and inference |
| **Killian** | Software Engineer | Fullstack — physically builds the software stack for data streaming, data recording, dashboard UI |
| **Claire & Tucker** | Infrastructure Engineers | Cloud computing, networking, streaming large data volumes over local network |
| **Sandhya** | Research Operations | Data collection oversight, participant recruitment/management, EEG setup, issue logging |
| **Julia** | Admin | Operations and administration |
| **Ian** | AI Researcher (intern) | Building contrastive embedding models for biometric and eye tracking data |
| **Matteo** | Founding Neuroscientist | Automating EEG data collection and QC, Developing EEG metrics/insights |

---

## Team Dynamics and My Working Relationship

My relationship with Avery and Mehdi is complex — they are my bosses but the vast amount of time we spend together means we have all naturally developed personal relationships that sometimes spill over into the murky backwaters of friendship. The first months (Sept 2025 – Jan 2026) were along many axis, extremely challenging for me personally. I carried bad habits from my PhD: going dark when stuck, over-perfecting deliverables, not communicating blockers, failing to scope tasks realistically. These were compounded by interpersonal dynamics with Avery that eroded my confidence, a TRT trough in January, and the general shock of transitioning from solo academic work to collaborative startup pace.

In January 2026, I was given a set of operational guidelines outlining an accountability framework that I must adhere to if I was to continue working at the company. The intent was to strengthen several meta-cognitive skills, including time management, communication, problem scoping and task prioritisation.

Up to that point, I had been experiencing significant anxiety about my performance. Having a clear, structured framework to work within was a huge relief and my mood and relationship with the rest of the team stabilised. I followed the protocol religiously and have since then received consistent feedback from both Mehdi and Avery that I am doing well. In the long term this moment marked a critical inflection point in my relationship with the company and the founders. At this moment in time the feedback on my trajectory has been very positive and I am happy at the company. Naturally, I remain aware that there is ongoing room for improvement and I continue to take my personal and professional growth seriously.

---

## Current Strategic Priorities (April 2026)

- Scaling longitudinal multi-modal data collection
- Automating data collection workflows (reducing operator-to-recording ratio)
- Developing the EEG metrics/insights engine
- Building real-time monitoring and alerting infrastructure
- Participant retention and engagement strategies

---

## Scientific North Star

The startup sits at the intersection of my long-term scientific goals: if behaviour arises from a multi-modal, multi-scale latent state, then Constellation is building the measurement infrastructure to actually access that state. The EEG metrics work connects directly to my PhD research on travelling wave modes — the question is whether those macroscopic flow patterns can serve as a basis for the neural component of the behavioural embedding, and how they interact with signals from other modalities.

See also: [[Academic Research Project Ideas]], [[03_Projects/EEG-Behavioural Metrics/EEG metrics|EEG Metrics]]

#constellation #work #context-hub
