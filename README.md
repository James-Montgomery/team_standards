# Team Standards

This document is meant to be the scaffold for setting team standards for a
data science / machine learning team. Many of these are basic software
engineering standards / best practices that help facilitate team collaboration
in an organized manner. I use this document when setting up new projects /
development teams. The sections of this document are meant to be heavily
modified to fit the preferences of the user / team.

<!-- TOC -->
* [Communication Standards](#communication)
* [Coding Standards](#coding_standards)
  * [Prioritization](#prioritization)
  * [Python Style and Formatting](#style)
  * [Testing Standards](#testing)
  * [Tools](#tools)
* [Github](#github)
  * [Setting Up a Project](#setup)
  * [Code Reviews](#cr)
  * [Model Reviews](#mr)
  * [Branching](#branching)
* [Deployment](#deployment)
<!-- TOC -->

## Communication Standards <a name="communication"></a>

Communication standards are the backbone of any team. Setting basic rules
around the proper forums and form of discourse can help maintain healthy
relationships between teammates. Too little communication leads to
disorganization, but too much communication doesn't leave time to actually work!

* Be respectful
* Assume positive intent
* KISS (Keep It Simple Stupid)
 * Be clear
 * Be simple
 * Be concise
 * Don't use jargon if you don't need to
* Respect colleagues' preferred working hours
* Respect colleagues' time zones
* Headphones on means "let me work"
* Respect colleagues' time (sometimes we need to be heads down)
* Slack > Google Hangouts
* General team dialogue is for non-dev slack channels
* Technical dialogue (PRs, code questions, bug reporting) is for dev slack channels
* NO REPLY ALL EMAILS (pain of death and/or humiliation)
* No meetings after 3pm on Friday
* **Don't be jerk**
* Don't check phones during meetings
* Meetings are time boxed and don't bleed over
* Someone is always designated the "note taker"

## Coding Standards <a name="coding_standards"></a>

Coding standards are what people usually think of as "software engineering team
standards". These standards set the best practices that the team pledges to
follow when writing code. These practices are meant to encourage maintainable,
understandable, working code that engineers enjoy working with!

### Prioritization <a name="prioritization"></a>

The team adopts the [Agile Scrum](https://www.cprime.com/resources/what-is-agile-what-is-scrum/)
style of work assignment using the [SAFE framework](https://www.scaledagile.com/enterprise-solutions/what-is-safe/).
Developers only work on assigned tasks unless otherwise decided by scrum
master / tech lead.

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
* The last sprint in every PI is dedicated just to tech debt / model debt

**Note:** Model debt is similar to tech debt. We often take short cuts to get a
model to production. We say that we will deploy a minimal viable product (MVP)
and the improve upon it iteratively. It's important that we go back and fix the
modeling short cuts that we took to get to the MVP.

### Python Style and Formatting <a name="style"></a>

Style is important for maintainability. Styling encourages good documentation,
uniformity of outputs, and code clarity.

* [PEP8](https://www.python.org/dev/peps/pep-0008/#naming-conventions) Conventions
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

### Testing Standards <a name="testing"></a>

In many ways test code makes or breaks a project. Catching problem spots as or
before they occur is a huge part of creating a maintainable project.

* Projects have all three tiers of the testing pyramid
  * Unit Testing
  * Smoke (Integration) Testing
  * End to End (E2E) Testing
* Unit tests rigorously examine individual units / components of code. The less complex the better.
  * Rule of thumb: One assert per test! (Just a rule of thumb...)
  * Unit tests handle their own setup and tear down
* Smoke tests are sparse sanity checks against core functionality.
* E2E testing are comprehensive tests of the entire project.
* Use mocking when called for.
* Team sets a minimum acceptable level of coverage for code.
* Tests are clear and well documented.
* Tests are as automated as possible.

### Tools <a name="tools"></a>

It's important to use similar tools so that teammates can easily help each other
debug technical problems. While it isn't essential that every teammate use the
same IDE, for example, it can be helpful to all use somewhat similar development
environments. A good team lead will strike a balance between micromanaging tool
use and establishing common patterns and workflows in the team.

  * Agile: [JIRA](https://www.atlassian.com/software/jira) or [Trello](https://trello.com/en-US)
  * Code Versioning: [Github](https://github.com/)
  * Containerizing: Docker
  * Cloud Deployments: Terraform
  * Text Editor: [Atom](https://atom.io/)
  * Python Distribution: >= 3.6 from [Anaconda](https://www.anaconda.com/distribution/)
  * Python IDE: [PyCharm](https://www.jetbrains.com/pycharm/)
  * Python Linter: [Pylint](https://www.pylint.org/)
  * Python Unit Tests: [Nose Tests](https://nose.readthedocs.io/en/latest/)

## Github <a name="github"></a>

Versioning standards are important to make sure that a record of work is kept
and accessible. This is not only for the sake of accountability, but also to
help with bugs. If a production roll back is required to fall back to a past
stable version...we want to actually have a record of that version!

* All projects are in a repository
* It's easier to condense code/projects/repositories than to split them
* Set team standards for minimum test coverage
* Repos are named after a project.
* A  one sentence project description with the name of the team owning the repo is added in the repo description.
* Repos will include at least 3 topic tags.
* Set an SLA for reviews.
* Branch protections are added to ensure proper branching strategies and PRs
* [Semantic versioning](https://devhints.io/semver) using git tagging and releases

### Setting Up a Project <a name="setup"></a>

New projects should all be of similar form to create a sense of continuity. It
can be helpful to create [template repositories](https://help.github.com/en/articles/creating-a-template-repository).

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
* Deployable units should share a repository.
  * i.e. the lambda an api is deployed on should have a terraform definition in the same repo as the api code

Here is an example template for building proof of concept python tools:
[LINK](https://github.com/James-Montgomery/python_project_template)

### Peer Reviews (PRs) / Code Reviews (CRs) <a name="cr"></a>

Release Philosophy: Release Often and Release Small <br>
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

### Peer Reviews (PRs) / Model Reviews (MRs) <a name="mr"></a>

One of the most overlooked aspects of a modeling / data science team is model
review. We often focus on code review standards forgetting that we should also
be vetting our models with a "jury of our peers".

* Models are formulated as packages, modules, or classes for easy of reuse and testing
* If appropriate, offline testing results should be part of the model review
* If appropriate, online testing results should be part of the model review
* A clear description of the model should be available as pre-reading material
* All papers relevant to the model are referenced in documentation by title, publication year, and authors
* Mathematical conventions are stated in model documentation
* Model code mirrors the mathematical conventions (i.e. for variable naming)
* Model performance metrics should tie back to business value
* Data sources for the model are well documented (including how to access / fetch the data)
* Preprocessing of data is clearly explained
* Try to hold model reviews in person
* Try to hold model reviews in rooms with whiteboards

### Branching <a name="branching"></a>

There are many different branching strategies that a team can use to manage updates
to their projects in Github. Pick a strategy that meets your needs and stick to it.
A bad branching strategy can make rollbacks and releases a nightmare, so choose carefully.
Enforce your branching strategy using branch protections in Github.

Recommended Reading: [Learn Branching](https://learngitbranching.js.org/?locale=en_US)

## Deployment <a name="deployment"></a>

* (Cloud) Infrastructure (Infra) is divided by importance
  * Dev: Infra for development and experimentation.
  * QA: Infra for quality assurance of next "stable" version to be pushed to prod.
  * Prod: Infra for stable versions of project.
* CICD includes automated testing! No if and or buts.

## Acknowledgments

A big thank you to David Harrington, Petra Khaliqi, Esther Wall, Fabrice Guillaume,
Thanos Kintsakis, and Bryce Crawford who have greatly shaped my view of how a well
oiled tech team should operate.
