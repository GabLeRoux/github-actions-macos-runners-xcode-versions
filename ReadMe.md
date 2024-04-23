## GitHub Actions: macOS Runners and Xcode Versions

This repository demonstrates the use of GitHub Actions to print the Xcode version and macOS version on different macOS
runner environments.

### Overview

The project currently contains [a single GitHub Actions workflow file](.github/workflows/main.yml) that runs on
the `push` event to the `main` branch. The workflow uses a matrix strategy to test the workflow on various macOS runner
environments, including:

- `macos-11`
- `macos-12`
- `macos-13`
- `macos-14`
- `macos-latest`

Each job in the matrix runs two steps:

1. **Print Xcode Version**: This step uses the `xcodebuild -version` command to print the installed Xcode version.
2. **Print OS Version**: This step uses the `sw_vers -productVersion` command to print the macOS version.

### Usage

To use this project, simply create a new repository and copy the workflow file into the `.github/workflows` directory.
You can then customize the matrix to include the macOS runner environments you need to test.

### Results

Here's a table summarizing the macOS and Xcode versions for each runner image based on the outputs you've provided.

Last update : 2024-04-23

| Runner Image | macOS Version | Xcode Version | Xcode Build Version |
|--------------|---------------|---------------|---------------------|
| macos-11     | 11.7.10       | 13.2.1        | 13C100              |
| macos-12     | 12.7.4        | 14.2          | 14C18               |
| macos-13     | 13.6.6        | 15.0.1        | 15A507              |
| macos-14     | 14.4.1        | 15.0.1        | 15A507              |
| macos-latest | 12.7.4        | 14.2          | 14C18               |

### Why?

I wanted to know what macOS versions and Xcode versions are available on the GitHub Actions macOS runners and couldn't
find an up to date list. It also helped resolving
the [following issue](https://github.com/game-ci/unity-builder/issues/642#issuecomment-2072058707).

Interestingly, [the following documentation](https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners)
indicates this :

> The macos-latest label currently uses the macOS 14 runner image.

But at the time of writing, the `macos-latest` runner image uses macOS 12.7.4. 🤦

### Nice to have

- [ ] Implement a cron job to run the workflow on a regular schedule.
- [ ] Add a step that will update this readme's table with the latest macOS and Xcode versions.

### Contributing

Feel free to contribute.

## License

[MIT](LICENSE.md) © [Gabriel Le Breton](https://gableroux.com)
