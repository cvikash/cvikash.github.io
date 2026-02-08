---
title: "Alterations of specific cortical GABAergic circuits underlie abnormal network activity in a mouse model of Down syndrome"
layout: page
permalink: /projects/down-syndrome-gaba-circuits/
classes: wide
---

<section class="page-hero">
  <div class="container">
    <h1 class="page-hero__title">Alterations of specific cortical GABAergic circuits underlie abnormal network activity in a mouse model of Down syndrome</h1>
    <p class="page-hero__subtitle">Understanding cognitive deficits through cortical network dynamics and Up/Down state detection</p>
  </div>
</section>

<section class="page-content">
  <div class="container">
    <!-- Publication Info -->
    <div class="content-card" style="background: linear-gradient(135deg, rgba(26, 86, 219, 0.05) 0%, rgba(14, 165, 233, 0.05) 100%); border-left: 4px solid var(--color-primary);">
      <div style="display: flex; justify-content: space-between; align-items: start; flex-wrap: wrap; gap: 1rem;">
        <div>
          <p style="margin: 0; color: var(--color-text-muted); font-size: 0.9rem;"><strong>Published:</strong> August 12, 2020 in eLife</p>
          <p style="margin: 0.5rem 0 0 0; color: var(--color-text-muted); font-size: 0.9rem;"><strong>DOI:</strong> 10.7554/eLife.58731</p>
        </div>
        <a href="https://elifesciences.org/articles/58731" target="_blank" class="btn btn--primary">
          Read Full Paper →
        </a>
      </div>
    </div>

    <!-- Introduction -->
    <div class="content-card blog-style">
      <p style="font-size: 1.125rem; line-height: 1.9; color: var(--color-text-secondary); margin-bottom: 2rem; font-weight: 400;">
        Down syndrome affects millions of people worldwide, and one of its most significant challenges is intellectual disability. 
        For years, researchers have noticed something interesting: drugs that reduce inhibitory activity in the brain seem to 
        improve cognition in mouse models of Down syndrome. This suggested that maybe there's too much inhibition happening—but 
        which circuits? And how exactly does this lead to cognitive problems?
      </p>

      <p style="font-size: 1.125rem; line-height: 1.9; color: var(--color-text-secondary); margin-bottom: 2rem;">
        That's what this study set out to answer. We focused on the prefrontal cortex—a brain region crucial for executive 
        functions like working memory and cognitive flexibility. Using a mouse model of Down syndrome (Ts65Dn mice), we 
        investigated how specific inhibitory circuits are altered and how these changes affect network activity. My contribution 
        focused on developing computational methods to detect and analyze Up and Down states in cortical local field potentials 
        (LFP), which are key signatures of cortical network dynamics.
      </p>
    </div>

    <!-- The Problem -->
    <div class="content-card blog-style">
      <h2 style="margin-bottom: 1.5rem;">The Problem: Too Much Inhibition?</h2>
      
      <p>
        The prefrontal cortex relies on a delicate balance between excitation and inhibition. Too much of either, and things 
        go wrong. Previous work had shown that blocking GABA receptors (the main inhibitory neurotransmitter) could improve 
        cognitive function in Down syndrome mouse models. But the brain has many different types of inhibitory neurons, each 
        with different roles. Which ones are causing the problem?
      </p>

      <p>
        We looked at two major types of inhibitory circuits: <strong>Martinotti cells</strong> (which target the dendrites 
        of pyramidal neurons) and <strong>parvalbumin-positive basket cells</strong> (which target the cell bodies). These 
        circuits do very different things. Martinotti cells help integrate information from different sources, while PV cells 
        help synchronize activity across brain regions. Understanding how each is affected in Down syndrome would tell us a 
        lot about what's going wrong.
      </p>
    </div>

    <!-- Up and Down States -->
    <div class="content-card blog-style">
      <h2 style="margin-bottom: 1.5rem;">Detecting Up and Down States: The Method</h2>
      
      <p>
        One of the key ways we studied network activity was by detecting <strong>Up and Down states</strong> in cortical 
        local field potentials (LFP). These are fundamental patterns of cortical activity that occur during quiet wakefulness 
        and sleep. Understanding them is crucial for understanding how the cortex processes information.
      </p>

      <p>
        <strong>Up states</strong> are periods of high neuronal activity—lots of neurons firing, synchronized activity, 
        and strong network engagement. <strong>Down states</strong> are the opposite—periods of relative quiescence with 
        low firing rates. The cortex naturally alternates between these states, and this alternation is thought to be 
        important for information processing and memory consolidation.
      </p>

      <h3 style="margin-top: 2rem; margin-bottom: 1rem;">How We Detect Them</h3>
      
      <p>
        Detecting Up and Down states from LFP recordings isn't trivial. The signals are noisy, and the transitions can be 
        subtle. We developed computational methods that analyze the LFP signal to identify these states based on several 
        characteristics:
      </p>

      <ul style="margin-top: 1rem; line-height: 1.9; color: var(--color-text-secondary);">
        <li><strong>Power spectral density:</strong> Up states show increased power in specific frequency bands, particularly 
        in the gamma range (30-80 Hz), which reflects synchronized network activity</li>
        <li><strong>Amplitude fluctuations:</strong> The LFP amplitude is higher during Up states and lower during Down states</li>
        <li><strong>Temporal dynamics:</strong> Up states typically last hundreds of milliseconds to seconds, with clear 
        transitions between states</li>
        <li><strong>Phase locking:</strong> During Up states, neurons become more synchronized, which we can detect through 
        phase analysis of the LFP</li>
      </ul>

      <p style="margin-top: 1.5rem;">
        Our algorithm essentially looks for periods where the LFP crosses certain thresholds and maintains certain characteristics 
        for a minimum duration. We use a combination of filtering, threshold detection, and state validation to reliably identify 
        these states. This gives us a way to quantify network dynamics and see how they're altered in Down syndrome.
      </p>
    </div>

    <!-- Key Findings -->
    <div class="content-card blog-style">
      <h2 style="margin-bottom: 1.5rem;">What We Found</h2>
      
      <p>
        The results revealed specific, targeted alterations in inhibitory circuits. The <strong>Martinotti cell circuit</strong> 
        was strongly enhanced—there was more inhibition coming from these cells onto pyramidal neuron dendrites. Interestingly, 
        the Martinotti cells themselves weren't more excitable; the enhancement was at the synaptic level.
      </p>

      <p>
        The <strong>PV basket cell circuit</strong> told a different story. The amount of perisomatic inhibition was actually 
        normal, but the PV cells themselves had changed. They lost their classic "fast-spiking" phenotype and became more 
        excitable. This is significant because fast-spiking PV cells are crucial for generating gamma oscillations, which are 
        important for cognitive functions.
      </p>

      <h3 style="margin-top: 2rem; margin-bottom: 1rem;">Network-Level Consequences</h3>
      
      <p>
        When we looked at the network activity using our Up/Down state detection methods, we found that pyramidal neurons 
        fired less overall in Down syndrome mice. But more importantly, they showed increased phase locking to network 
        oscillations—meaning they were more tightly synchronized to the network rhythm, but potentially less flexible in 
        their responses.
      </p>

      <p>
        This increased phase locking, combined with reduced overall firing, suggests that the network is in a more rigid, 
        less flexible state. Think of it like an orchestra where everyone is playing in perfect sync, but they can't 
        improvise or adapt. This rigidity likely contributes to the cognitive inflexibility seen in Down syndrome.
      </p>
    </div>

    <!-- Significance -->
    <div class="content-card blog-style" style="background: linear-gradient(135deg, rgba(26, 86, 219, 0.03) 0%, rgba(14, 165, 233, 0.03) 100%);">
      <h2 style="margin-bottom: 1.5rem;">Why This Matters</h2>
      
      <p>
        This work provides a much more precise picture of what's going wrong in Down syndrome. Instead of just "too much 
        inhibition," we now know which specific circuits are affected and how. This opens up possibilities for targeted 
        interventions—maybe we can specifically modulate Martinotti cell activity or restore PV cell fast-spiking properties, 
        rather than broadly blocking all inhibition.
      </p>

      <p>
        The Up/Down state detection methods we developed also provide a powerful tool for studying cortical network dynamics 
        in other conditions. These states are fundamental to cortical function, and being able to reliably detect and analyze 
        them opens up new ways to understand how neural circuits work—and how they go wrong in disease.
      </p>
    </div>

    <!-- Technical Contribution -->
    <div class="content-card blog-style" style="border-top: 2px solid var(--color-border); margin-top: 3rem; padding-top: 2rem;">
      <h3 style="color: var(--color-primary); margin-bottom: 1rem;">My Contribution</h3>
      <p>
        I contributed to this work by developing the computational methods for detecting and analyzing Up and Down states 
        in cortical LFP recordings. This involved signal processing, state detection algorithms, and analysis of network 
        dynamics. The methods we developed allow for reliable identification of these fundamental cortical states, which 
        are crucial for understanding how network activity is altered in Down syndrome and other neurodevelopmental conditions.
      </p>
    </div>

    <!-- Authors & Citation -->
    <div class="content-card" style="background: var(--color-bg-tertiary); margin-top: 2rem;">
      <div style="margin-bottom: 1.5rem;">
        <h3 style="font-size: 1.1rem; margin-bottom: 1rem; color: var(--color-text-primary);">Authors</h3>
        <p style="margin: 0; line-height: 1.8; color: var(--color-text-secondary);">
          Javier Zorrilla de San Martin, Cristina Donato, Jérémy Peixoto, Andrea Aguirre, 
          <strong>Vikash Choudhary</strong>, Angela Michela De Stasi, Joana Lourenço, 
          Marie-Claude Potier, Alberto Bacci
        </p>
        <p style="margin: 0.5rem 0 0 0; color: var(--color-text-muted); font-size: 0.9rem;">
          Institut du Cerveau (ICM), CNRS UMR 7225 – Inserm U1127, Sorbonne Université, Paris, France
        </p>
      </div>
      
      <div style="border-top: 1px solid var(--color-border); padding-top: 1.5rem;">
        <h3 style="font-size: 1.1rem; margin-bottom: 1rem; color: var(--color-text-primary);">Citation</h3>
        <div style="background: var(--color-bg-primary); padding: 1.5rem; border-radius: var(--radius-md); border: 1px solid var(--color-border);">
          <p style="margin: 0; font-style: italic; line-height: 1.8; color: var(--color-text-secondary); font-size: 0.95rem;">
            Zorrilla de San Martin, J., Donato, C., Peixoto, J., Aguirre, A., Choudhary, V., De Stasi, A. M., 
            Lourenço, J., Potier, M. C., & Bacci, A. (2020). Alterations of specific cortical GABAergic circuits 
            underlie abnormal network activity in a mouse model of Down syndrome. 
            <em>eLife</em>, 9, e58731. 
            <a href="https://doi.org/10.7554/eLife.58731" target="_blank" style="color: var(--color-primary);">https://doi.org/10.7554/eLife.58731</a>
          </p>
        </div>
        <div style="margin-top: 1.5rem; display: flex; gap: 1rem; flex-wrap: wrap;">
          <a href="https://elifesciences.org/articles/58731" target="_blank" class="btn btn--primary">
            Read Full Paper →
          </a>
          <a href="https://scholar.google.com/citations?user=G9J3MVQAAAAJ&hl=en" target="_blank" class="btn btn--secondary">
            View on Google Scholar
          </a>
        </div>
      </div>
    </div>
  </div>
</section>

