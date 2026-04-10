
## Long-term Research Questions

### Travelling waves, structure, and function
- Can neuromodulator systems be recorded using travelling waves?  
  **Modalities:** HD-EEG + sMRI / PET

- Can brain structure be imaged through travelling waves?  
  **Modalities:** HD-EEG + sMRI

- Are brain networks or modes with higher levels of spatial frequency mixing correlated with emergent behaviours?  
  **Modalities:** HD-EEG

- Are modes derived from geometric structure, rather than dynamics, critical for constructing vector field dynamics? How does this compare with connectome-based structure?  
  **Modalities:** HD-EEG or fMRI + sMRI

- Can travelling wave modes provide a mapping between humans and animals?  
  **Modalities:** Wide-field electrophysiology + HD-EEG

### Dynamical systems and modelling
- Can Dynamic Mode Decomposition (DMD) be applied to divergence and curl fields instead of SVD, in order to extract controllable modes that can be perturbed via brain stimulation?

- Can a fluid-dynamic model based on Navier-Stokes equations provide governing equations for neural function?  
  **Modalities:** HD-EEG + neural mass modelling

- Can Hidden Markov Models identify recurring cycles or sequences of fundamental modes that occur during specific brain states or relate to cognitive performance?  
  **Modalities:** HD-EEG

- Spectral fundamental modes: can we compute the vector field directly on raw data and use a POD-like decomposition to extract spectral flow states, thereby avoiding arbitrary band-limit selection?

### Brain state transitions and mode sequences
- How does microscale activity, for example between hippocampus and thalamus, shape the transition probability, fractional occupancy, and mean lifetime of each state or fundamental mode?

- Are there circadian pacemaker cells for brain state transitions?

- How does this account compete with the idea that transitions are governed primarily by the systems-level energy landscape?

- A possible approach would be to build a neural mass model tuned to MEG data and test how activity in network hubs such as hippocampus shapes the evolution of the brain through mode space.

### Universality, cognition, and computation
- Can travelling wave principles be applied to neuromorphic computing, for example by encoding information as skyrmions?

- Is there a universal embedding for human behaviour?  
  Is there a universal grammar to the way wave patterns are organised across space and time that can be learned by a transformer?

- Is this grammar similar to the structure found in movement or human language?  
  Perhaps neural activity has a syntax and punctuation.

### Cycling dynamics and cognition
- Vidaurre et al. (2023) argue that large-scale cortical networks are organised in structured cycles over approximately 300–500 ms, and that phase within this cycle predicts reaction time.  
  Can this be linked to phase-locking concepts and used to test the effects of TI stimulation delivered at different phases of cycles between fundamental modes?

- Are there distinct clusters of cycling between fundamental modes?  
  For example:
  - one class related to sensorimotor processing
  - another related to resting or default-mode processing

### Redundancy, synergy, and wave type
- Luppi, Rossa, and Mediano found that some brain regions are more redundant whereas others are more synergistic. What properties make a region one or the other?

- We already suspect that long-range structure contributes to a system’s integrative capacity. But what determines whether individual regions are redundant or synergistic?

- One possibility is that this is partly explained by different wave types:
  - vortex waves may generate highly turbulent dynamics near singularities, potentially leading to nonlinear frequency mixing and integration/synergy
  - planar waves may recruit circuits in parallel and may be more related to redundancy

- We appear to see more planar waves in Alzheimer’s disease and with ageing.

- Are the complexity and diversity of wave patterns related to cognitive flexibility or fluid intelligence?

- Are certain wave types required for consciousness?  
  More specifically, what is the mechanism by which integrated information emerges in the human brain?

---

## Medium-term Goals
- Publish a gold-standard framework for analysing travelling waves in neural recordings
- Build a MATLAB wrapper
- Build a Dockerised version
- Demonstrate examples in mice calcium imaging and fMRI

---

## Short-term Goals
- Are fundamental modes of travelling waves conserved in mice?  
  **Potential output:** extra figure or supplementary analysis for the current paper

---

## Software Goals
- Confirm that all computations are correct
  - curl direction conventions
  - divergence sign conventions
  - numerical correctness
  - bug fixing and validation

---

# Project Options

## 1. Stability analysis of travelling cortical waves and their role in cognitive function

### Background
Large-scale neural activity in the human brain exhibits rich and complex wave patterns, but the organisation of these waves and their role in behaviour remains unclear. Recent work by our group developed a framework to unify the diversity of wave phenomena observed in electroencephalography (EEG) recordings. This framework suggests that neural activity can be understood as arising from parsimonious interactions between fundamental modes of travelling waves, including spirals, sources, sinks, and planar waves.

Spatio-temporal waves propagating across the cortical surface produce different classes of fixed points. For example, a wave spiralling into or out of a brain region can generate a stable or unstable fixed point, while multiple wave fronts can interact to produce saddle points.

