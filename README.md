# SGKB Setup Action

An action to conveniently setup pipelines according to our standards.
* Setup Node.js and NPM cache (version taken from `.nvmrc`)
* Setup Java and Gradle cache (version and distro via option with defaults)

## Usage

```yaml
name: CI

jobs:
  deploy:
    # This action currently only works on linux!
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: stgallerkb/setup-action@v1.0
        with:
            azure-npm-user: ${{ secrets.AZURE_NPM_USER }}
            azure-npm-secret: ${{ secrets.AZURE_NPM_PAT }}
            azure-npm-registry: ${{ secrets.AZURE_NPM_REGISTRY }}
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
| `timezone`           | :x:                 | Europe/Zurich | The timezone to use (Linux only)         |

## Release

To create a new release follow this guide:

```sh
git tag -a -m "Description of this release" v1.0
git push --follow-tags
```

You may also want to add or update the base major tag, following:

```sh
# if the tag already exists
git push --delete origin v1
git tag -a v1 
git push --follow-tags
```