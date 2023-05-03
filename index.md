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
| Feature stop (final planner submission)       | March 24, 2023     |
| Planner Abstract submission deadline          | April 21, 2023     |
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

## Participants


### Optimal Track

* **SymBD** [(planner abstract)](TODOSymBD_2023_opt_optimal.pdf)  
  *Alvaro Torralba*  
  Symbolic Bidirectonal Blind Search

* **FTSPlan** [(planner abstract)](TODOfts_sbd_opt_optimal.pdf)  
  *Alvaro Torralba*  
  Optimal planner based on reformulation and search under the merge-and-shrink representation search. After reformulation uses symbolic bidirectional search

* **Hapori MIPlan Optimal All Data** [(planner abstract)](abstracts/planner19_hapori_mip2.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Sequential portfolio of optimal IPC planners computed with the MIP formulation by Nunez, Borrajo and Linares (2015).

* **Ragnarok** [(planner abstract)](abstracts/planner17_ragnarok.pdf)  
  *Dominik Drexler, Daniel Gnad, Paul Höft, Jendrik Seipp, David Speck, Simon Ståhlberg*  
  Sequential portfolio of optimal planners developed at Linköping University

* **Hapori Stone Soup Optimal** [(planner abstract)](abstracts/planner19_hapori_stonesoup.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Sequential portfolio of optimal IPC planners computed with the Stone Soup algorithm

* **FTSPlan** [(planner abstract)](TODOfts_ms_opt_optimal.pdf)  
  *Alvaro Torralba*  
  Optimal planner based on reformulation and search under the merge-and-shrink representation search. After reformulation uses A* with the merge-and-shink heuristic.

* **CEGAR++** [(planner abstract)](abstracts/planner34_cegarplusplus.pdf)  
  *Raphael Kreft, Silvan Sievers*  
  Pattern Databases for interesting patterns up to size 2, patterns computed with hill climbing and CEGAR, combined with domain abstractions and Cartesian abstractions computed with CEGAR in a maximum heuristic over SCP heuristics, generated through greedy computation of hybrid-optimized orders.

* **QDom-Lmcut** [(planner abstract)](TODOdom_opt_optimal.pdf)  
  *Alvaro Torralba*  
  Dominance Pruning

* **Hapori Explainable Planner Selection - Single Decision Tree Optimal** [(planner abstract)](abstracts/planner19_hapori_epsdt.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Planner selection portfolio as described in Explainable Planner Selection for Classical Planning (AAAI 2022) using Fawcetts et al (ICAPS 2014) PDDL features and linear regression.

* **Hapori Delfi Optimal** [(planner abstract)](abstracts/planner19_hapori_delfi.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Planner selection portfolio as described in Deep Learning for Cost-Optimal Planning: Task-Dependent Planner Selection (Sievers AAAI 2019)

* **Symk** [(planner abstract)](abstracts/planner3_symk.pdf)  
  *David Speck*  
  Symbolic bidirectional blind search

* **Hapori Greedy Optimal** [(planner abstract)](abstracts/planner19_hapori_greedy.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Sequential portfolio of optimal IPC planners computed with the greedy offline approximation algorithm by Streeter and Smith (UAI 2008).

* **DecAbStar** [(planner abstract)](abstracts/planner18_decabstar.pdf)  
  *Daniel Gnad, Silvan Sievers, Alvaro Torralba*  
  Optimal planner based on decoupled state-space search and abstraction heuristics.

* **Fast Downward Stone Soup 2023 Optimal** [(planner abstract)](abstracts/planner28_fdss_2023.pdf)  
  *Clemens Büchner, Remo Christen, Augusto Blaas Corrêa, Salomé Eriksson, Patrick Ferber, Jendrik Seipp, Silvan Sievers*  
  Portfolio of configurations from the main Fast Downward branch, scheduled with the Stone Soup algorithm.

* **DALAI 2023 Optimal** [(planner abstract)](abstracts/planner4_dalai.pdf)  
  *Clemens Büchner, Remo Christen, Salomé Eriksson, Thomas Keller*  
  Disjunctive Action Landmarks All In -- Path-dependent landmark heuristic search tailored to find optimal solutions.

* **DecStar-2023** [(planner abstract)](abstracts/planner15_decstar.pdf)  
  *Daniel Gnad, Alvaro Torralba, Alexander Shleyfman*  
  Optimal planner based on decoupled state-space search.

* **Odin** [(planner abstract)](abstracts/planner2_odin.pdf)  
  *Dominik Drexler, Jendrik Seipp, David Speck*  
  Transition cost partitioning over abstraction heuristics

* **Hapori Explainable Planner Selection - Linear Regression Optimal** [(planner abstract)](abstracts/planner19_hapori_epslr.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Planner selection portfolio as described in Explainable Planner Selection for Classical Planning (AAAI 2022) using Fawcetts et al (ICAPS 2014) PDDL features and linear regression.

* **Dofri** [(planner abstract)](abstracts/planner21_dofri.pdf)  
  *Paul Höft, David Speck, Jendrik Seipp*  
  forward search with A* and the Saturated Post-Hoc optimization heuristic that selectively reuses previous SPhO LP solutions.

* **Hapori IBaCop2 Sat** [(planner abstract)](abstracts/planner19_hapori_ibacop2.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Sequential portfolio of optimal IPC planners computed on an instance-based fashion. A set of 3 planners are pre-selected based on PDDL task and heuristic features.

* **Scorpion 2023** [(planner abstract)](abstracts/planner25_scorpion_2023.pdf)  
  *Jendrik Seipp*  
  Saturated cost partitioning over abstraction heuristics.

* **ComplementaryPDB** [(planner abstract)](abstracts/planner7_TODO.pdf)  
  *Santiago Franco, Stefan Edelkamp, Ionut Moraru*  
  Modified version of complementary heuristic, where we are using completely new bin packing algorithms(paper pending), in situ learning of all the algorithm parameters critical to the pattern selection performance (previously only which pattern generation algorithm we use). Also we have added a new pattern generator inspired on how Gamer chooses a single PDB which it keeps improving. Also the selection algorithm is based on size of search space (previously selection criteria was time). Some features from previous complementary heuristic as in the iJCAI 18 paper are yet to be adapted to this version, e.g. mutation for local search of succesful selection, stratified sampling.


### Satisficing Track

* **Hapori Explainable Planner Selection - Single Decision Tree Satisficing** [(planner abstract)](abstracts/planner19_hapori_epsdt.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Planner selection portfolio as described in Explainable Planner Selection for Classical Planning (AAAI 2022) using Fawcetts et al (ICAPS 2014) PDDL features and linear regression.

* **TFTM2** [(planner abstract)](abstracts/planner22_tftm_co1.pdf)  
  *Alex Tuisov, Michael Katz*  
  Planner based on the IJCAI 2021 paper The Fewer the Merrier: [Pruning Preferred Operators with Novelty](https://www.ijcai.org/proceedings/2021/0576.pdf).

* **Spock** [(planner abstract)](abstracts/planner1_spock.pdf)  
  *Jendrik Seipp, Mauricio Salerno, Raquel Fuentetaja*  
  FDSS 2018 with action elimination. Removes redundant actions from each found plan to -potentially- rapidly find a cheaper plan.

* **Powerlifted Satisficing** [(planner abstract)](abstracts/planner8_powerlifted.pdf)  
  *Augusto B. Corrêa, Guillem Francès, Markus Hecher, Davide Mario Longo, Jendrik Seipp*  
  Powerlifted planner using a sequential portfolio configuration

* **DiSCO** [(planner abstract)](abstracts/planner16_disco.pdf)  
  *Maximilian Fickert, Daniel Gnad*  
  Satisficing planner based on Decoupled Search and COnjunctions.

* **OpCount4Sat - Satistificng** [(planner abstract)](abstracts/planner10_opcount4sat.pdf)  
  *Daniel Matheus Doebber, André Grahl Pereira, Augusto B. Corrêa*  
  Operator Counting Heuristics for Satisficing Planning

* **Hapori Delfi Satisficing** [(planner abstract)](abstracts/planner19_hapori_delfi.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Planner selection portfolio as described in Deep Learning for Cost-Optimal Planning: Task-Dependent Planner Selection (Sievers AAAI 2019)

* **Hapori MIPlan All Data Sat** [(planner abstract)](abstracts/planner19_hapori_mip2.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Sequential portfolio of optimal and satisficing IPC planners computed with the MIP formulation by Nunez, Borrajo and Linares (2015).

* **Hapori Greedy Satisficing** [(planner abstract)](abstracts/planner19_hapori_greedy.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Sequential portfolio of satisficing IPC planners computed with the greedy offline approximation algorithm by Streeter and Smith (UAI 2008).

* **DALAI 2023 Satisficing** [(planner abstract)](abstracts/planner4_dalai.pdf)  
  *Clemens Büchner, Remo Christen, Salomé Eriksson, Thomas Keller*  
  Disjunctive Action Landmarks All In -- Path-dependent landmark heuristic search tailored to find some solution fast and improve improve it iteratively.

* **Scorpion Maidu Satisficing** [(planner abstract)](abstracts/planner8_maidu.pdf)  
  *Augusto B. Corrêa, Guillem Francès, Markus Hecher, Davide Mario Longo, Jendrik Seipp*  
  Version of the Scorpion planner using width-search algorithms

* **Cerberus** [(planner abstract)](abstracts/planner23_cerberus.pdf)  
  *Michael Katz*  
  Planner Cerberus from IPC 2018

* **Approximate Novelty Anytime** [(planner abstract)](abstracts/planner29_ApxNoveltyFD.pdf)  
  *Anubhav Singh, Nir Lipovetzky, Miquel Ramirez, Javier Segovia-Aguas*  
  The anytime configuration of the planner. It uses ApxNovelty search to find the first satisficing plan. After which, it switches to lazy wastar with a upper bound on the plan cost, and continues to optimize the solutions until timeout.

* **Hapori Stone Soup Satisficing** [(planner abstract)](abstracts/planner19_hapori_stonesoup.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Sequential portfolio of satisficing IPC planners computed with the Stone Soup algorithm

* **DecStar-2023** [(planner abstract)](abstracts/planner15_decstar.pdf)  
  *Daniel Gnad, Alvaro Torralba, Alexander Shleyfman*  
  Satisficing planner based on decoupled state-space search.

* **FSM** [(planner abstract)](abstracts/planner20_FSM.pdf)  
  *Gustavo Prolla Lacroix, Rafael Vales Bettker, André Grahl Pereira*  
  A learning-based planner for short-time sampling, training, and testing.

* **Forward Backward Anytime Novelty Search** [(planner abstract)](abstracts/planner30_NoveltyFB.pdf)  
  *Anubhav Singh, Chao Lie, Nir Lipovetzky, Miquel Ramirez, Javier Segovia-Aguas*  
  The anytime configuration of the planner. It uses Forward Backward Novelty Search search to find the first satisficing plan. After which, it switches to lazy wastar with a upper bound on the plan cost, and continues to optimize the solutions until timeout.

* **Fast Downward Stone Soup 2023 Satisficing** [(planner abstract)](abstracts/planner28_fdss_2023.pdf)  
  *Clemens Büchner, Remo Christen, Augusto Blaas Corrêa, Salomé Eriksson, Patrick Ferber, Jendrik Seipp, Silvan Sievers*  
  Portfolio of configurations from the main Fast Downward branch, scheduled with the Stone Soup algorithm.

* **TFTM1** [(planner abstract)](abstracts/planner22_tftm_argmax.pdf)  
  *Alex Tuisov, Michael Katz*  
  Planner based on the IJCAI 2021 paper The Fewer the Merrier: [Pruning Preferred Operators with Novelty](https://www.ijcai.org/proceedings/2021/0576.pdf).

* **Hapori Explainable Planner Selection - Linear Regression Satisficing** [(planner abstract)](abstracts/planner19_hapori_epslr.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Planner selection portfolio as described in Explainable Planner Selection for Classical Planning (AAAI 2022) using Fawcetts et al (ICAPS 2014) PDDL features and linear regression.

* **Hapori IBaCop2 Sat** [(planner abstract)](abstracts/planner19_hapori_ibacop2.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Sequential portfolio of satisficing IPC planners computed on an instance-based fashion. A set of 5 planners are pre-selected based on PDDL task and heuristic features.

* **Levitron Satisficing** [(planner abstract)](abstracts/planner8_levitron.pdf)  
  *Augusto B. Corrêa, Guillem Francès, Markus Hecher, Davide Mario Longo, Jendrik Seipp*  
  Hybrid planner using both the grounded planner Scorpion Maidu and the lifted planner Powerlifted


### Agile Track

* **OpCount4Sat - Agile** [(planner abstract)](abstracts/planner10_opcount4sat.pdf)  
  *Daniel Matheus Doebber, André Grahl Pereira, Augusto B. Corrêa*  
  Operator Counting Heuristics for Satisficing Planning

* **Hapori Explainable Planner Selection - Single Decision Tree Agile** [(planner abstract)](abstracts/planner19_hapori_epsdt.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Planner selection portfolio as described in Explainable Planner Selection for Classical Planning (AAAI 2022) using Fawcetts et al (ICAPS 2014) PDDL features and linear regression.

* **Hapori Stone Soup Agile** [(planner abstract)](abstracts/planner19_hapori_stonesoup.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Sequential portfolio of satisficing IPC planners computed with the Stone Soup algorithm

* **Forward Backward Novelty Search** [(planner abstract)](abstracts/planner30_NoveltyFB.pdf)  
  *Anubhav Singh, Chao Lie, Nir Lipovetzky, Miquel Ramirez, Javier Segovia-Aguas*  
  Forward Backward Approximate BFWS with novelty approximation and goal count heuristics, f=<#w,#g>, see ICAPS 2021 papers on Approximate Novelty Search and Width-based backward search

* **DiSCO** [(planner abstract)](abstracts/planner16_disco.pdf)  
  *Maximilian Fickert, Daniel Gnad*  
  Agile planner based on Decoupled Search and COnjunctions.

* **Hapori Delfi Agile** [(planner abstract)](abstracts/planner19_hapori_delfi.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Planner selection portfolio as described in Deep Learning for Cost-Optimal Planning: Task-Dependent Planner Selection (Sievers AAAI 2019)

* **Levitron Agile** [(planner abstract)](abstracts/planner8_levitron.pdf)  
  *Augusto B. Corrêa, Guillem Francès, Markus Hecher, Davide Mario Longo, Jendrik Seipp*  
  Hybrid planner using both the grounded planner Scorpion Maidu and the lifted planner Powerlifted

* **DALAI 2023 Agile** [(planner abstract)](abstracts/planner4_dalai.pdf)  
  *Clemens Büchner, Remo Christen, Salomé Eriksson, Thomas Keller*  
  Disjunctive Action Landmarks All In -- Path-dependent landmark heuristic search tailored to find solutions fast.

* **Grounding Schematic Representation with GRINGO for Width-based Search** [(planner abstract)](abstracts/planner29_ApxNoveltyTarski.pdf)  
  *Anubhav Singh, Nir Lipovetzky, Miquel Ramirez, Javier Segovia-Aguas, Guillem Francès*  
  Approximate Best First Width Search with novelty approximation and goal count heuristics, f=<#w,#g>, the planner leverages Tarski to ground the schematic representation of the planning problem, refer https://tarski.readthedocs.io/en/latest/notebooks/grounding-reachability-analysis.html

* **Hapori Explainable Planner Selection - Linear Regression Agile** [(planner abstract)](abstracts/planner19_hapori_epslr.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Planner selection portfolio as described in Explainable Planner Selection for Classical Planning (AAAI 2022) using Fawcetts et al (ICAPS 2014) PDDL features and linear regression.

* **Scorpion Maidu Agile** [(planner abstract)](abstracts/planner8_maidu.pdf)  
  *Augusto B. Corrêa, Guillem Francès, Markus Hecher, Davide Mario Longo, Jendrik Seipp*  
  Version of the Scorpion planner using width-search algorithms

* **TFTM1** [(planner abstract)](abstracts/planner22_tftm_argmax.pdf)  
  *Alex Tuisov, Michael Katz*  
  Planner based on the IJCAI 2021 paper The Fewer the Merrier: [Pruning Preferred Operators with Novelty](https://www.ijcai.org/proceedings/2021/0576.pdf).

* **Hapori Greedy Agile** [(planner abstract)](abstracts/planner19_hapori_greedy.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Sequential portfolio of satisficing IPC planners computed with the greedy offline approximation algorithm by Streeter and Smith (UAI 2008).

* **FTSPlan** [(planner abstract)](TODOfts_ff_agl_agile.pdf)  
  *Alvaro Torralba*  
  Optimal planner based on reformulation and search under the merge-and-shrink representation search. After reformulation uses Greedy Best First Search with the FF heuristic.

* **Approximate Novelty** [(planner abstract)](abstracts/planner29_ApxNoveltyFD.pdf)  
  *Anubhav Singh, Nir Lipovetzky, Miquel Ramirez, Javier Segovia-Aguas*  
  Approximate Best First Width Search with novelty approximation and goal count heuristics, f=<#w,#g>, leverages Fast Downward to ground the schematic representation of the planning problem

* **Hapori MIPlan All Data Random Order Agl** [(planner abstract)](abstracts/planner19_hapori_mip2.pdf)  
  *Patrick Ferber, Michael Katz, Jendrik Seipp, Silvan Sievers, Daniel Borrajo, Isabel Cenamor, Tomas de la Rosa, Fernando Fernandez-Rebollo, Carlos Linares, Sergio Nunez, Alberto Pozanco, Horst Samulowitz, Shirin Sohrabi*  
  Sequential portfolio of satisficing and agile IPC planners computed with the MIP formulation by Nunez, Borrajo and Linares (2015).

* **DecStar-2023** [(planner abstract)](abstracts/planner15_decstar.pdf)  
  *Daniel Gnad, Alvaro Torralba, Alexander Shleyfman*  
  Agile planner based on decoupled state-space search.

* **Fast Downward Stone Soup 2023 Agile** [(planner abstract)](abstracts/planner28_fdss_2023.pdf)  
  *Clemens Büchner, Remo Christen, Augusto Blaas Corrêa, Salomé Eriksson, Patrick Ferber, Jendrik Seipp, Silvan Sievers*  
  Portfolio of configurations from the main Fast Downward branch, scheduled with the Stone Soup algorithm.

* **TFTM2** [(planner abstract)](abstracts/planner22_tftm_co1.pdf)  
  *Alex Tuisov, Michael Katz*  
  Planner based on the IJCAI 2021 paper The Fewer the Merrier: [Pruning Preferred Operators with Novelty](https://www.ijcai.org/proceedings/2021/0576.pdf).

* **FSM** [(planner abstract)](abstracts/planner20_FSM.pdf)  
  *Gustavo Prolla Lacroix, Rafael Vales Bettker, André Grahl Pereira*  
  A learning-based planner for short-time sampling, training, and testing.

* **Cerberus** [(planner abstract)](abstracts/planner23_cerberus.pdf)  
  *Michael Katz*  
  Planner Cerberus from IPC 2018

* **Powerlifted Agile** [(planner abstract)](abstracts/planner8_powerlifted.pdf)  
  *Augusto B. Corrêa, Guillem Francès, Markus Hecher, Davide Mario Longo, Jendrik Seipp*  
  Powerlifted planner using a sequential portfolio configuration



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

We got many registrations and in particular many registrations with
multiple submissions in a team. To keep the computation time manageable, we
ask that you limit your submissions to one variant per planner. If two of
your submissions are substantially different ideas, it is of course fine to
submit both. As a guideline, if two submissions would be described with two
planner abstracts, then they are two submissions. If you would describe them
in one planner abstract with a short paragraph describing the differences
between them, they are variants of the same planner.

After some discussions, we decided to allow multiple variants of the same
planner if you think they are likely end up on very different spots in
scoring (i.e., not next to each other).
In that case, you should still
write two planner abstracts, but one may discuss the difference to the
other submission. In that case, we ask you to write a paragraph into the
second planner abstract that discusses your reasons of why you think
this should be a separate submission, i.e., why you think these two
submissions will not end up next to each other in the scoring. In the
post-IPC analysis, we then ask you to evaluate this reasoning: if the
planners indeed ended up in very different spots, what made the
difference? If they ended up next to each other, why did this happen?
Moreover, if the leaderboard ends up with multiple variants of the same
planner in the first places, we reserve the right to merge these entries.
New variants can be submitted until April 16 via pull requests.



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
