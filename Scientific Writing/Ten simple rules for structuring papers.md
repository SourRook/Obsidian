# Ten simple rules for structuring papers

# Rule 1: Focus your paper on a central contribution, which you communicate in the title

- Focus *on a single message*

Papers that simultaneously focus on multiple contributions tend to be less convincing about each and are therefore less memorable.

This Rule of One:  make the claim and/or model as simple as the data and logic can support but no simpler. In the end, your struggle to find this balance may appropriately result in “one contribution” that is multifaceted. For example, a technology paper may describe **both its new technology** and **a biological result using it**; the bridge that unifies these two facets is a clear description of how the new technology can be used to do new biology.

Novel contributions

What we did + what we found

1. Divergence and vorticity flowfields are conserved in the human cortex
2. Dynamically combining these flowfields govern cognitive functions

Spatial patterns of divergence and vortex flow are conserved in the cortex and give rise to distinct behaviours

Routing of cortical activity through

*What is your one sentence summary of this work?*

*Ans:*

# Rule 2: Write for flesh-and-blood human beings who do not know your work

1. Make the reader care about the problem we are addressing
2. Do not use jargon and technical terms without clearly defining. Avoid abbrev and acronyms that the readers have to go back to earlier sections to identify / define
3. Repeat the message and beginning and end of intro
4. Limit claims / ideas to what humans can hold in working memory
5. Open with the problem statement in discussion

Think like a designer—for each element, determine the impact that you want to have on people and then strive to achieve that objective

Try to think through the paper like a naïve reader who must first be made to care about the problem you are addressing (see Rule 6) and then will want to understand your answer with minimal effort

Try to think through the paper like a naïve reader who must first be made to care about the problem you are addressing (see Rule 6) and then will want to understand your answer with minimal effort

Humans are better at remembering the **beginning and the end of a list** than the middle

# Rule 3: Stick to the context-content-conclusion (C-C-C) scheme

Use CCC

- Set up context -> why was i told that (if context is missing)
- Content- Advances the story
- Conclusions - the problems finds their conclusions -> why was i told that (if context is missing)

The vast majority of popular (i.e., memorable and re-tellable) stories have a structure with a discernible beginning, a well-defined body, and an end. The beginning sets up the context for the story, while the body (content) advances the story towards an ending in which the problems find their conclusions. This structure reduces the chance that the reader will wonder “Why was I told that?” (if the context is missing) or “So what?” (if the conclusion is missing).

Present the most exciting content first (e.g., as seen in news articles) -> Title. But use CCC for the rest of the paper

The C-C-C scheme defines the structure of the paper **on multiple scales**. At the whole-paper scale, the introduction sets the context, the results are the content, and the discussion brings home the conclusion. Applying C-C-C at the paragraph scale, the first sentence defines the topic or context, the body hosts the novel content put forth for the reader’s consideration, and the last sentence provides the conclusion to be remembered.

# Rule 4: Optimize your logical flow by avoiding zig-zag and using parallelism

- Avoid zig-zag
- Using parallelism
- Repeat words are OK

Only the central idea of the paper should be touched upon multiple times.

Otherwise, *each subject should be covered in **only one place** in order to minimize the number of subject changes.*

Ideas that are similar, such as two reasons why we should believe something, *should come one immediately after the other.*

if we have three independent reasons why we prefer one interpretation of a result over another, use same syntax, and sentence / paragraph structure. When the structure and syntax are simple and transparent the reader will find it easier to focus on the content

*There is nothing wrong with using the same word multiple times in a sentence or paragraph.* Resist the temptation to use a different word to refer to the same concept—doing so makes readers wonder if the second word has a slightly different meaning.

# The components of a paper (Rules 5–8)

There are 3 spatial scales for structuring a paper: across **sections,** across **paragraphs**, within **paragraphs**

Note that the abstract is special **in that it contains all three elements** (Context, Content, and Conclusion), thus comprising all three colors.

# Rule 6: Communicate why the paper matters in the introduction

- Gap that exists in current knowledge and method
- Why this gap is important (iterate through set of progressively more specific paragraphs that culminate in a clear exposition of waht is lacking in the literature, then end by a paragraph summarizing **what the paper does to fill the gap:**

Example:

Paragraph 1: Explain why have a single coordinatre systtem to explain all human brain dynamics is important and provide evidence that this is an unsolved problem

Paragraph 2: Explain what specifically is unsolved (introduce the notion of basis functions i.e. coordinate system and why it presumed that there cannot be a single set of coordinates or basis functions for all humans) → but maybe allude to the fact that foudnation models etc must be discovering these otherwise how could we have generative models that generalise ?) What specifically is the mathematica/ computational problem in discoverin these (is it looking at the activity rather than the activity gradient?) Is it that the brain is an extremely non linear system (the anna karenina paradox, all linear systems are alike all non linear systems are uniquely different).

