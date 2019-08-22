# Team Standards

This document is meant to be the scaffold for setting team standards for a data science / machine learning team. Many of these are basic software engineering standards / best practices that help facilitate team collaboration in an organized manner. I use this document when setting up new projects / development teams. The sections of this document are meant to be heavily modified to fit the preferences of the user / team.

<!-- TOC -->
* [Coding Standards](#coding_standards)
  * [Prioritization](#prioritization)
  * [Python Style and Formatting](#style)
  * [Tools](#tools)
* [Github](#github)
  * [Setting Up a Project](#setup)
  * [Peer Reviews](#pr)
  * [Branching](#branching)
* [Deployment](#deployment)
<!-- TOC -->

## Coding Standards <a name="coding_standards"></a>

### Prioritization <a name="prioritization"></a>

The team adopts the [Agile Scrum](https://www.cprime.com/resources/what-is-agile-what-is-scrum/) style of work assignment using the [SAFe framework](https://www.scaledagile.com/enterprise-solutions/what-is-safe/). Developers only work on assigned tasks unless otherwise decided by scrum master / tech lead.

* Fewer meetings/ceremonies when possible
* Stand Up Every Morning (20 min max)
* All stories and bugs have:
  * Acceptance criteria
  * An owner
  * An epic
  * A sprint
  * A description
  * A title
* PIs are 3 months
* Sprints are 2 weeks
* Every sprint ends with a Demo and Retro meeting (1 hour total)
* The last sprint in every PI is dedicated just to tech debt

### Python Style and Formatting <a name="style"></a>

* PEP8 Conventions
  * Indentation: 4 spaces
  * Max line length: 99 characters
  * Blank lines: Top level class and function definitions are preceded by 2 blank lines. Method definitions inside a class are preceded by one blank line.
  * Source file encoding: UTF-8
  * Imports are all at the top of the file
  * Strings are double quoted.
  * All functions, classes, and modules require docstrings
* Non-PEP8 Conventions
  * Code derived from a paper should reference the paper
  * Code derived from a paper should follow the naming conventions of the paper
  * Papers are referenced using `title`, `publication year`, and `author` in documentation
  * Models should be defined as classes and used as objects
  * Local development done in `Conda Virtual Environment`

### Tools <a name="tools"></a>

  * Agile: [JIRA](https://www.atlassian.com/software/jira) or [Trello](https://trello.com/en-US)
  * Code Versioning: [Github](https://github.com/)
  * Text Editor: [Atom](https://atom.io/)
  * Python Distribution: >= 3.6 from [Anaconda](https://www.anaconda.com/distribution/)
  * Python IDE: [PyCharm](https://www.jetbrains.com/pycharm/)
  * Python Linter: [Pylint](https://www.pylint.org/)
  * Python Unit Tests: [Nose Tests](https://nose.readthedocs.io/en/latest/)

## Github <a name="github"></a>

* All projects are in a repository
* It's easier to condense code/projects/repositories than to split them
* Set team standards for minimum test coverage
* Repos are named after a project.
* A  one sentence project description with the name of the team owning the repo is added in the repo description.
* Repos will include at least 3 topic tags.
* Set an SLA for reviews.

### Setting Up a Project <a name="setup"></a>

* A gitignore file to prevent clutter
* A README file
  * Project description
  * Setup instructions
  * References to source material
  * References to authors / maintainers
* Dependency files for project (i.e. requirements.txt, makefile, build.sbt)
* A project folder with code
* A deployment folder with any terraform, docker, or jenkins files
* (Unless Pure Research) restrictions on pushing to master
* (Unless Pure Research) restrictions on merging to master without a PR
* Private unless welcoming open collaboration
* Team projects are assigned to team organization (no personal repos!)

### Peer Reviews (PRs) / Code Reviews (CRs) <a name="pr"></a>

Release Philosophy: Release Often and Release Small
Small, decoupled releases help streamline the release pipeline and make PRs less painful.

* Merging to Master requires a PR from a team member who did not contribute to the merge branch
* Squash on merge to facilitate easy rollback
* PRs should focus on these main areas:
  * Code Clarity
  * Commenting / Documentation
  * Logging
  * Proper Testing
  * Efficiency
  * Security
  * Following Team Conventions
* Small PRs preferred over Big PRs
* PRs are properly labeled (i.e. `Do-Not-Merge`, `Ready-For-Review`, `Work-In-Progress`)
* Mark PRs by Level of Effort (LOE) (i.e. `Big`, `Medium`, `Small`)
* Refer to agile ticket referencing work (i.e. the JIRA ticket number)
* (Unless Pure Research) set up automated testing
  * Unit testing
  * Smoke Testing
  * End to End Testing
  * Style/Type/Format Checking

For a PR checklist see [Checklists](Tips_and_Tricks.md)

For tips about PRs see [Tips and Tricks](Tips_and_Tricks.md)

Recommended Reading: [Clean Code by Robert Martin](https://www.investigatii.md/uploads/resurse/Clean_Code.pdf) <br>
Recommended Reading: [The Architecture of Open Source Applications](http://aosabook.org/en/index.html)

### Branching <a name="branching"></a>

Use a trunk based workflow. Developers make branches for particular features/bugs. These branches are merged with master when complete through a peer reviewed merge request. Specific versions are clearly tagged and linked to a particular master checkpoint.

![Git Trunk](gitflow_trunk.png)

Recommended Reading: [Learn Branching](https://learngitbranching.js.org/?locale=en_US)

## Deployment <a name="deployment"></a>

ToDO: CICD

## Acknowledgments

A big thank you to David Harrington, Petra Khaliqi, Esther Wall, Fabrice Guillaume, Thanos Kintsakis, and Bryce Crawford who have greatly shaped my view of how a well oiled tech team should operate.
