### Build and release helm chart
The [**Build and release helm chart**](templates/github-workflows/build_release_helm_chart.yaml) workflow, lints,builds and releases a helm chart to github while updating the chart version to the most resent tagged version i nthe git repository.

#### Configuration
In the workflow you can set a value for **USE_QUOTES_HELM** to true or false.
If set to true, the version in the helm chart is stated as **version: "v1.0.0"**, else the version is presented without quotes: **version: v1.0.0**.
This is important for the workflow to update the version in the helm chart.
