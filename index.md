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
As in previous editions, the competitors must submit the source code of their
planners that will be run by the organizers on the actual competition
domains/problems, unknown to the competitors until this time. This way no
fine-tuning of the planners will be possible.

All competitors must submit an abstract (max. 300 words) and an up to 8-page
paper describing their planners. After the competition we ask the
participants to analyze the results of their planner and submit an extended
version of their paper. An important requirement for IPC 2023 competitors is
to give the organizers the right to post their paper and the source code of
their planners on the official IPC 2023 web site, and the source code of
submitted planners must be released under a license allowing free
non-commercial use.

As in the previous IPC 2018, we will use the container technology
[Apptainer](http://apptainer.org/) (formerly known as Singularity) to promote
reproducibility and help with compilation issues that have caused problems in
the past.
In contrast to the previous IPC, we will host repositories of planners
ourselves.
The repositories will be hosted on Github under the
[ipc2023-classical](https://github.com/ipc2023-classical) organization, and
they will be kept private until the end of the competition when we make them
public, i.e., after the competition is concluded, we plan to make all
planners, domains, and all related data accessible from one place.

When a competition team registers (see below), we create a private repository
(or multiple repositories if needed) and add competitors as users with write
access.
After the "feature stop" deadline (March 10, 2023), we allow competitors to
send only a pull request with bug fixes.
We will review every pull request with its accompanying description of the bug
fix to make sure that no big changes or parameter tuning is committed to the
repository.
To help us with the debugging process, in contrast to previous years, planner
authors will be responsible for detecting if the run of their planner and our
analysis of the results was successful. We will add more details on this
later.


This year, we will also allow to submit multiple planners to multiple tracks
from a single repository (see the Planner Submission section below).
So, each team will need only one repository per code-base and different
parameters for different tracks can be set by providing multiple Apptainer
files.

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
Comming soon

## Organizers
 - [Daniel Fišer](https://danfis.cz) (Saarland University)
 - [Florian Pommerening](http://ai.cs.unibas.ch/people/pommeren/index.html) (University of Basel)

Contact us: [ipc2023-classical@googlegroups.com](ipc2023-classical@googlegroups.com)
