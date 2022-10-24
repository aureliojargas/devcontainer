# aureliojargas/devcontainer

My default image for [devcontainer](https://docs.github.com/en/codespaces/setting-up-your-project-for-codespaces/introduction-to-dev-containers), to be used in VS Code and GitHub Codespaces.

Image identifier: `ghcr.io/aureliojargas/devcontainer:latest`

## The Docker image

This is Ubuntu 22.04 with `git` plus dev tools for Shell (`shfmt`, `shellcheck`) and Python.

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

- https://github.com/aureliojargas/clitest/blob/master/.devcontainer/devcontainer.json

## Automatic publishing

Every merge on the `main` branch will trigger a build and push for the Docker image into the GitHub Container Registry.

The image will always be tagged only with `latest` to keep everything simple.

Details in [.github/workflows/publish.yaml](.github/workflows/publish.yaml).
