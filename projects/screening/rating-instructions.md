# Rating Instructions for Scopus Records

You are rating Scopus records for a PhD literature review on virtual commissioning (VC). Work only from the title, author keywords and abstract in the input file. Do not search the web and do not use outside knowledge about the papers. When the abstract does not cover a question, leave that rating empty.

OUTPUT: a JSON list with exactly one object per input record, in the same order, with the keys
`id, rq1, rq2, rq3, t1, t3, t4, t5, t6, note, relevance, screen, screen_reason`.

## THE EIGHT QUESTIONS

- **rq1 Time saved:** How much commissioning time does VC save, in which phase (design, FAT, SAT, on-site commissioning), and does the saving outweigh the effort of building the model? (Includes reported time or cost savings, ramp-up reduction, modelling effort, cost-benefit.)
- **rq2 Faults:** Which faults are tested in VC (fault injection, abnormal situations, error handling, disturbances), and does this reduce faults at FAT, SAT or in operation? (Includes reliability of control software, detected errors and bugs.)
- **rq3 Fidelity:** How is the fidelity of VC models quantified (metric, physical reference, accuracy against the real system), and how is adequacy for a test argued (level of detail, fit for purpose, validity)?
- **t1 Use and validated scope:** What is VC or the digital twin used for (purposes, life-cycle phases, digital model/shadow/twin level), and which behaviour does it validate (logic, kinematics, dynamics, timing) depending on how the controller is represented?
- **t3 Model availability:** When in the delivery of a machine is the VC model available; practices for developing the model alongside the machine and keeping them aligned (including automatic model generation from engineering data).
- **t4 Co-simulation:** How are several simulators or emulators coupled (FMI/FMU, co-simulation, OPC UA coupling, synchronisation, which component owns the clock), and is reproducibility of runs ensured?
- **t5 X-in-the-loop:** Which configuration (MiL, SiL, HiL, virtual or emulated PLC versus real PLC, virtual robot controller) is used, which tests go with which, and what does real hardware reveal that emulation does not?
- **t6 Reconfigurability:** Is the twin built modular, component-based or generated so it can be adapted as the machine changes, and what effort is reported for adapting it?

## RATING SCALE (exactly these strings)

- `"Yes"` = addresses the question directly and reports an answer (a method with results, or measured data).
- `"Partly"` = addresses part of the question, or states the answer as a claim without data.
- `"Mentions"` = the topic is named but not worked on.
- `""` = not covered.

Be strict with "Yes": a claim like "VC reduces commissioning time" without numbers is "Partly". Most records will have several empty ratings.

## OTHER FIELDS

- **note:** one sentence, at most 30 words, in your own words (do not copy the abstract), saying what the paper reports that is relevant to the questions. If nothing is relevant, say in a few words what the paper is about.
- **relevance:** "High" (directly informs rq1, rq2 or rq3 with a method or data), "Medium" (relevant to one of the eight questions, or useful background) or "Low" (VC only in passing, or off-topic).
- **screen:** the suggested abstract-stage (S2) decision, "Include", "Maybe" or "Exclude". Be inclusive when in doubt: use "Maybe" rather than "Exclude" when unsure.
  - **Include** when all of these hold: (1) a peer-reviewed journal article, conference paper or book chapter; (2) English; (3) the subject is a simulation, emulation or twin of a discrete manufacturing or machine-building system (production lines, cells, robots, PLC-controlled equipment), with adjacent domains only where the commissioning problem transfers; (4) it reports an architecture, a method or an implementation, not a vision, roadmap or editorial.
  - **Exclude:** digital twins of humans, cities, buildings as buildings, energy grids, vehicles in operation, or product life cycles without a production system; pure machine-learning papers where the twin is a surrogate with no physical system in the loop; papers where simulation is only a data source for optimisation, with no commissioning or validation question; editorials, extended abstracts and posters. Building and HVAC "commissioning" papers are Exclude. Mark secondary studies (reviews, surveys) "Exclude" with screen_reason "Secondary study: harvest references".
- **screen_reason:** a few words naming the criterion that decided it (for example "Discrete manufacturing VC method", "Building energy commissioning", "Secondary study: harvest references", "Education/training only").
