# Open Source Software (OSS) Projects on GitHub

This repository serves as a guide on how to do
Open Source Software (OSS) projects on GitHub.

## Open Source Software

Other commonly used terms are

- Free and Open Source Software (FOSS)
- Free/Libre and Open Source Software (FLOSS)

Open source software is software licensed under an open source license.

The [Open Source Initiative](https://opensource.org/) defines criteria for open source software and lists all licenses that are considered open source licenses.

### How to choose a open source license?

If you are not sure which license you should chose have a look at [Choose a License](https://choosealicense.com).
It helps you to find a license that is aligns with your intent of openness.

#### Copyleft licenses

Examples: GNU General Public License (GPL), Affero GPL (AGPL),
Lesser General Public License (LGPL), or Eclipse Public License (EPL)

#### Permissive licenses

Examples: Apache, MIT, or Berkeley Source Distribution (BSD)

### Licensing of artifacts that are not source code

For creative work such as text or images you can use a creative commons license:
[Creative Commons](https://creativecommons.org/share-your-work/cclicenses/)

## Presentation of the repository

### How to design a good README file?

The README is the first thing that people see when they visit your repository.
Thus, a good README invites people to explore your repository and use your software.

A good README should contain at least the following information:

- A brief introduction to the project
- Instructions on how to build, test, and run the project
- License information

See my template: [README.md](/templates/README.md)

### Plain text artifacts instead of binary artifacts (diagrams, etc.)

If you want to include diagrams in your README file you should use plain text formats if possible.
Binary formats are not suitable for version control systems such as Git, which results in a not transparent change history.

Examples for plain text representations:

- [Mermaid diagrams](https://github.blog/2022-02-14-include-diagrams-markdown-files-mermaid/)
- [Math formulas](https://github.blog/2022-05-19-math-support-in-markdown/)
- [Slide decks](https://marp.app)

A comparison between different plain text formats for diagrams can be found here: [https://text-to-diagram.com](https://text-to-diagram.com)

## Continuous Integration/Delivery on GitHub

Continuous integration (CI) and continuous delivery (CD) are software development practices that help to automate the build, test, and deployment process.
Providing a feedback loop for developers and users.
Since the build process is executed in a virtual environment, it is reproducible and independent of the local development environment.
Missing dependency declarations are detected early through the clean virtual environment.

Further, it is a form of documentation, because it shows how to build, test, and deploy the software.
This way, you can't forget how to perform a complex build or deployment process.

### GitHub Workflows with Actions

In GitHub, CI/CD is implemented as [GitHub workflows and actions](https://docs.github.com/en/actions/using-workflows).

Tasks that should be automated with workflows and actions:

- Testing
- Building
- Linting (ensure consistent code style)
- Deployment (e.g., as Docker image or to a cloud provider)

### Credentials and secrets

File that represent credentials or secrets should **never** be committed to the repository, **even if it is a private repository**!
If you need to store credentials or other secrets in your repository, you should use [GitHub secrets](https://docs.github.com/en/actions/reference/encrypted-secrets).

In the following example, the `google-services.json` file is created during the CI process from a GitHub secret.
The content of the file is not stored in the repository and is now shown in the logs of the CI process.

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Copy google-services.json file
      run: echo "$GOOGLE_SERVICES_JSON" >> google-services.json
      env:
       GOOGLE_SERVICES_JSON: ${{ secrets.GOOGLE_SERVICES }}
```

## Collaboration on GitHub

### Pull requests

Pull requests (also known as merge requests) are a way to propose changes to a repository.
They are also a way to discuss changes via comments and reviews.
If you are not part the owner or a collaborator of a repository, pull requests are the only way to contribute to a repository.

You can setup GitHub so that you need one or more review(s) before a pull request can be merged.
This is often done in organizations to ensure code quality and inform others about changes.

Similar to the [size of a commit](https://github.com/andreas-bauer/git-101#commit-size), a pull request should be as small as possible.
This makes it easier to review and understand the changes.

### Issues

Issues are not only to report bugs, but also a simple way for project management and coordination, e.g., to discuss new features or improvements.

You can use issues to manage

- To-do lists
- User stories
- Discuss ideas and design decisions
- Feature requests
- Answer questions

## Contribute to a OSS projects

### Good-first-issue

GitHub provides a list of issues that are suitable for beginners:
[GitHub topic](https://github.com/topics/good-first-issue)

This is a great opportunity to get started contributing to open source software.