How has this problem been solved previosuly → Dimentionality redutions across the popatulinto find eigenmodes or basis functions to express the entire cohort, but these are cohort specific and dont generalise outisde of the recording, for instnace the fMRI has a set of canonicl networks which are highyl conserved and these spatial networks can be found across diverse brain state and neuropathological conditions (we can express all BOLD fluctuations exist in a space that span the subsapce spanned by these basis funcrtions) → this si what we mean by a coordinate system, but there is no coordinate system for eletorphysiolgicla recordings that are universal. To solve this groups often take the embeddings and try to align them in the latent space .. but this has limitation X (subfield gap)

We also have bassi functions that start with the geometry (e.g,. Pang et al.,) so we can express the BOLD signals as spanning some subspace spanned by these geometric basis functions.. but limition Y

Spatial

In all these cases we start with raw neural signals and perform dimentioanlity reduction (linear/. non linear) and then do something with these latents (networks or eigenmodes)

Eigenmodes

Basis functions

coordinate system

### Title

### Abstract (CCC)

A central goal of systems of neuroscience is understanding how information flow is coordinated among large populations of neurons to shape behaviour. However, recording same populations of neurons at different time points and in individuals is challenging, and the same populations give rise to different behaviours in different individuals, interpreting large-scale neural activity via comparisons of activity patterns across individuals and across time points is challenging. Therefore the alignment of low-dimensional latent representations is necessary to properly compare high-dimensional neural activities across time, across subsets of neurons and across individuals

the abstract’s structure is highly conserved. Do nto deviate from C-C-C

*Intra-paragraph*

The **one** question is… (context) → this absolutely must communicate to the reader what gap the paper will fill

The first sentence orients the reader by introducing the broader field in which the particular research is situated. 

Then, this context is narrowed until it lands on the open question that the research answered. 

A successful context section sets the stage for distinguishing the paper’s contributions from the current state of the art by communicating what is missing in the literature (i.e., the specific gap) and why that matters (i.e., the connection between the specific gap and the broader context that the paper opened with).

**Here we do (content)**

The content (“Here we”) first describes the novel method or approach that you used to fill the gap or question. 

**What we found (content)**

Then you present the meat—your executive summary of the results.

**How it matters (conclusion)**

Finally, the conclusion interprets the results to answer the question that was posed at the end of the context section. There is often a second part to the conclusion section that highlights how this conclusion moves the broader field forward (i.e., “broader significance”). This is particularly true for more “general” journals with a broad readership.

Most common mistake with the abstract, which is to talk about results before the reader is ready to understand them. Do not do this!!!

### Intro

This entire section is about *context*

**Big problem in science** - > Field domain (context)

The Neural Correspondence Problem (NCP) and the need for alignment.

The study of brain function and cognition relies on the measurement and interpretation of changes in brain activity. Analyzing of the behaviours of large populations of neurons are required to understand brain states in health and disease1, or to differentiate, for example, between novice and expert performance in a complex task2, or between states of wakefulness and sleep3. However, comparing neural recordings across subsets of neurons, across subjects, or across time points is challenging, owing to extrinsic factors such as recording instabilities arising from diferent electrode placement on the scalp, to intrinsic difference in neural architecture due to neurodegeneration and plasticity.

Historically, neuroscientist compare neural-activity patterns between recordings by extracting features form neural population signals such as amplitude or phase and comparing how these features of neuronal activitty shifts across conditions (for instance, during learning, attention or movement4,5). One challenge with this aproach ist that the brain is a highly complex system and a key charavetsic of complex systems is that their behavior is determined  by a variety of dunamics that occur across multiple spatial and temporal scales . As a result, the impact of different behavioral conditions, perturbations or disease states involves complex effects across the entire brain from local circuits to large-scale networks. 