Although much work has examined the role of individual waves in cognition, the stability analysis of multiple interacting wave fronts, and their relationship to cognitive function, remains largely unexplored.

### Project Description
This project will investigate the relationship between fixed points in spatio-temporal wave patterns of neural activity and cognitive function. Using ideas from dynamical systems theory and stability analysis, we will test whether the stable, unstable, and saddle points generated by interacting neural wave fronts are associated with cognitive performance and neurodegenerative disease, especially Alzheimer’s disease (AD).

We hypothesise that brain atrophy, a hallmark of AD, alters wave dynamics in ways that produce characteristic patterns of unstable and saddle points. These may be sensitive both to the extent of cortical degeneration and to the degree of cognitive impairment.

### Aims
1. Use phase-space analysis to map trajectories of travelling waves in EEG recordings.
2. Apply stability analysis to examine how interactions between travelling waves, including spirals, sources, sinks, and planar waves, generate equilibrium points.
3. Test whether equilibrium-point dynamics correlate with measures of cognitive function and brain atrophy in individuals with Alzheimer’s disease.

### Motivation
This project aims to identify spatio-temporal wave signatures associated with Alzheimer’s disease using EEG. EEG is non-invasive, cost-effective, and scalable, making it an attractive modality for identifying biomarkers for early detection and disease monitoring.

### Candidate Profile
We are looking for a highly motivated student who wants to strengthen their skills in computational neuroscience, mathematics, and programming.

### Skills
- Previous experience in Python or MATLAB is highly beneficial
- Basic knowledge of linear algebra and vector calculus is required
- Some knowledge of differential geometry is preferred but not necessary

### Supervision
- M. Vinao-Carl (PostDoc)
- Dr R. Peach (PostDoc)
- Dr M. Barahona / Dr N. Grossman (PI)

---

## 2. Deep brain imaging through scalp electroencephalography

### Background
The dynamics of many natural systems are fundamentally constrained by their underlying structure. The shape of a drum influences its acoustic properties, the morphology of a river bed shapes underwater currents, and the geometry of a protein determines which molecules it can interact with.

We previously showed that trajectories of neural activity, expressed as travelling waves across the cortex, are shaped by white matter connectivity, i.e. the structural connectome. We also showed that travelling waves recorded with EEG can predict the extent of subcortical atrophy in Alzheimer’s disease.

### Project Description
This project will use high-density EEG and structural magnetic resonance imaging (sMRI) from a dataset of approximately 61 participants to test whether the geometry and connectome of individual brains can be reconstructed from the equilibrium points and eigenmodes of travelling wave patterns observed on the cortical surface.

### Requirements
- **Programming:** Python / MATLAB (required)
- **Background:** linear algebra and vector calculus (required), differential geometry (preferred)

### Supervisors
- M. Vinao-Carl (PostDoc)
- R. Peach (PostDoc)
- Mauricio / Nir

---

## 3. Functional imaging of neurotransmitter systems through scalp electroencephalography

### Background
Neuromodulators such as dopamine, serotonin, norepinephrine, acetylcholine, and histamine are key regulators of large-scale neural activity and complex behaviour. However, direct imaging of neuromodulatory systems in humans remains limited.

### Project Description
We propose that the spatio-temporal dynamics of cortical travelling waves are shaped by the underlying distribution of metabotropic receptors. This project will test whether receptor population structure can be reconstructed indirectly from electrical wave patterns measured at the scalp.

Using high-density EEG and structural MRI from a cohort of Alzheimer’s disease patients and healthy controls (n = 61), the project will:
1. test whether different neurotransmitter systems can be inferred from wave dynamics measured at the cortical surface
2. test whether these inferred differences relate to disease trajectory and cognitive impairment

### Requirements
- **Programming:** Python / MATLAB (required)
- **Background:** linear algebra and vector calculus (required), differential geometry (preferred)

### Supervisors
- M. Vinao-Carl (PostDoc)
- R. Peach (PostDoc)
- Nir

---

## 4. A fluid-dynamic paradigm for the human brain

### Background
There are currently no accepted governing equations for neural systems, and the discovery of such principles would have major implications for experimental and clinical neuroscience, including diagnosis, forecasting, and control.

Recent work in our group suggests that neural activity observed in EEG recordings can be understood as arising from parsimonious interactions between fundamental travelling-wave modes, including spirals, sources, sinks, and planar waves. This raises the possibility that aspects of neural dynamics may be captured using fluid-dynamic equations.

### Project Description
This computational project will test whether neural models based on fluid dynamics, for example Navier-Stokes-like formulations, can reproduce the rich wave phenomena observed in empirical brain recordings.

---

## 5. Controlling the brain: real-time perturbation of dynamic modes of travelling waves

