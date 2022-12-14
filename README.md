# aureliojargas/devcontainer

My default image for [devcontainer](https://docs.github.com/en/codespaces/setting-up-your-project-for-codespaces/introduction-to-dev-containers), to be used in VS Code and GitHub Codespaces.

Image identifier: `ghcr.io/aureliojargas/devcontainer:latest`

## The Docker image

This is Ubuntu 22.04 with `git` plus dev tools for Shell (`shfmt`, `shellcheck`) and Python (`black`, `pylint`).

There's also some extra tools that I cannot work without:

- `ed` to create/edit git commit messages ([because](https://github.com/aureliojargas/dotfiles/commit/aa46442185c0ef2ddd74ed842fb64fa3a9235838))
- `fish` for a nice interactive shell experience
- `git-revise` to change commit history effortlessly
- `tig` to view commit history easily
- `vim` to the rescue when there's no VS Code

Details in [.devcontainer/Dockerfile](.devcontainer/Dockerfile)

## How to use it

Just add the following line to your `.devcontainer/devcontainer.json` file:

```json
"image": "ghcr.io/aureliojargas/devcontainer",
```

Examples:

- https://github.com/aureliojargas/replace/blob/main/.devcontainer/devcontainer.json

- https://github.com/aureliojargas/sedsed/blob/main/.devcontainer/devcontainer.json

- https://github.com/aureliojargas/clitest/blob/main/.devcontainer/devcontainer.json

- https://github.com/aureliojargas/sedparse/blob/main/.devcontainer/devcontainer.json

- https://github.com/aureliojargas/txt2regex/blob/main/.devcontainer/devcontainer.json

## Personalization

[My dotfiles](https://github.com/aureliojargas/dotfiles) are inserted into the running container `$HOME` during the init phase, by automatically running the [setup script](https://github.com/aureliojargas/dotfiles/blob/main/setup). Note that this repository must be set in GitHub→Settings→Codespaces→Dotfiles.

**My VS Code settings and extensions** are synchronized into the web VS Code instance in Codespaces by using the official [Settings Sync](https://code.visualstudio.com/docs/editor/settings-sync) feature.

## Automatic publishing

Every merge on the `main` branch will trigger a build and push for the Docker image into the GitHub Container Registry.

The image will always be tagged only with `latest` to keep everything simple.

Details in [.github/workflows/publish.yaml](.github/workflows/publish.yaml).

## References

- Docker images: https://github.com/devcontainers/images/tree/main/src
- Features: https://github.com/devcontainers/features/tree/main/src
- Run in CI: https://github.com/devcontainers/ci#github-action
