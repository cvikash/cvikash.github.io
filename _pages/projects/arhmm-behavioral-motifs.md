---
title: "Behavioral motifs identification in freely swimming zebrafish using autoregressive hidden markov models (ARHMMs)"
layout: page
permalink: /projects/arhmm-behavioral-motifs/
classes: wide
---

<section class="page-hero">
  <div class="container">
    <h1 class="page-hero__title">Behavioral motifs identification in freely swimming zebrafish using autoregressive hidden markov models (ARHMMs)</h1>
    <p class="page-hero__subtitle">Decoding behavioral states from high-resolution tracking data using machine learning</p>
  </div>
</section>

<section class="page-content">
  <div class="container">
    <!-- GitHub Info -->
    <div class="content-card" style="background: linear-gradient(135deg, rgba(26, 86, 219, 0.05) 0%, rgba(14, 165, 233, 0.05) 100%); border-left: 4px solid var(--color-primary);">
      <div style="display: flex; justify-content: space-between; align-items: start; flex-wrap: wrap; gap: 1rem;">
        <div>
          <p style="margin: 0; color: var(--color-text-muted); font-size: 0.9rem;"><strong>Project:</strong> Autoregressive Hidden Markov Model implementation</p>
          <p style="margin: 0.5rem 0 0 0; color: var(--color-text-muted); font-size: 0.9rem;"><strong>Repository:</strong> RoLi lab</p>
        </div>
        <a href="https://github.com/cvikash/_HMMs.jl" target="_blank" class="btn btn--primary">
          View on GitHub →
        </a>
      </div>
    </div>

    <!-- Introduction -->
    <div class="content-card blog-style">
      <p style="font-size: 1.125rem; line-height: 1.9; color: var(--color-text-secondary); margin-bottom: 2rem; font-weight: 400;">
        Freely behaving animals don't just move randomly—they transition through distinct behavioral states organized at multiple 
        temporal scales. A zebrafish might cycle between sleep and wake over hours, but within those periods, it's constantly 
        switching between exploration and exploitation, movement and rest, active swimming and quiescence. Each of these states 
        has characteristic behavioral signatures, but how do we identify them from the continuous stream of movement data?
      </p>

      <p style="font-size: 1.125rem; line-height: 1.9; color: var(--color-text-secondary); margin-bottom: 2rem;">
        This project tackles that challenge by developing and applying <strong>autoregressive hidden Markov models (ARHMMs)</strong> 
        to identify behavioral motifs in freely swimming larval zebrafish. Unlike classic HMMs, ARHMMs capture the fact that what 
        happens next in behavior often depends on what just happened—a crucial feature for understanding behavioral sequences. 
        We implemented this method in Julia and applied it to high-resolution behavioral tracking data to uncover the hidden states 
        that organize zebrafish behavior.
      </p>
    </div>

    <!-- The Challenge -->
    <div class="content-card blog-style">
      <h2 style="margin-bottom: 1.5rem;">The Challenge: From Continuous Signals to Discrete States</h2>
      
      <p>
        When you watch a zebrafish swim freely in an arena, you're seeing a complex, continuous stream of behavior. The fish moves 
        through space, its tail undulates, its eyes track or saccade, and its body posture changes constantly. But underlying this 
        continuous behavior are discrete behavioral states—periods of active exploration, quiescent rest, directed swimming, 
        and more. The challenge is identifying where one state ends and another begins.
      </p>

      <p>
        Traditional approaches often rely on simple thresholds (e.g., "if speed > X, then active"). But behavior is more nuanced 
        than that. A fish might be moving slowly but actively exploring, or moving quickly but in a stereotyped pattern. We needed 
        a method that could capture the <strong>multidimensional nature</strong> of behavior and identify states based on patterns 
        across multiple behavioral features simultaneously.
      </p>
    </div>

    <!-- The Method: ARHMM -->
    <div class="content-card blog-style">
      <h2 style="margin-bottom: 1.5rem;">Why Autoregressive HMMs? Capturing Behavioral Dependencies</h2>
      
      <p>
        Hidden Markov Models are powerful tools for identifying hidden states from observed sequences. In a classic HMM, the 
        probability of observing a particular behavior at time <em>t</em> depends only on the current hidden state. But behavior 
        doesn't work that way—what you do next often depends on what you just did. A fish that just made a saccade is more likely 
        to continue moving; a fish that just stopped is more likely to remain quiescent.
      </p>

      <p>
        That's where <strong>autoregressive HMMs (ARHMMs)</strong> come in. In an ARHMM, the probability of an observation depends 
        on both the current hidden state <em>and</em> the previous observation. This allows the model to capture sequential 
        dependencies—the fact that behaviors have momentum, that transitions between states are structured, and that the context 
        of what just happened matters for what comes next.
      </p>

      <div class="figure-item" style="margin: 2rem 0;">
        <div class="figure-image" style="display: flex; gap: 1rem; flex-wrap: wrap; justify-content: center;">
          <img src="/assets/images/project_arhmm/HMM_graphical_model.png" alt="HMM graphical model" loading="lazy" style="max-width: 48%; flex: 1 1 45%; min-width: 200px;">
          <img src="/assets/images/project_arhmm/ARHMM_graphical_model.png" alt="ARHMM graphical model" loading="lazy" style="max-width: 48%; flex: 1 1 45%; min-width: 200px;">
        </div>
        <div class="figure-caption">
          <strong>Graphical models:</strong> (Left) Classic HMM: emission depends only on the current hidden state. 
          (Right) ARHMM: emission depends on both the current hidden state and the previous observation, allowing the model to 
          capture sequential dependencies in behavioral sequences.
        </div>
      </div>

      <p>
        We implemented both HMM and ARHMM variants in Julia, with full parameter estimation (Baum–Welch algorithm), state decoding 
        (Viterbi algorithm), and tools for discretizing continuous behavioral features using Gaussian mixture models. The package 
        is available on GitHub and provides a complete pipeline from raw behavioral data to inferred state sequences.
      </p>
    </div>

    <!-- The Experiment -->
    <div class="content-card blog-style">
      <h2 style="margin-bottom: 1.5rem;">Recording Behavior at High Resolution</h2>
      
      <p>
        To apply this method, we recorded freely swimming larval zebrafish in a featureless arena (30 mm × 30 mm) at high 
        spatiotemporal resolution. We tracked multiple behavioral parameters simultaneously:
      </p>

      <ul style="margin: 1.5rem 0; padding-left: 2rem; line-height: 1.8;">
        <li><strong>Speed and dispersal:</strong> How much the animal moves within a time window, capturing overall activity level</li>
        <li><strong>Tail and heading:</strong> Body orientation and movement direction, revealing directed vs. undirected movement</li>
        <li><strong>Eye movement:</strong> Left and right eye angles, allowing us to detect saccades and conjugate eye movements</li>
      </ul>

      <p>
        From these raw signals, we derived three key observables for the ARHMM: <strong>dispersal</strong> (movement magnitude), 
        <strong>heading velocity</strong> (smoothed directional movement), and <strong>saccade rate</strong> (frequency of conjugate 
        saccades in the eye-angle traces). These three features capture different aspects of behavior—overall activity, directed 
        movement, and eye movement patterns—that together define distinct behavioral states.
      </p>

      <div class="figure-item" style="margin: 2rem 0;">
        <div class="figure-image">
          <img src="/assets/images/project_arhmm/zebrafish_behavior_combined.png" alt="Zebrafish behavior: trajectory, dispersal, and eye angles" loading="lazy">
        </div>
        <div class="figure-caption">
          <strong>Behavioral tracking:</strong> (A) Trajectory of a freely swimming zebrafish in a featureless arena (30 mm × 30 mm). 
          (B) Schematic showing fish body and eye-angle measurement. (C) Dispersal over time, capturing overall movement magnitude. 
          (D) Left and right eye angles, revealing saccades and conjugate eye movements. These high-resolution behavioral signals 
          form the basis for state identification using ARHMMs.
        </div>
      </div>
    </div>

    <!-- Discretization and State Inference -->
    <div class="content-card blog-style">
      <h2 style="margin-bottom: 1.5rem;">From Continuous to Discrete: Building the Model</h2>
      
      <p>
        The first step was converting our continuous behavioral signals into discrete symbols that the ARHMM could work with. We 
        used a <strong>Gaussian mixture model (GMM)</strong> to cluster the multidimensional behavioral space into discrete 
        categories. Each time point gets assigned to one of these categories based on its combination of dispersal, heading velocity, 
        and saccade rate.
      </p>

      <p>
        Then we fit a <strong>5-state ARHMM</strong> to this discrete sequence. The model learns:
      </p>

      <ul style="margin: 1.5rem 0; padding-left: 2rem; line-height: 1.8;">
        <li><strong>State transition probabilities:</strong> How likely is the fish to switch from one behavioral state to another?</li>
        <li><strong>Emission probabilities:</strong> Given a hidden state and the previous observation, what's the probability of 
        observing each behavioral symbol?</li>
        <li><strong>Initial state distribution:</strong> What states does the fish start in?</li>
      </ul>

      <p>
        Using the Viterbi algorithm, we then decode the most likely sequence of hidden states given the observed behavioral data. 
        This gives us a state assignment for every time point, revealing when the fish transitions between different behavioral motifs.
      </p>
    </div>

    <!-- Results -->
    <div class="content-card blog-style">
      <h2 style="margin-bottom: 1.5rem;">What We Found: Organized Behavioral Motifs</h2>
      
      <p>
        The ARHMM successfully identified extended bouts of distinct behavioral activity with smooth transitions between them. 
        Rather than random switching, the model revealed that zebrafish behavior is organized into coherent, state-like motifs 
        that persist over time and transition in structured ways.
      </p>

      <div class="figure-item" style="margin: 2rem 0;">
        <div class="figure-image">
          <img src="/assets/images/project_arhmm/ARHMM_sleep_substate.png" alt="ARHMM inferred states from zebrafish behavioral signals" loading="lazy">
        </div>
        <div class="figure-caption">
          <strong>ARHMM state inference:</strong> The model assigns each time point to one of five hidden states based on the 
          observed behavioral signals (dispersal, saccade rate, eye angles). The bottom panel shows the inferred state sequence 
          over time, revealing extended bouts of distinct activity and smooth transitions between states. This demonstrates that 
          zebrafish behavior is organized into interpretable, state-like motifs rather than random switching.
        </div>
      </div>

      <p>
        Each of the five inferred states captures a different behavioral pattern. Some states correspond to active exploration—high 
        dispersal, frequent saccades, directed movement. Others correspond to quiescent periods—low dispersal, minimal movement, 
        stable eye positions. The transitions between states aren't random; they follow patterns that reflect the organization of 
        behavior at multiple temporal scales.
      </p>

      <p>
        This approach provides a powerful framework for understanding how behavior is organized. By identifying the hidden states 
        that structure behavioral sequences, we can ask questions about how these states are regulated, how they change across 
        conditions, and how they relate to underlying neural activity. The ARHMM doesn't just describe behavior—it reveals the 
        structure that organizes it.
      </p>
    </div>

    <!-- Technical Details -->
    <div class="content-card blog-style">
      <h2 style="margin-bottom: 1.5rem;">Implementation and Tools</h2>
      
      <p>
        The complete implementation is available as a Julia package on GitHub. The package provides:
      </p>

      <ul style="margin: 1.5rem 0; padding-left: 2rem; line-height: 1.8;">
        <li><strong>HMM and ARHMM models:</strong> Full implementations with parameter estimation and state decoding</li>
        <li><strong>Baum–Welch algorithm:</strong> Expectation-maximization for learning model parameters from data</li>
        <li><strong>Viterbi algorithm:</strong> Finding the most likely state sequence</li>
        <li><strong>GMM discretization:</strong> Converting continuous behavioral features into discrete symbols</li>
        <li><strong>Model selection:</strong> Log-likelihood and AIC for comparing models</li>
      </ul>

      <p>
        The package is designed to be flexible and extensible, making it easy to apply ARHMMs to other behavioral datasets or 
        adapt the method for different types of sequential data. All code is documented and includes example notebooks showing 
        how to apply the method to zebrafish behavioral data.
      </p>

      <p style="margin-top: 2rem;">
        <a href="https://github.com/cvikash/_HMMs.jl" target="_blank" class="btn btn--primary">
          Explore the Code on GitHub →
        </a>
      </p>
    </div>

    <!-- What This Means -->
    <div class="content-card blog-style" style="background: linear-gradient(135deg, rgba(26, 86, 219, 0.03) 0%, rgba(14, 165, 233, 0.03) 100%);">
      <h2 style="margin-bottom: 1.5rem;">Why This Matters: Understanding Behavioral Organization</h2>
      
      <p>
        Behavior isn't just a continuous stream—it's organized into discrete, coherent states that persist over time and transition 
        in structured ways. By identifying these states using ARHMMs, we can understand how behavior is organized at multiple 
        temporal scales, from rapid transitions between movement and rest to longer-term cycles of exploration and exploitation.
      </p>

      <p>
        This approach has broad applications. It can be used to identify behavioral states in any animal, to compare behavior across 
        conditions or genotypes, and to link behavioral states to underlying neural activity. The method provides a quantitative, 
        data-driven way to parse behavior into interpretable motifs, opening up new questions about how behavior is generated, 
        regulated, and organized.
      </p>

      <p>
        For zebrafish specifically, understanding these behavioral motifs helps us understand how sleep and wake states are organized, 
        how animals explore their environment, and how behavioral states relate to neural activity patterns. By combining this 
        behavioral analysis with whole-brain imaging, we can begin to map the neural circuits that generate and regulate these 
        behavioral states.
      </p>
    </div>
  </div>
</section>

