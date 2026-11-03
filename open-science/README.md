# ESTER Open Science Standards  
_Draft v0.1_

**Applies to:** All ESTER team members and all ESTER repositories (code, data, documentation).  
**Scope:** These standards define how we implement open, reproducible, and ethically responsible research across the ESTER project.

---

## 1. Core Principles

Based on the responsibility meeting outcomes and workflow rules, ESTER commits to the following core principles.

### 1.1 Transparency

- All **code**, **data transformations**, **modelling decisions**, and **assumptions** must be:
  - documented,
  - traceable, and
  - linked to version control (Git history, pull requests, issues).
- Every major component (e.g. data pipelines, likelihood functions, model modules) must:
  - be developed on a feature branch,
  - go through a **Pull Request**,
  - pass **automated checks** (linting, tests, reproducibility checks), and
  - receive at least one **review** prior to merge.

### 1.2 Reproducibility

- All analysis scripts must run in a **clean environment**, using:
  - reproducible environment management (e.g. `renv`, `conda`, or Docker),
  - versioned model components (tags, releases),
  - standardised preprocessing scripts.
- Every dataset must include:
  - **metadata** (provenance, scope, methods),
  - a **data dictionary** (field descriptions, units, codes).
- Every model must be:
  - **versioned** (tags/releases with change logs),
  - **documented** (parameters, structure, assumptions),
  - **testable** (unit tests and validation checks where feasible).

### 1.3 FAIR Data Principles

Implementation & monitoring of FAIR standards is led by **PostDoc1 (FAIR lead, currently Sophie)**, with PI oversight.

- **Findability**
  - Use standardised schemas for archaeological datasets (including controlled vocabularies / “thesauri”).
  - Document proxies, parameters, and assumptions in the model specification and/or `docs/` directory.
- **Accessibility**
  - Release datasets publicly once approved by the PI.
  - Use stable identifiers (e.g. DOIs, persistent IDs) and open, non-proprietary formats (e.g. CSV, JSON).
- **Interoperability**
  - Use consistent field names, ontologies, and coordinate systems (e.g. GIS standards).
  - Harmonise proxy definitions across regions wherever possible.
- **Reusability**
  - Provide clear licensing statements (e.g. CC-BY, CC-BY-SA, or as agreed).
  - Document limitations, assumptions, and known biases (e.g. in proxy definitions, sampling strategies, taphonomic effects).

### 1.4 Ethical Data Governance

From PI responsibilities and data governance notes:

- Integration of external repositories (e.g. **XRONOS**) is **controlled** and documented.
- The PI approves:
  - data inclusion/exclusion decisions (e.g. which external datasets are incorporated),
  - final proxy definitions used in published models,
  - public release of generated datasets and layers.
- All outputs undergo a **sensitivity review** prior to publication, especially for:
  - human remains,
  - culturally sensitive sites,
  - restricted or vulnerable heritage information.

---

## 2. Documentation Standards

### 2.1 Internal Documentation

