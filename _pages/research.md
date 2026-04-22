<img width="1447" height="1357" alt="image" src="https://github.com/user-attachments/assets/d9bf186c-1fe3-47c8-8d82-fa89c883b79c" />---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
header:
  og_image: "research/ecdf.png"
---

<div style="text-align: justify; font-size: 1.05em; line-height: 1.6; margin-bottom: 40px;">
My research operates at the intersection of advanced neuroimaging, computational network analysis, and digital health. I focus on unraveling the complex mechanisms of neurodegenerative diseases, particularly Alzheimer's disease, by quantifying brain clearance systems and network resilience. Ultimately, my goal is to translate these hospital-based neurobiological findings into scalable, real-world digital biomarkers using wearable technology and machine learning.
</div>

## 1. Multi-modal Neuroimaging & Glymphatic System
I investigate structural and functional brain alterations in aging and neurodegenerative disorders by integrating diverse neuroimaging modalities. My work focuses on mapping the trajectory of cognitive decline through the lens of the glymphatic system and proteinopathies. 

* **Macro to Microscale Morphometry:** Analyzing structural changes through cortical thickness and volume measurements alongside microstructural fluid dynamics using DTI-ALPS and Intravoxel Incoherent Motion (IVIM) MRI.
* **Molecular Imaging Integration:** Establishing automated preprocessing and quantification pipelines for PET imaging. This includes evaluating amyloid burden via the Centiloid scale and mapping tau pathology utilizing SUVR and Braak staging to uncover the mediating role of the glymphatic system in protein accumulation.

## 2. Brain Connectomics & Network Resilience
To understand how the brain networks deteriorate or compensate during disease progression, I employ advanced graph theory and machine learning on brain connectomics. This approach allows for the mathematical modeling of brain resilience and plasticity.

* **Network Alterations in Disease Cohorts:** Conducting comparative analyses of structural and functional connectivity (SC/FC) networks across various clinical populations.
* **Quantifying Cognitive Reserve:** Investigating SC-FC coupling and utilizing network communicability metrics to quantitatively define and measure cognitive reserve.
* **Advanced Predictive Modeling:** Developing diagnostic classification models utilizing Graph Convolutional Networks (GCN) to capture the topological complexities of the brain network for accurate clinical predictions.

## 3. Digital Health & Wearable-based Clinical Monitoring
I expand my research beyond conventional neuroimaging by developing digital healthcare platforms. This involves extracting physiological biomarkers from wearable sensors to create real-time, preventative clinical solutions.

* **Real-time Psychiatric Monitoring:** Designing predictive models to identify and prevent dangerous behaviors in psychiatric wards by synchronizing real-time smartwatch physiological data with CCTV visual tracking.
* **Digital Phenotyping:** Evaluating physiological and behavioral abnormalities through continuous smartwatch data analysis.
* **Wearable-Glymphatic Synchronization:** Bridging digital health and neurobiology by mapping smartwatch-derived sleep parameters to MRI-based glymphatic system efficiency, establishing accessible digital biomarkers for brain clearance monitoring.

My academic research falls into two main areas: understanding the influence of
geography on actor behavior before, during, and after civil conflict, and
developing new tools to improve the study of institutions (both formal and
informal) in peace and conflict. One strand of research in this first area
explores how the territories that ethnic groups inhabit shape rebel group
formation and condition their relationship with the state. My interest in
geography also informs projects on active conflicts including the targeting of
UN peacekeepers by insurgent groups, civilian victimization after rebel
territorial conquest, and communal violence in fragile settings.

My other main research agenda uses advanced methods to develop new measures of
institutions. One project uses Bayesian item response theory to measure the
strength of peace agreements as a latent variable and free researchers from
post-treatment bias caused by using the duration of agreements as a proxy for
their strength. In others, I apply unsupervised learning techniques to over a
billion observations of product-level international trade data to measure
economic interdependence and illicit economic exchange.

In a new avenue of research, I leverage social media data to explore
participation in extremist movements across multiple contexts, gaining insight
into the early stages of radicalization.

<nbsp>

{% include base_path %}

{% assign ordered_pages = site.research | sort:"order_number" %}

{% for post in ordered_pages %}
  {% include archive-single.html type="grid" %}
{% endfor %}
