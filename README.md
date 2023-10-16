# workflows

The marking workflow run by all labs is found in [./.github/workflows/autograding.yml](./.github/workflows/autograding.yml).

The workflow takes one argument, `lab`, which is the number of the lab to mark. For example, to mark lab 1:
```jobs:
  autograding:
    uses: UCLCOMP0061/workflows/.github/workflows/autograding.yml@main
    with:
      lab: 1
```

The workflow is triggered when a student pushes to the `main` branch of their repo and works as follows:
- It checks out the student's code, as well as the test file and `autograding.json` from the template repo (so any changes the students make to the test and scoring files are ignored).
- The tests defined in each repo's `.github/classroom/autograding.json` are run using the `autograding` action.
- Results are displayed in the GitHub UI, as a table in the GitHub Actions job under `autograding / Autograding summary`, and as a set of badges in the README.
The badges are created in the `build-badges` job, which runs after the `autograding` job.
It uses [markpatterson27/points-bar/](https://github.com/markpatterson27/points-bar/) to create the points bar.

### Fork of autograding action
We use our own fork of the autograding action [UCLCOMP0061/autograding](https://github.com/UCLCOMP0061/autograding).
The release of the action is off the `dev` branch and enables the summary tables by default.
This enables the summary tables to be generated.
The fork is based on [markpatterson27/autograding](https://github.com/markpatterson27/autograding)

