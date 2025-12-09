# Team Roles

This document aims at defining team roles, responsibilities, and communication flows within the ESTER project, aligned with the scientific objectives, the agile delivery structure (PIs & Sprints), and the interdisciplinary workflow (archaeology – environmental science – modelling – data engineering). It documents the current agreement and has to be revised quaterly. We have specifically to ensure a balance of tasks and the limits of employment.

The tasks defined here focus on project year 1 **WP1 (data collection) and early WP2 (model specification)** and have been developed for milestone [PI-1](https://github.com/project-ester-hub/ester-roadmap/milestone/3) and [Epic #90](https://github.com/project-ester-hub/ester-roadmap/issues/90).


## Roles (PI, PostDoc 1)
As of publication of this documentation, two team members are working for the project, the PI Martin Hinz, and PostDoc 1 Sophie Schmidt. Their tasks and responsibilities will be defined in the following paragraphs.

## Overview

- PI responsibilities are generally:
  - conceptual modelling,
  - method design,
  - data strategy,
  - agile project setup,
  - HPC preparation,
  - cross-disciplinary (team) steering

- PostDoc1 responsibilities are generally:
  - archaeological population proxies,
  - data collection,
  - early analysis,
  - participation in modelling,
  - supporting case study preparation
    
## Detailed tasks

### PI Martin Hinz

#### Leadership & Strategy

- Define scientific direction for WP1–WP3 and overall modelling framework, including modelling priorities.
- Maintain coherence with the ESTER project proposal and theoretical framing.
- Ensure consistency with ERC goals (regionalised population estimates, uncertainty quantification, methodological innovation).
- Approve major modelling assumptions and architecture decisions.

#### Project & Team Coordination
- Maintain roadmap & iteration structure.
- Sprint planning as *Project Owner*, retrospectives, PI-level decision-making.
- Run sprints, reviews, retrospectives (for year 1).
- Maintain relationship with external partners (XRONOS, COREX, ...).
- Lead communication with institutional and funding bodies.
 
#### Modelling Architecture & Methodology
- Lead design of the hierarchical state-space process model in Year 1
- Approve observation model specifications for archaeological proxies, radiocarbon, dendrochronology, pollen.
- Lead the transition of the Swiss pilot model into the Eurasia-wide framework.
- Maintain the modelling repository structure.

#### Data Governance
- Oversee controlled integration of XRONOS (synergy explicitly stated in WP1)
- Approve proxy definitions and data cleaning strategies.

#### Technical Contribution
- Design high-level modelling workflow.
- Develop conceptual and mathematical components (state-space structure, assumptions).
- Support debugging and model validation.

#### Documentation & Dissemination
- Oversee publications, presentations, outreach outputs.
- Maintain the high-level roadmap in GitHub Projects.
- Lead conceptual parts of publications, ensure coherence with proposal narrative.
- Represent ESTER at international conferences & public visibility events.
  
#### Quality Assurance & Ethics
- Set quality standards for documentation.
- Approve releases of code and documentation.

### Post Doc Sophie Schmidt

#### Data Integration & Preprocessing
- Implement data ingestion workflows (archaeological: radiocarbon, aoristic sums, dendro chronology).
- Collect, curate, and standardise archaeological datasets ("thesauri": settlements, findspots, cultural phases).
- Coordinate with PI regarding required proxy coverage for each region.
- Convert datasets into standard CSV/time-series formats ready for modelling (aligning with WP1 deliverables).
- Develop standardised preprocessing scripts in R/Python.

#### Development & Validation of Archaeological Proxies
- Identify and operationalise proxies (site counts, settlement size, artefact variance, occupation sequences).
- Run systematic testing + quality control pipelines.
- Explore possibilities for novel archaeological proxies in cooperation with PI.
- Document assumptions, strengths, and limitations of each proxy for PI review (eg. Bias Matrix...).

#### Modelling Implementation
- Prepare model-ready data structures for NIMBLE/R etc.
- Collaborate with PI to refine observation models for archaeological data.
- Perform initial model diagnostics & interpretation of results within an archaeological context.
- Coordinate with Martin for methodological decisions.
  
*(Optional:)*
- Translate conceptual model drafts into runnable code.
- Take part in the initial hierarchical Bayesian models (NIMBLE/R, Python optional).
- Implement proxy likelihoods, taphonomic corrections, detection-rate components.

#### Spatial Analysis (GIS)
- Analyse settlement patterning, mobility, land-use, and contextualise results regionally.
- Provide spatial datasets for model regionalisation (grid/hex systems).
  
#### Computational Infrastructure
- Create reproducible pipelines (quarto, scripts, automated runs).
- Assist with continuous monthly updates and validation.

#### Documentation/FAIR and Open Science
- Set quality standards for reproducibility and FAIR compliance.
- Set quality standards for internal technical documentation (model specs, parameter descriptions).

*(Optional)*
- Write unit tests and usage examples.

#### Communication
- Takes the role of *Scrum Master*
  - Present progress during sprint reviews.
  - Summarise obstacles early (weekly standups).

#### Research & Publication
- Lead archaeological components of papers.
- Lead Author for first result paper.
- Prepare conference presentations; coordinate data visualisations with PI.
- Work toward first joint methodological paper by end of Year 1.
- Co-author methodological papers and case studies.
- Support preparation of ESTER datasets for public release.
- Represent ESTER at international conferences & public visibility events.

## Responsibility matrix

There are some tasks each team member may complete without a need for validation by another team member. Other tasks should be discussed and/or cross-checked. 

| task/area | PI MH | PostDoc SCS |
| ------ | ---- | ---- |
| archaeological proxy definition | discusses and approves decision | develops and approves decisions |
| arch. proxy operationalisation | discusses | develops and approves decision |
| data inclusion/exclusion decisions |  approves decision  | develops and approves decision |
| major GitHub merges | always need a second opinion | always need a second opinion |
| public release of gathered data |  | develops and decides |
| public release of data developed by the project | discusses and approves | discusses and develops |
| publications | first drafts of introductions | first drafts of archaeological sections |
| GIS workflows | may discuss if needed | develops and decides |
| arch. datasets | may discuss if needed | develops and decides |
| conceptual model changes | discusses and decides | develops and discusses|

## Communication & Workflows

Regular meetings following the agile methodology aim at identifying challenges early on and developing strategies to deal with them. Written exchange may take place via different channels. Especially model development should be reviewed properly and quality assuring procedures followed.

### Meeting Cadence
- Daily: 10 minutes standup (current todos done, in progress, blockers)
- Weekly: 30-minute check-in (priorities).
- Biweekly:
  - scrum meetings(Sprint planning, Sprint Review, Sprint Retrospective)
  - 60–90 min modelling deep dive.
  - 60-90 min journal club
- Monthly: Release + model update run + roadmap update. (Release Party)
- Quarterly: Research strategy check-in (first time after advisory board meeting).

### Preferred Channels
- GitHub Issues → technical tasks, bug reports, modelling notes
- GitHub Projects → PI-level planning, sprint board
- Nextcloud/Drive → documents, drafts
- Element/Matrix → everyday clarifications

### Review Workflow
- Every major component (data pipeline, likelihood, model module) requires:
	- Pull request
	- Automatic checks (linting, tests)
	- PI review & merge

### Quality Procedures
- Reproducibility: scripts must run via a clean environment.
- Every dataset: metadata + data dictionary.
- Every model: versioned, documented, testable.
