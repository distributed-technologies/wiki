### Helm release pipeline
When a helm chart repository is being developed there is a need to continuously release these for others to use, both for new features and for bug fixes.

The releases of the helm chart should be as follows:
1. On merge with the main branch:  
 Trigger Github workflow that, builds a package, creates a Github release, and attaches the package as an asset to the release.
2. On new asset upload to release:  
Trigger Github workflow that pushes the package to ArtifactHub with the released version. 
