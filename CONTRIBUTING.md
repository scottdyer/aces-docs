<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the ACES Documentation -->

# Contributing to ACES Documentation

Thank you for your interest in contributing documentation to the ACES project.

You don’t need to be a programmer or Git expert to help. All documentation is
written in simple Markdown files, which makes it easy for anyone to contribute.

If you’re not comfortable with the Git workflow (forking, cloning, branching,
committing, and submitting pull requests), that’s okay—just reach out and we’ll
help get your content (text, images, or graphics) formatted into Markdown.

This document explains the contribution process and how the documentation site
is built.

## Quick Links

- **Published Documentation:** <https://docs.acescentral.com>
- **MkDocs User Guide:** <https://www.mkdocs.org/user-guide/>
- **Material for MkDocs Theme:** <https://squidfunk.github.io/mkdocs-material/>
- Need help? Reach out on the **ASWF Slack:** <https://aswf.slack.com>

## How the Documentation Is Built

### Publishing

The ACES Documentation website is built with [MkDocs](https://www.mkdocs.org)
using the [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
theme. Markdown files are converted to HTML, and the site structure (including
navigation) is defined in  `mkdocs.yml`. 

Changes to the `main` branch are automatically deployed via a [GitHub
Action](.github/workflows/main.yml). Updates publish to
<https://docs.acescentral.com>.

- To update existing content, edit the relevant `.md` file. 
- To add new pages, create a new `.md` file and add it to the `nav:` section of
  `mkdocs.yml`.

### Previewing Locally

You can preview your changnes before submitting them by using Docker with the
provided `Dockerfile`:

1.  Ensure Docker is installed and running. 
2.  In your terminal, navigate to your local clone of the `aces-docs`
    repository. 
3.  Run: `docker compose up`
4.  Once the build completes, the site will be available at
    <http://0.0.0.0:8000>.
5.  The site will auto-refresh as you save changes to the files. Continue
    editing until you're satisfied, then submit a pull request.

## Legal Requirements

ACES is a project hosted by the Academy Software Foundation (ASWF) and follows
the open source software best practice policies of the ASWF TAC with guidance
from the Linux Foundation.

### License

ACES Documentation is licensed under the [Creative Commons Attribution 4.0
International License](./license). New contributions should abide by that
license. 

### Contributor License Agreement (CLA)

To maintain the legal integrity of the project's codebase, we require all
contributors to complete a **Contributor License Agreement (CLA)**.

ACES uses [EasyCLA](https://lfx.linuxfoundation.org/tools/easycla) for managing
CLAs, which automatically checks to ensure a CLA has been signed by a
contributor before a commit can be merged.

* If you are an individual writing the code on your own time and you're SURE you
  are the sole owner of any intellectual property you contribute, you can [sign
  the CLA as an individual
  contributor](https://docs.linuxfoundation.org/lfx/easycla/contributors/individual-contributor).

* If you are writing the code as part of your job, or if there is any
  possibility that your employers might think they own any intellectual property
  you create, then you should use the [Corporate Contributor Licence
  Agreement](https://docs.linuxfoundation.org/lfx/easycla/contributors/corporate-contributor).

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

### Copyright Notices
All new files should include a licence statement and copyright.

``` md
<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the ACES Documentation -->
```