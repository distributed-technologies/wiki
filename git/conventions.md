# Conventions

## make

All repositories that generate artifacts or can be tested
should contain a **Makefile**.

The following commands have an agreed upon functionality:

- all
- build
- clean
- help

### all
The default command of the Makefile, should build the
entire repo if contains any changes, and generate the required artifacts.

### build
Force the build of artifacts 


### clean
Should clean the repo so all generated files are removed,
and the folder is in clean state, similar to a newly cloned
repo.

### help 
List the possibly commands for the Makefile and describes
each of the commands.




## Folder conventions

This section describes a list of folders with we all 
agree on is our default way to add additional folders
so they are named the same across platforms.

### /docs

This folder should contain all .md files, pictures
and other files that are used to document the repository.

### /chart

This is the folder for all our repos containing a helm chart.
The chart will always be in the chart folder, which may
contain 3 folders:

- ./charts/
- ./templates/
- ./crds/

and 3 files:

- ./Chart.yaml
- ./values.yaml
- ./values.schema.json

The values.schema.json is used to validate the value input 
files, and should always ensure correct use of the chart, 
more info can be found here: https://helm.sh/docs/topics/charts/

### /artifacts

Common folder for all artifacts generated as part of the make process.
