# Git workflows
To use any of the git workflow templates, copy the workflow file into the /.github/workflows/ folder in your github repository. Some workflows work out of the box, while some needs to be configured for a specific usecase. This will be explicitly stated in a **configuration** paragraph under the workflow section. 

### Version Bump 
The [**Version Bump**](../templates/github-workflows/bump_version_main.yaml) workflow, bumps the version tag on a commit made to the main branch. The version bump depends on the content of the commit message:

* Major (#major)
* Minor (#minor)
* Patch (#patch)

This means that if you e.g. want to bump the version v1.0.0 to v1.0.1 your commit message to main should include the string '#patch'. There is no default version bump and therefore this workflow will fail if the commit message does not contain any of the three strings required to bump a specific version.

### Build and release helm chart
The [**Build and release helm chart**](../templates/github-workflows/build_release_helm_chart.yaml) workflow, lints, builds and releases a helm chart to github while creating a release tag from the version in the helm chart. The workflow is triggered when there is a push to main branch. 

#### configuration
In the workflow you can set a value for **USE_QUOTES_HELM** to true or false.
If set to true, you state that your helm chart version is marked with quotes e.g. **version: "v1.0.0"**, else the version is presented without quotes: **version: v1.0.0**.
This is important for the workflow to update the version in the helm chart.
