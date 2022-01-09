# build-monogame

This action allows you to build your monogame project via **msbuild**.

The action first checks out your repo and sets up `dotnet`,`msbuild`, as well as the `mgcb` build tool.
It then builds the `Content` resources using `mgcb` and then builds the game/project using `msbuild`.

# Usage

```yml
name: Run checks on incoming PR

on:
  pull_request:
    branches: [master, release, develop]

  # allow running this workflow manually
  workflow_dispatch:

jobs:
  android-build-check:
    runs-on: windows-latest

    steps:
      - name: Build android project
        uses: igotinfected-ci/build-monogame@v1
        with:
          solution-path: '${{ github.workspace }}\Project\Project.sln'
          content-mgcb-path: '${{ github.workspace }}\Project\Android\Content'
          content-mgcb-platform: "Android"
          project-path: '${{ github.workspace }}\Project\Android'
          csproj-path: '${{ github.workspace }}\Project\Android\Android.csproj'
          build-target: "PackageForAndroid"
          build-configuration: "Release"
```
# License

The scripts and documentation in this project are released under the [MIT License](LICENSE)