### Core Idea
- Compute AMVO
- Replace SVD with Dynamic Mode Decomposition with control (DMDc)
- Simulate control of divergence and vortex modes through TI perturbations

### Project Direction
This project would move from descriptive modelling toward controllability. The aim is to identify dynamic modes of travelling waves that can, in principle, be perturbed in real time using stimulation.

---

## 6. Nature computes better: biomimetic computing based on spatio-temporal wave patterns

### Background
Skyrmions are small, stable magnetic structures in which spins form swirling configurations. They have attracted interest as a substrate for unconventional computing because of their potential advantages in data storage, energy efficiency, and memory stability.

Recent work in our lab suggests that spatio-temporal neural waves may also be organised into skyrmion-like topographic structures and may play a key role in complex behaviours, including sensory processing, decision-making, and set shifting.

### Project Description
This project asks whether these biological principles can be used to improve neuromorphic computing hardware or algorithms.

---

## 7. From the cortex to the STN

### Background
Parkinson’s disease is a neurodegenerative disorder associated with neuronal loss in the substantia nigra (SN). In later stages it is often treated with deep brain stimulation targeting the subthalamic nucleus (STN). Early detection is critical, but diagnosis often occurs only after substantial neuronal loss.

### Project Description
Using a dataset of 9 Parkinson’s disease patients with structural MRI and 280-channel EEG, this project will apply methods developed in our lab for predicting deep-brain atrophy and test whether they can be used to infer neuronal loss in the substantia nigra.

This could provide a novel biomarker for Parkinson’s disease based on a cheap, accessible, and non-invasive measurement modality.

---

# Datasets

## OPENNEURO and related datasets

### VEPCON
**Title:** Source imaging of high-density visual evoked potentials with multi-scale brain parcellations and connectomes  
**DOI:** 10.18112/openneuro.ds003505.v1.1.2

- **N:** 20 healthy young participants
- **EEG:** 128-channel
- **Modalities:** high-density EEG, structural MRI, diffusion MRI
- **Task:** visual evoked potentials during face and motion discrimination tasks

### Cuban Human Brain Mapping Project
**Paper:** https://www.nature.com/articles/s41597-021-00829-7

- **N:** 282 healthy young and middle-aged participants  
  Mean age 31.9 ± 9.3 years, range 18–68
- **Modalities:**
  - high-density resting-state EEG (64–120 channels)
  - MRI
  - cognitive tests
  - demographic data
- **EEG conditions:** eyes closed, eyes open, hyperventilation, recovery
- **MRI:** T1 and diffusion-weighted imaging
- **Availability:** data available upon request  
  https://chbmp-open.loris.ca/

**Contacts:**
- pedro.valdes@neuroinformatics-collaboratory.org
- peter@cneuro.edu.cu
- pedro@uestc.edu.cn

### Nencki-Symfonia EEG/ERP Dataset
**DOI:** 10.5524/100990  
**OpenNeuro:** https://openneuro.org/datasets/ds004621/versions/1.0.1

- **N:** 42 healthy young participants
- **EEG:** 128-channel
- **Tasks:**
  - extended multi-source interference task (MSIT+)
  - 3-stimulus oddball task
  - simple reaction task
  - resting-state protocol

### High-density diffuse optical tomography dataset of naturalistic viewing
**DOI:** 10.18112/openneuro.ds004569.v1.0.0

- **N:** 58 healthy adults, age 18–76
- **Repeated sessions:** 36 participants, 106 total sessions
- **Task:** watched a 10-minute clip from *The Good, the Bad, and the Ugly* (1966)
- **Notes:** preprocessed data available

**Possible idea:** test reconstruction of movie features within subject

### Face processing MEEG dataset with HED annotation
- **N:** 18 healthy young participants
- **Modalities:** sMRI + EEG
- **EEG:** 70 channels
- **Task:** perceptual decision task using famous, unfamiliar, and scrambled faces

### Naturalistic auditory/visual stimuli + high-density EEG
**OSF:** https://osf.io/2ar9q/  
**Paper:** https://www.sciencedirect.com/science/article/pii/S1053811923004810#sec2

- **N:** 13 participants
- **EEG:** 256-channel
- **Modalities:** high-density EEG + structural MRI
- **Task:** movie viewing and auditory tone listening

---

# Notes

## Candidate Meta-projects
- Standardise travelling-wave analysis across EEG, calcium imaging, fMRI, and possibly HD-DOT
- Build a translational bridge from human EEG to animal electrophysiology
- Develop stimulation-ready dynamical models of divergence and vortex modes
- Test whether travelling-wave dynamics offer biomarkers for neurodegeneration and psychiatric disease
- Explore whether wave grammar provides a universal latent space for brain and behaviour

## Immediate Priorities
- Finish current paper
- Add mouse conservation result as supplementary analysis
- Validate software stack end-to-end
- Define strongest PhD/MRes project options from the long-list