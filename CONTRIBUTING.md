<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the ACES Documentation -->

# Contributing to ACES Documentation

Thank you for your interest in contributing documentation to the ACES project.

Even if you are not a programmer or just lack comfortability with contributing
through the Git workflow, you can still contribute!

All documentation content is generated from simple Markdown text files. This
keeps it is easy for programmers and non-programmers alike to contribute. If you
are intimidated by the process of forking, cloning, branching, committing, and
submitting back via a pull request, that's ok.

Reach out to us and we can help get your content-including any text, images, or
graphics-formatted into Markdown.

This document explains details of the contribution process and procedures.

## How the Documentation Is Built

### Publishing

The ACES Documentation website is built using [MkDocs](https://www.mkdocs.org)
using the [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
theme to generate HTML from simple Markdown files. The site configuration,
including navigation, is managed through the `mkdocs.yml` file. 

Changes are automatically deployed via a [GitHub
Action](.github/workflows/main.yml) triggered when new commits are made on `main`.
Updates to `main` will publish to 
[https://docs.acescentral.com](https://docs.acescentral.com).

To update existing content, simply modify the relevant `.md` file. 

To add new pages, create a new `.md` file and add a reference to it in the `nav:`
section found in `mkdocs.yml`.

### Previewing

By using Docker and the included `Dockerfile`, you can easily spin up a local
version of the docs to preview your changes locally and make sure they appear
exactly as you want before submitting your pull request. 

1.  Ensure Docker is installed and running. 
2.  In your terminal, navigate to the local clone of the `aces-docs` repository. 
3.  Type the command: `docker compose up` This will spin up a Docker container
    for aces-docs. 
4.  If the build completes and the Docker container is running, a local version
    of the doc site will then be viewable at
    [http://0.0.0.0:8000](http://0.0.0.0:8000).
5.  The doc site should refresh whenever changes are saved. So continue to
    adjust your files, hit save, and preview the changes until you are
    satisfied. Once satisfied with your updates, proceed to submit a pull
    request.

## Legal Requirements

ACES is a project hosted by the Academy Software Foundation (ASWF) and follows
the open source software best practice policies of the ASWF TAC with guidance
from the Linux Foundation.

### License

ACES Documentation is licensed under the [Creative Commons Attribution 4.0
International License](./license). New contributions should abide by that license. 

All new files must include a licence statement and copyright.

``` md
<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the ACES Documentation -->
```

### Contributor License Agreement (CLA)

To maintain the legal integrity of the project's codebase, we require all
contributors to complete a **Contributor License Agreement (CLA)**.

ACES uses [EasyCLA](https://lfx.linuxfoundation.org/tools/easycla) for managing
CLAs, which automatically checks to ensure a CLA has been signed by a contributor
before a commit can be merged.

* If you are an individual writing the code on your own time and you're SURE you
  are the sole owner of any intellectual property you contribute, you can [sign
  the CLA as an individual contributor](https://docs.linuxfoundation.org/lfx/easycla/contributors/individual-contributor).

* If you are writing the code as part of your job, or if there is any
  possibility that your employers might think they own any intellectual property
  you create, then you should use the [Corporate Contributor Licence Agreement](https://docs.linuxfoundation.org/lfx/easycla/contributors/corporate-contributor).

The ACES CLA's are the standard forms used by Linux Foundation projects and
[recommended by the ASWF
TAC](https://github.com/AcademySoftwareFoundation/tac/blob/main/process/contributing.md#contributor-license-agreement-cla).

### Commit Sign-Off

Every commit must be signed off. That is, every commit log message must include
a “`Signed-off-by`” line (generated, for example, with “`git commit --signoff`”
or "`git commit -s`"), indicating that the committer wrote the code and has the
right to release it under the [license](LICENSE).

Here is an example Signed-off-by line, which indicates that the submitter
accepts the DCO:

`Signed-off-by: John Doe <john.doe@example.com>`

If John Doe has signed an individual CLA, or his corporation's CLA Manager has
included his GitHub account in a corporate CLA approved list, his pull request
can be merged. Otherwise the EasyCLA system will provide instructions on signing
a CLA, or request inclusion in an existing corporate CLA approved list.

See the [ASWF TAC
CONTRIBUTING.md](https://github.com/AcademySoftwareFoundation/tac/blob/main/process/contributing.md#contribution-sign-off)
file for more information on this requirement.