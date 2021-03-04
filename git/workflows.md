# Git workflows
To use any of the git workflow templates, copy the workflow file into the /.github/workflows/ folder in your github repository. Some workflows work out of the box, while some needs to be configured for a specific usecase. This will be explicitly stated in a **configuration** paragraph under the workflow section. 

### Version Bump 
The [**Version Bump**](templates/github-workflows/bump_version_main.yaml) workflow, bumps the version tag on a commit made to the main branch. The version bump depends on the content of the commit message:

* Major (#major)
* Minor (#minor)
* Patch (#patch)

This means that if you e.g. want to bump the version v1.0.0 to v1.0.1 your commit message to main should include the string '#patch'. There is no default version bump and therefore this workflow will fail if the commit message does not contain any of the three strings required to bump a specific version.