The problem si taht modelling the collective influence of a given perturbation or of a particular change in neural state requires algoirthhsm to compute (i) higher-order dependencies between large numebrs of nodes, (ii) computing their causal (directed) interactions and (iii) mapping this interactions across scales. Whoil;e Over the past two decades, increasingly sophisticated analytic methods have been developed to  compute higher-order dependencies 7–9, multi-scale interactions, and causal information flow or directed connectivity. exhaustively mapping the parameter space of interaction order, directed connectivity across scales is prohibitively expensive and therefore these need to be choses a prioro. HJoweber in many cases (if not in most) it is impossible to know in adance which brain region are relevant for a given behaviour, or equallywhich frequency to choose from an anlaysis and what causal interactions between brain regions or bands to test . And even if it were possible iy it may be fundamentally impossible to compare  directly between two subnjects if the function of a brain oscillation with a arptouclar frequecny could index into different brain networks and subserve  different behaviours oin two  individuals .

Historically neuroscientists have sought to compare two recordings of neural activity by first assuming a causal connection between pairs of neurons  or brain regions (nodes) whos activation co-vary similarly across recordings, and then by comparing the changes in activity in a particualr frequency band across these pairs of nodes. However, in many cases (if not in most) it is technically difficult to choose which brain regions are to be recorded from a priori. The brain is a complex interconnected multi scale network it cannot always be known a prioi what is the most important  spatial or tempora scale to record and analyse from  for a given task or behaviorla paradigm. 

The alternative is to summarize each recording in a way that is invariant to the specific subset of neurons that is recorded. Many existing strategies build invariance to the exact sets of neurons recorded by computing interactions or correlations of firing10–12, and then extracting various metrics, such as entropy, connectivity and criticality13,14. These approaches can be informative when there are suitable metrics to compare across conditions. However, data-driven strategies that identify couplings across multiple neurons would provide an even richer multidimensional picture of changes in neural circuits. 

To tackle the problem of neural-activity correspondence, a potential approach is to first find a representation of the neural activity  Check for updates  Control Perturbed  Low-dimensional manifolds  Dimensionality reduction method  Data set A Data set B  Fig. 1 | Comparison of patterns of neural activity via the alignment of their latent spaces. The schematic shows the generation of two latent spaces (oval shapes, bottom) from data sets corresponding to two neuronal states (control and perturbed) by means of dimensionality reduction. The alignment of the latent spaces (indicated by the yellow and orange lines) indicates that the data sets share a common structure despite having unique detectable differences. Figure adapted from ref. 89; credit for original image: Benjamin Dewey, Eva Dyer. produces a concise representation of a sequence of activity from which the sequence can be faithfully reconstructed) to improve estimates of trial-averaged neural states in individuals, and to identify stable low-dimensional structures in neural activity across multiple individuals performing the same motor task20. Incorporating temporal information can, in fact, yield latent factors that are more stable across trials, recordings and subjects and, crucially, that are also more interpretable.  Latent spaces cannot be directly compared  A critical assumption in the use of a latent-space model to compare two neural recordings is that their latent spaces provide an adequate representation of what is driving the activity of the neural circuit. When comparing two sets of neurons encoding similar information, it is typically assumed that there are representations of their latent spaces in which the activity of the neurons is similar. The objective is to find these representations so that both data sets can be placed into a common reference frame. Unfortunately, the latent spaces of two data sets of neural recordings encoding the same information may be substantially different. This is because, to differentiate signal from noise (variability in neuron firing, as well as interference from other neural circuits) and to infer latent factors, each dimensionality-reduction technique relies on assumptions about how information is encoded. Without a complete understanding of the brain’s encoding strategies, such assumptions are (at best) approximations. For example, PCA associates latent factors with the patterns of neural activity that account for as much of the population’s variance as possible. When the patterns of interest are roughly equally important — that is, when they are responsible for similar levels of variability in neural activity — relatively insignificant changes in the activity of a few neurons can reorder these patterns. This leads to latent spaces that encode the same information but that must be transformed to match each other (Fig. 2). In more sophisticated methods of estimating latent factors, the ordering of factors (by significance of their contributions to neural activity) is typically not unique, and comes down to particularities of the algorithm. Moreover, latent factors that are common across recordings may be obscured by additional unrelated neural activity. Moreover, the difficulty of tracking particular neurons in long-term recordings or of matching them across time after spike sorting can give rise to instabilities40–42. This can also introduce changes in the latent factors that are dominant, making direct comparisons of recordings across neurons in acute measurements or across individuals impossible. All of these challenges make direct comparisons across latent factors difficult, and highlight the need for alignment: similar brain states in two data sets of neural recordings need to be placed in the same latent space.  Finding correspondence across distinct neural recordings In this section, we discuss four strategies to alignment. They rely on different assumptions about the shared structure of the data sets or on partial information about correspondences (either across neurons or across time).  Global distribution of latent states. Assuming that latent spaces that may have a different ordering are comparable introduces the need for building in rotational invariance, or for finding the best rotation of the latent factors that maximally aligns the source and target data (Fig. 2b, c, right). One way to address this problem is to find a mapping from one  that is more ‘abstract’ than the firing of individual neurons, and then compare different neural data sets through their representations (Fig. 1). Suitable representations can be constructed by approximating the activity of each neuron as being driven by a combination of a small number of latent factors — that is, low-dimensional representations of the high-dimensional data describing coordinated activity across populations of neurons15. After each data set has been fitted with a latent model, if the circuits are performing similar tasks their latent models could be suitably compared. A substantial body of evidence shows that there are many settings in which latent factors are stable and can be tracked across subsets of neurons and across time points, and even across individuals8,16–23. This suggests that these latent models may be powerful for comparing data sets of recordings of neural activity. However, even when latent factors preserve the essential features of the neural activity, small perturbations in the data caused by electrode-driven instabilities and neuronal biology can lead to the divergence of otherwise similar latent representations. Alignment techniques can correct latent representations so that they can be suitably compared.