- Responsibilities, decision rules, and process documentation are maintained in  
  [ester-project-governance/team/roles.md](https://github.com/project-ester-hub/ester-project-governance/tree/main/team/roles).
- All repositories must maintain an up-to-date `README.md` that describes:
  - the **purpose** of the repository,
  - the **repository structure** (folders, key modules),
  - **setup instructions** (environment, dependencies, how to run),
  - **contribution practices** (branching, PRs, issue templates).

### 2.2 Model Documentation

Each model (or model family) must provide:

- A clear description of:
  - **parameters** (meaning, priors, units),
  - **observation models** (likelihoods, link functions),
  - **links to data sources** (internal/external datasets, version/DOI),
  - **assumptions** (e.g. taphonomic loss model, proxy behaviour, independence assumptions).
- For each **release** (version tag):
  - a model **version tag** (e.g. `v1.2.0`),
  - a short **summary of methodological changes**,
  - **performance / diagnostics notes** (e.g. convergence, effective sample sizes, posterior predictive checks).

---

## 3. Code Quality and Review Process

### 3.1 Code Practices

- Work on **feature branches** (e.g. `feature/<topic-name>`).
- Follow consistent style guidelines for R and Python (linting, formatter where applicable).
- Include **unit tests** and/or regression tests where feasible, especially for:
  - core model components,
  - data transformation functions,
  - utility libraries.
- Ensure scripts:
  - handle missing values and edge cases,
  - are runnable end-to-end (or clearly indicate which steps are manual),
  - can be executed in a documented clean environment.

### 3.2 Review Workflow

- Every Pull Request requires **at least one review**, regardless of author.
- Conceptual model changes (e.g. new model structure, new proxy interpretation) require **PI approval**.
- Archaeological data workflows:
  - are led by **PostDoc1**,
  - are reviewed by the PI as needed, especially prior to public release or publication.

### 3.3 Automated Checks

- **Linting / style checks** (R, Python, YAML, etc.).
- **Reproducibility checks**, e.g.:
  - running the main pipeline in a clean container/virtual environment,
  - verifying outputs against expected results.
- **Validation checks** for:
  - data formats and schemas,
  - proxy definitions (types, ranges, units),
  - model assumptions where they can be asserted programmatically.

---

## 4. Data Management and Proxy Standards

### 4.1 Archaeological Data  
_Lead: PostDoc1_

- Maintain standardised ingestion workflows for:
  - radiocarbon datasets,
  - aoristic sums / typologically dated data,
  - dendrochronological datasets,
  - settlement datasets and related spatial layers.
- Ensure quality assurance through:
  - internal consistency checks (e.g. date ranges, IDs, coordinates),
  - bias assessments (e.g. sampling, taphonomy, research history),
  - region-specific harmonisation (terminology, phase schemes, coordinate reference systems).
- Each **proxy definition** must include:
  - the rationale for using this proxy,
  - known assumptions and biases,
  - expected behaviour in the model (e.g. detection rate, informativeness, resolution).

### 4.2 Environmental Data  
_Lead: PostDoc2 (future)_

- Maintain standardised workflows for:
  - pollen and vegetation proxies,
  - land-use and landscape openness proxies,
  - environmental reconstructions (e.g. climate, hydrology).
- Environmental data must follow the **same FAIR and documentation principles** as archaeological data:
  - metadata,
  - data dictionary,
  - versioning,
  - licensing,
  - documented limitations.

---

## 5. Publication and Open Access Standards

### 5.1 Paper Writing

- **Preprints are encouraged** (e.g. OSF, arXiv, EarthArXiv), where journal policy allows.
- Methods, modelling steps, and data transformations must be:
  - openly documented,
  - linked to public repositories (code + data),
  - sufficiently detailed to allow reproduction by third parties.

### 5.2 Authorship Discipline

- The **PI** leads the conceptual framing and overall narrative.
- **PostDocs** lead domain-specific sections (e.g. archaeological, environmental, modelling).
- All contributors document their contributions, e.g. via:
  - GitHub issues / commits,
  - Overleaf comments,
  - a structured author contributions section (CRediT taxonomy where appropriate).

### 5.3 Data Release

- After PI approval, the following should be made **publicly available** (for each major publication or release):
  - cleaned datasets,
  - proxy layers (e.g. raster/hex grids),
  - model outputs in an interpretable form (e.g. aggregated summaries, posterior means/intervals),
  - reproducibility packages (e.g. scripts + data subset sufficient to re-run key results).
- Sensitive or restricted data must be handled according to the ethical governance standards (Section 1.4).

### 5.4 Code Release

- All code required to reproduce a publication’s results must be deposited in a **permanent public repository**, e.g.:
  - GitHub release linked to
  - Zenodo (or similar) DOI.
- The repository must include:
  - instructions to reproduce the key results,
  - environment specifications (`renv.lock`, `environment.yml`, `Dockerfile`, etc.),
  - clear license information.

---

## 6. Communication & Governance in Support of Open Science

### 6.1 Decision-Making Transparency

- **Scientific decisions**:
  - PI leads;
  - PostDocs propose options and alternatives.
- **Methodological choices** (e.g. choice of likelihoods, priors, model structure):
  - PostDocs lead implementation;
  - PI approves conceptual changes.
- Changes to the **project roadmap** must be reflected in GitHub Projects and/or the central roadmap repository.

### 6.2 Meeting Records

- **Sprint items** are structured in GitHub (issues, milestones, or project notes).
- The **roadmap** is updated at least monthly, including:
  - major decisions,
  - upcoming milestones,
  - shifts in priorities.
- **Quarterly strategy updates** are documented and archived.

### 6.3 Open Sharing of Knowledge

- **Journal clubs** (biweekly) focus on:
  - methods,
  - case studies,
  - conceptual advances relevant to ESTER.
- Internal modelling documentation is maintained as part of the `docs/` directory (or equivalent central hub).
- Public tutorials, workshops, and documentation (e.g. blog posts, example notebooks) are encouraged, and should:
  - reference ESTER repositories where appropriate,
  - follow the same open-access and reproducibility standards.

---

## 7. Release Workflow for Open Science Outputs

### 7.1 Monthly

- Run the **model update** (where relevant and feasible).
- Execute a **pipeline reproducibility test** in a clean environment.
- Update the **project roadmap** (GitHub Projects or equivalent).
- Release **non-sensitive outputs** publicly, subject to PI approval, e.g.:
  - updated proxy layers,
  - updated aggregated estimates.

### 7.2 Per Sprint

- Merge completed tasks via Pull Requests following the review workflow.
- Update associated documentation:
  - `README.md`,
  - model documentation,
  - `CHANGELOG.md` where used.

### 7.3 Per Publication

- Release:
  - the **code** required to reproduce the results,
  - the **data** (or subset) used for the analyses,
  - an **archived version** with DOI (e.g. Zenodo, OSF),
  - a **reproducibility package** (scripts + instructions + minimal data).
- Document the link between:
  - the publication,
  - the code/data repository,
  - the version/tag used for the analysis.

---

## ✔ Summary Table: Open Science Responsibilities

| Area                               | Lead      | Approver | Notes                                         |
|------------------------------------|-----------|----------|-----------------------------------------------|
| FAIR & reproducibility standards   | PostDoc1  | PI       | Implementation & monitoring                   |
| Conceptual modelling transparency  | PI        | —        | Defines assumptions & overall framework       |
| Documentation standards            | Shared    | PI       | PR-based workflow, `docs/` and `README`       |
| Data ingestion & cleaning          | PostDoc1  | PI       | Includes metadata and data dictionary         |
| Proxy definitions                  | PostDoc1  | PI       | Must be documented, versioned, and testable   |
| Model versioning                   | Shared    | PI       | Every release must be tagged and documented   |
| Public dataset release             | PostDoc1  | PI       | PI approval required for all releases         |
| Public code release                | Author    | PI       | Must be reproducible and archived (DOI)       |
| Publication packages (Zenodo etc.) | Author    | PI       | Includes code, data, and model documentation  |

---

_This is a living document. Updates should be proposed via Pull Request, discussed in the team where necessary, and approved by the PI._
