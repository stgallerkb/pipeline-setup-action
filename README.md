# SGKB Setup Action

An action to conveniently setup pipelines according to our standards.
* Setup Node.js and NPM cache (version taken from `.nvmrc`)
* Setup Java and Gradle cache (version and distro via option with defaults)

## Usage

```yaml
name: CI

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: stgallerkb/setup-action@v1.0
```

## Options

| Name                 | Required            | Default Value | Description                              |
|----------------------|---------------------|---------------|------------------------------------------|
| `use-node`           | :x:                 | `true`        | Indicator to setup Node.js and NPM cache |
| `use-java`           | :x:                 | `true`        | Indicator to setup Java and Gradle cache |
| `java-version`       | :x:                 | 17            | Java version to use                      |
| `java-distribution`  | :x:                 | zulu          | Distirbution to use, see [supported distributions](https://github.com/actions/setup-java#supported-distributions) |
| `azure-npm-registry` | :white_check_mark:  | –             | Azure NPM registry URL                   |
| `azure-npm-user`     | :white_check_mark:  | –             | Azure NPM registry user                  |
| `azure-npm-secret`   | :white_check_mark:  | –             | Azure NPM user secret (PAT)              |

## Release

To create a new release follow this guide:

```sh
git tag -a -m "Description of this release" v1.0
git push --follow-tags
```