The study of brain function and cognition relies on comparing brain states across humans. Comparing the dynamics across large populations of neurons is critical to understand transitions from healthy to disease states or for instance to unveil the neural substrates of performance in a complex task. However, comparing the dynamics of large populations of neurons across individuals and over time is challenging. This difficult, herein referred to as the Nerual Correpsondence Problem (NCP) arises from several factors, owing to recording instabilities such as electrode placement,  shape that no two neural recordings are ever reocrding form exactly the same neurons. However even in idealised Furthermore, the brain is a complex interconnected network of non-linearly interconnecting components. These components are coordinated across multiple spatial and temporal scales. Thus effect of different experimental manipulations / conditions on neural activity are  highly hetoregenous, which makes direct compariosn of  population activity across subjects  challenging. This difficulty is commonly referred to as the neural correspondenc problem (NCP), and arises beacuse 

Therefore the alignment of low-dimensional latent representations is necessary to properly compare high-dimensional neural activities across time, across subsets of neurons and across individualsRecording

and changes in plasticity over time mean that no

**Current Solutions to NCP**

Historically, neuroscientists have sought to compare population activity between recordings by extracting the firing rate, amplitude / phase or other feature sof neuronal activity and mapping these statistical properties to a behavioral outcome, or compare these features between two experimental conditions (for instance healthyt vs control) behavioral conditions (e.g. before vs after learning) or under some interventions (stim v sham) .

**The need for a universal coordinate system**

**Embracing heterogeneity**

One alternative is to summarize each recording in a way that is invariant to the specific subset of neurons that is recorded, for example by building invariance by computing interactions or correlations of firing10–12, and then extracting various summary metrics, such as entropy, average degree connectivity or criticality13,14.These approaches can be predictive when there are suitable metrics to compare across conditions but because they are seocnd order statistics they are  difficult to interpret mechansitically (whether they are just a concise description of activity,) and unlike the amplitude or phase they can only be modulated indirectly. 

A second alternative is to use data-driven strategies to identify couplings across multiple neurons would provide and provide a richer multidimensional picture of changes in neural circuits. Commonly this is done by summarize each recording in a way that is invariant to the specific neuronal populations that are recorded, by extracting latent representations that preserve key structures within neural data. However, these dimensionality-reduction approaches are typically unsupervised and the latent factors learned can be hard to interpret. Even with supervised labels or training data (such as movement kinematics, sleep states or behavioural states), it can be hard to know when a latent-space model suffices to describe the structure of the data. Furthermore, it is unclear when latent factors should be considered to be intrinsic to the functions of a neural population or whether they are just a concise description of activity, and these latent factors are difficult to interpret because they do not correponding directly to things like neural firing rate or amplitude that can be modulated directly e.g. via brain stimulation, we cannot “perturb” a latent factor int he same way as we can perturb the firing rate through electrical stimiulation and this is a problem for interpretability that limits the ulity for brain interventions. Therefore data-driven strategies that identify highyl conserved organisation structures across popatuliosn and across scales that do not require alignment in the latent space could provide an even richer multidimensional picture of changes in neural circuits and their relationship to behaviour.

