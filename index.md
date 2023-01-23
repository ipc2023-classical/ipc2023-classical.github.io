# International Planning Competition 2023 Classical Tracks

This is the website for the classical (sequential, deterministic) track of the
[IPC 2023](https://ipc2023.github.io).
This is the 10th IPC containing classical tracks making it the oldest part of
IPC.


## Calls
Please forward the following calls to all interested parties.

 - [Call for Domains](calls/ipc2023-call-for-domains.txt)


## Preliminary Schedule

| Event                                         | Date               |
|:----------------------------------------------|:-------------------|
| Call for domains                              | August 1, 2022     |
| Call for participation                        | October, 2022      |
| Domain expression of interest deadline        | September 30, 2022 |
| Domain submission deadline                    | December 9, 2022   |
| Demo problems provided                        | December, 2022     |
| Planner registration                          | January 13, 2023   |
| Feature stop (final planner submission)       | March 10, 2023     |
| Planner Abstract submission deadline          | April 14, 2023     |
| Contest run                                   | May - June, 2023   |
| Results announced                             | July, 2023         |
| Result analysis deadline                      | August, 2023       |


## Tracks

### Optimal Track
 - single CPU core
 - 8Gb memory limit
 - 30min time limit
 - Plans must be optimal
 - The score of a planner is the number of solved tasks
 - If a suboptimal or invalid plan is returned, all tasks in the domain are counted as unsolved.
 - If that happens in more than one domain, the entry is disqualified.

### Satisficing Track
 - single CPU core
 - 8Gb memory limit
 - 30min time limit
 - Multiple plans can be returned, the one with the lowest cost is counted.
 - The score of a planner on a solved task is the ratio C\*/C where C is the
   cost of the cheapest discovered plan and C\* is the cost of a reference plan. The score on an unsolved task is 0. The score of a planner is the sum of its scores for all tasks.
 - If an invalid plan is returned, all tasks in the domain are counted as unsolved.
 - If that happens in more than one domain, the entry is disqualified.

### Agile Track
 - single CPU core
 - 8Gb memory limit
 - 5min time limit
 - The cost of the discovered plan is ignored, only the CPU time to discover a plan is counted.
 - The score of a planner on a solved task is 1 if the task was solved within 1 second and 0 if the task was not solved within the resource limits. If the task was solved in T seconds (1 ≤ T ≤ 300) then its score is 1 - log(T)/log(300). The score of a planner is the sum of its scores for all tasks.
 - If an invalid plan is returned, all tasks in the domain are counted as unsolved.
 - If that happens in more than one domain, the entry is disqualified.


## PDDL Fragment
IPC 2023 will use a subset of PDDL 3.1, as done since IPC 2011. Planners must
support the subset of the language involving STRIPS, action costs, negative
preconditions, and conditional effects (possibly in combination with forall,
as in IPC 2014 and 2018). We will also consider including domains with
disjunctive preconditions and existential quantifiers, in which case we
provide an automatic translation compiling these features away, and we run all
planners on both variants and select the best result per instance.

Most planners in previous IPCs rely on a grounding procedure to instantiate
the entire planning task prior to start solving it. In IPC 2023, we will
follow in the steps of the previous IPC by including domains and problems that
are hard to ground.


## Registration
To register a team, the participants need to send an e-mail with a
subject containing "[Registration]" to
[ipc2023-classical@googlegroups.com](ipc2023-classical@googlegroups.com).
The e-mail must contain:
1. names of participants,
2. e-mail contacts,
3. github usernames,
4. the number of repositories (code bases) the team needs (multiple
   planners can be built from the same repository),
5. a (tentative) list of tracks, where the team intends to submit their
   planners; if you are interested in a different track than optimal,
   satisficing, or agile, please, let us know too.

Based on that, we will create private repositories under the
[ipc2023-classical](https://github.com/ipc2023-classical) organization and add
all participants as users with with write access and participants can commit
to the repository as they wish until the "feature stop" deadline
(March 10, 2023).

## Planner Submission

As in previous editions, the competitors must submit the source code of their
planners that will be run by the organizers on the actual competition
domains/problems, unknown to the competitors until this time. This way no
fine-tuning of the planners will be possible.

As in the previous IPC 2018, we will use the container technology Apptainer
(formerly known as Singularity) to promote reproducibility and help with
compilation issues that have caused problems in the past. In contrast to the
previous IPC, we will host repositories of planners ourselves. The repositories
will be hosted on Github under the ipc2023-classical organization, and they will
be kept private until the end of the competition when we make them public, i.e.,
after the competition is concluded, we plan to make all planners, domains, and
all related data accessible from one place.

This year, we will also allow to submit multiple planners to multiple tracks
from a single repository. In each repository, we only consider the branch
`ipc2023-classical`. Feel free to use other branches for development as you wish, but we will
ignore them. Any file called `Apptainer.<shortname>` in the root directory of
this branch defines one entry. For the `<shortname>`, please use the name and
variant of your planner as a short identifier (a single word, up to 16
characters long, starting with a letter, using only letters, digits, and
underscores). If you build different versions of your planner from the same
repository, use a different `<shortname>` per version. A single entry can
participate in multiple tracks, see "Apptainer Images" for details.

## Apptainer Images

We prepared a [demo submission](https://github.com/ipc2023-classical/submission-demo)
that showcases how to set up the repository and Apptainer scripts.

Your Apptainer recipe files have to specify the following labels:

* `Name`: name of the planner
* `Description`: a short description of your planner
* `Authors`: a list of authors, including contact email addresses (`Firstname Lastname <firstname.lastname@email.example>`)
* `License`: the license under which you publish this code. It has to be permissive enough to allow us to publish the code after the competition.
* `Tracks`: a comma-separated list of tracks this image should participate in. Use only the following terms to identify tracks: `optimal`, `satisficing`, `agile`. For example, to run your planner in the optimal and agile track use `Tracks optimal, agile`.
* Your Apptainer recipe must contain all of the following labels describing
supported PDDL features. Each label must be set to either `yes` or `no`, or if
the feature is supported only partially, then set it to `partially, ` followed
by the description of what is and isn't supported:

  * `SupportsDerivedPredicates`: specify whether your planner supports `(:derived ...)` construct
  * `SupportsUniversallyQuantifiedPreconditions`: `(forall ...)` in actions' preconditions
  * `SupportsExistentiallyQuantifiedPreconditions`: `(exists ...)` in actions' preconditions
  * `SupportsUniversallyQuantifiedEffects`: `(forall ...)` in actions' effects
  * `SupportsNegativePreconditions`: `(not (...))` in actions' preconditions
  * `SupportsEqualityPreconditions`: `(= ?x obj1)`, for action parameter `?x` and constant `obj1`, in actions' preconditions
  * `SupportsInequalityPreconditions`: `(not (= ?x ?y))` or `(not (= ?x obj1))`, for action parameters `?x` and `?y`, and constant `obj1`, in actions' preconditions
  * `SupportsConditionalEffects`: `(when ...)` in actions' effects
  * `SupportsImplyPreconditions`: `(imply ...)` in actions' preconditions

To improve reproducibility, we require Apptainer images to be self-contained and licensed appropriately.

* The recipe should copy the content of the repository into the container at the
start of the build. In particular, do not clone repositories in the recipe. 

* If you use third-party libraries, either install them through standard package
managers (apt, yum, pip), or copy them into the repository. Please do not use
git submodules to include dependencies.

* If possible, use explicit versions. For example, do not use `ubuntu:latest` as
your base image but pick a specific version. If you install packages through pip,
pick specific versions of those packages.

* If your build depends on closed-source libraries that require a license,
please contact us.

* If you use a portfolio of existing planners, it is up to you to get permission
from the authors of the portfolio components and give appropriate credit and
licensing. We recommend contacting the planner authors.

In addition to reproducibility and licensing issues, we ask that you make your image as small as possible using the following tricks:

* Use a [multi-stage build](https://apptainer.org/docs/user/latest/definition_files.html#multi-stage-builds)
where one stage is used for compiling the planner and one for running the
planner. Copy the compiled planner from the first stage to the second, and only
copy/install the files that are required at runtime. The size of the compilation
stage then does not matter and the second stage can be limited to contain only
essential files.

* [Strip binaries](https://www.man7.org/linux/man-pages/man1/strip.1.html) after compilation

* Use small packages. For example, use python-minimal instead of python if possible.



## Bug-fixing Policy

When a competition team registers (see above), we create a private repository
(or multiple repositories if needed) and add competitors as users with write
access. After the “feature stop” deadline (March 10, 2023), we allow competitors
to send only a pull request with bug fixes. We will review every pull request
with its accompanying description of the bug fix to make sure that no big
changes or parameter tuning is committed to the repository.

To help us with the debugging process, in contrast to previous years, planner
authors will be responsible for detecting if the run of their planner and our
analysis of the results was successful. After the feature stop deadline, we will
run all planners on all tasks and give the participants access to the results of
their planners. For each run, the data will contain the log files of the
planner, measured time and memory consumption, exit code, and our conclusion
about what this means in terms of solving the instance. We ask participants
to check their results for any errors. If an error was caused by a bug in the
planner, please send a pull request on Github with a detailed description of the
bug and the fix. If the error was on our side (e.g., malformed PDDL) let us know
as soon as possible. We will do at least two rounds of this starting after the
"feature stop" deadline (exact timeline TBD).


## Planner Abstract Submission

All competitors must submit an abstract (max. 300 words) and an up to 8-page
paper describing their planners. After the competition we ask the participants
to analyze the results of their planner and submit an extended version of their
paper. An important requirement for IPC 2023 competitors is to give the
organizers the right to post their paper and the source code of their planners
on the official IPC 2023 web site, and the source code of submitted planners
must be released under a license allowing free non-commercial use.


## Organizers
 - [Daniel Fišer](https://danfis.cz) (Saarland University)
 - [Florian Pommerening](http://ai.cs.unibas.ch/people/pommeren/index.html) (University of Basel)

Contact us: [ipc2023-classical@googlegroups.com](ipc2023-classical@googlegroups.com)
