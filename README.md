# Benchmarking the Talking Owner's Manual (DeepTest Workshop Competition 26')
<p align="center">
  <img src="figures/deeptest-teaser.jpg" alt="Teaser" width="40%">
</p>

## Overview ##

The automotive domain increasingly adopts large language model (LLM)-based assistants to help drivers access information from vehicle **owner manuals** more efficiently [1,2]. For example, a driver may request instructions for enabling Adaptive Cruise Control (ACC). Many functions, such as for instance ACC, require specific environmental or driver-related preconditions, such as adequate sensor visibility in adverse weather to ensure safe operation. 

Manuals communicate these constraints through **warning statements**. An LLM-based assistant should therefore also provide such warnings if required. However, because LLMs may hallucinate, there is a risk that **essential warnings are omitted** or stated incorrectly. The objective of this competition is to find an automated way of stress-testing an LLM-based automotive assistant with respect to its reliability in **propagating accurate safety-related information** when necessary.

The competitors should propose an *automated* test generator that produces textual inputs (user requests) to test the information system.  The aim of the generation is to produce diverse failure-inducing tests, i.e., request that make the system ignore a warning in the response.An example of an executed (non-failing) test and system architecture is provided below.

The ranking of the tools is based on different metrics, including the number of **diverse warnings ignored** and the diversity of generated test inputs to support better root cause analysis. 

The generated user requests are evaluated on a public simplified RAG-based information system and on an **industrial research prototype** provided by [BMW Group](https://www.bmwgroup.com/).

<br><br>
![alt text](/figures/car-expert-usecase.png)

## Registration

To register for the competition, please send us your **Name**, **Affiliation & Address** to the following address: [lev.sorokin@tum.de](mailto:lev.sorokin@tum.de?subject=DeepTest%20Competition%20-%20Talking%20Manual). Use as email subject "DeepTest Competition - Talking Manual".

The registration is open until: *30-11-2025*.

Please note that the number of available spots is limited. Participants will receive a confirmation email along with further instructions and access to the competition code. Registration will be accepted on a first-come, first-served basis.

The competition is organized in the context of the DeepTest Workshop, co-located with the International Conference on Software Engineering (ICSE 2026). Participants will present their approach and results at the workshop, either in person or remotely.
Information about the workshop is available at: https://conf.researchr.org/home/icse-2026/deeptest-2026

## Implement Your Test Generator ##

We provide a code pipeline that will integrate your test generator with the system-under-test by validating, executing and evaluating your test cases. Moreover, we offer sample test generators to show how to use the code pipeline.
For the execution of the pipeline there is no GPU-based computation needed. Access to cloud-based LLMs will be granted.

Consider following constraints for the generated requests:

- Input should be based on english vocabulary.
- Input should be less then 20 words.

For the test generation you receive manual information and with an extracted list of warnings. 
You can inspect the manuals in the [data folder](data/) (upon registration).

Detailed installation instructions can be found in [INSTALLATION](documentation/INSTALLATION.md) (upon registration).
Guidelines for the competition are available in [GUIDELINES](documentation/GUIDELINES.md) (upon registration).

## Comparing the Test Generators ##

Deciding which test generator is the best is far from trivial and, currently, remains an open challenge. 
We use multiple metrics to rank the test generators. The first set of metrics which is available to participants is:

- (num diverse warnings) Number of diverse warnings ignored.
- (num warnings) Number of warnings ignored.
- (embedding diversity) Avg max embedding distance between generated requests.
- (time) Time to the first warning ignored.

The second metric is applied by the jurors and relies on clustering techniques to measure the diversity of failure-inducing test cases. The more clusters are covered the more diverse are the failure types.
As we expect that submitted tools are stochastic in nature, metrics are computed over several runs of the corresponding test generator.

We combine all metrics results into a single score to rank the results.

## License ##

The software we developed is distributed under MIT license. See the [LICENSE.md](LICENSE.md) file.

## Timeline

| Date        | Event                         |
|-------------|------------------------------|
| 30/11/2025  | Registration closes          |
| 31/12/2025  | Submission deadline          |
| 21/01/2026  | Results announcement         |
| 14/04/2026  | ICSE Presentation            |

## Organizers ##

Lev Sorokin  - BMW Group, TUM \
Ivan Vasilev - BMW Group, TUM \
Samuele Pasini - USI \
Matteo Biagiola - USI / University St Gallen \
Nargiz Humbatova - USI \
Kim Jinhan - USI

## Use Case Provider ##

<img src="figures/bmw-logo.png" alt="BMW Logo" style="width: 80%;" />

## References ## 

[1] [Generative AI, Augmented Reality and Teleoperated Parking – the Digital Experience in the BMW of the Future at the Consumer Electronics Show (CES) 2024](https://www.press.bmwgroup.com/global/article/detail/T0438824EN/generative-ai-augmented-reality-and-teleoperated-parking-%E2%80%93-the-digital-experience-in-the-bmw-of-the-future-at-the-consumer-electronics-show-ces-2024?language=en)

[2] Rony, M. R. A. H.; Süß, C.; Bhat, S. R.; Sudhi, V.; Schneider, J.; Vogel, M.; Teucher, R.; Friedl, K. E.; Sahoo, S. R. CarExpert: Leveraging Large Language Models for In-Car Conversational Question Answering. 2023. Fraunhofer Publica. DOI: 10.24406/publica-2245. Available at: https://publica.fraunhofer.de/handle/publica/457518

[3] Giebisch, R.; Friedl, K. E.; Sorokin, L.; Stocco, A. Automated Factual Benchmarking for In-Car Conversational Systems using Large Language Models. CoRR abs/2504.01248, 2025. Schloss Dagstuhl – Leibniz Center for Informatics. https://ieeexplore.ieee.org/document/11097480