Herew we propose a solution to this problem. Just as in a river where the the amplitude of the river at each moment in time varies continsuuly, yet the contours of the river give rise to a continuous predictable spatial pattern of flow that is stable over time, we theorised that the extreme density and overlap of microscopic white-matter fibres in the brain would give rise to a macroscopic flowfield of neuronal activity at the macroscale in such a way that even though the activity at each point in space is dynaic and lfucations the overall pattersn of flow are invariances ove rtime and even across the human population. We theorised that we these stable patterns of flow can be used as low-dimensional latent representation  that would allow any two subjects to be  directly compared without needing to align these subjects within a shared latent space. 

To achieve this we developed a computational strategy based on the *unit phase vector field of the human encephalogram (EEG). In this approach,* we extrac tht einatnsoue phase from the EEG via the hilebrt transform and compute the spatial gradient of the instantenous phase to yield a time-varying vector field that encodes the local direction and rate of phase progression across the cortex. The phase gradient is then normalized at each spatial location to unit length, producing the unit phase vector field F(r,t)=r,t=∇ϕr,t/∇ϕr,t, which characterizes the direction of flow independent of the strength, akin to mapping the layout of the river independent of flow magmitude or the layout of a city while ignoring the volume of traffic. As we cannot perform dimentioanlty reductionon this three dinetnal vector field we first w decompose the vector field to a scalar divervence and vortex field from which we compute our latent factors through lienar idmentioanlty reduction , principle component analysi (PCA). We therosied that this tranformation of the EEG to the unit phase vector would allow us to identify shared laten represntions from a simple linear dimentianltiy reduction.These repreanttisosn wdoule bd reictly interpretable because they drectly correspond to phsyical aspects of neural function Higher-order interactions are found around fixed points (sources, sinks, saddles, spirals) arising from nonlinear coupling among neighbouring regions32; (ii) directed communication can be inferred by tracing the vector streamlines 33; and (iii) multiscale communication can be computed through eigendecomposition of the field into patterns of signal flow spanning from low to high spatial frequencies34.

> 
> 

---

## Why this now works (conceptually and mathematically)

- **Intuition → mathematics → consequence** is explicit
- “Flow” is not metaphorical; it is operationalised via phase gradients and operators
- The **shared coordinate system** is defined *before* dimensionality reduction
- Interpretability follows from **field theory**, not post hoc explanation
- The reader understands *why* alignment is no longer necessary

If you want, next I can:

- Compress this into a **Methods opening paragraph**
- Add a **short formal definition box** (for mathematically trained readers)
- Rewrite it in a **Nature/Science “conceptual framing” style**
- Explicitly contrast this with **CCA / hyperalignment / shared latent models** in one paragraph

Here we propose that this invariance macroscopic brain activity as a vector field. In a vector field each point encodes the direction and magnitude of signal flowm thereby capturing directed connectivity30, and performing eigendecomposition on this vector field produes a family of basis functions that natural span from low to high spatila frequencies thereby providing a set of coordinates describing neural activity across multipel spatial and temporal scales.  Furthemore a vector field naturally can be used to undestand Higher-order relationships by analysing fixed points (sources, sinks, saddles, spirals) that arising from nonlinear coupling among large numbers of neurons. 

 the activitty flow at the macroscopic level that are not present in Flow fields are a

Must converge:

latent factors

dynamical basis function

eigenmodes

patent representations

modes

 exhibit mixxed selectivity m

**Narrower problem within** → What the field knows (content)

**Yet narrower paper Gap →** What the remaining gap is (conclusion)

**Summary** → Our approach (content) + Our results (conclusion

### Results

**Methods Summary**

- Our question (context)
- General methods (content)
- Answer sought (conclusion)

**Logic 1 (raw data) , Logic 2 (processed) … Logic N (final statistics)**

- We need to show… (context)
- That is how we show… (content)
- We thus know… (conclusion)

Figs support logic step

### Discussion

**Results → Conclusion** 

We found **(content)** → we filled the gap **(Conclusion)**

**Limitations in filling gap** 

Our limitation **(context)**, Details **(content)**, How to interpret / fix **(Conclusion)**

**Limits in generalisation** 

Our limitation **(context)**, Details **(content)**, How to interpret / fix **(Conclusion)**

**Science is better now** 

Our strength **(context)**, What it is useful for **(content)**, The difference made **(Conclusion)**

But it should also adhere to CCC

P1 - defines the topic or context

P2 - hosts the novel content put forth for the reader’s consideration

P3 -  provides the conclusion to be remembered

Each paragraph should also have this structure!!

Results

Discussion