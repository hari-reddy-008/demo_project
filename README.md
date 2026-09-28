# Capstone Evidence Pack

The evidence which was gathered during the process of reproducing and testing the three reference systems is contained in this folder.

## Submission Structure

The package includes a number of folders containing the evidence for each of the three systems, along with the environment notes, the perturbation log, and the final reflection brief.

## System 1 — Validated, Routed Insurance Policy Extraction

The evidence consists of the entire test suite, the results of the type-checking and linting, the routing tests, the calibration evidence, a specific routing trace which has been reviewed by a human, and a deliberate perturbation involving the absence of a source.

The test suite as a whole resulted in 45 tests passing and 3 being skipped; the ones that were skipped were the live Anthropic API tests since there was no ANTHROPIC_API_KEY available.

All nine routing tests were passed in the offline routing test process, and the live API pipeline was not run without credentials, nor was any live API-generated routing artifact created.

The deliberate disturbance caused the Endorsements / Schedule A source block to be removed from the copied policy fixture, after which the controlled offline extraction regarded the required field as missing_source and raised the issue without making any further API call.

## System 2 — Resilient Mortgage Document Extraction

The evidence consists of the entire test suite, the results of the static-analysis, the captures from offline replays, and a purposeful perturbation of the validator.

The entire test suite resulted in 25 cases passing.

The replay shows a failure to display the appraisal, the unavailable bonus information, and a discrepancy in the monthly income figure. The case involving the discrepancy illustrates the explicit identification of an inconsistency rather than merely accepting the given total.

The intentional disturbance caused the stated monthly income figure to change from 10892.17 to 9642.17 without altering any of the income components; the baseline showed a discrepancy but the result from the perturbed validator was in agreement with there being no discrepancies.

## System 3 — Supply Chain Risk Investigation

The evidence consists of the entire test suite, the static-analysis results, an offline investigation into Meridian, and a simulation of a logistics-timeout scenario.

The entire test suite resulted in 34 cases passing.

The compilation carried out using `mypy --python-version 3.13 supply_chain_risk/` was successful and found no problems in the eight source files.

The evidence from the investigation keeps track of the original source and identifies findings as either corroborated, based on a single source, contested, or incomplete. The result obtained after the timeout period indicates that the investigation carries on by recording the unavailable logistics source as an incomplete coverage area.

## Perturbation Evidence

One deliberate perturbation was performed for each system:

- In the policy pipeline, the Endorsements/Schedule A source block was removed from a copied policy fixture.
- For the mortgage extraction, the total stated monthly income was altered to agree with the deterministically calculated total.
- Supply chain: simulated a timeout in the logistics source.

The observations together with the baseline comparisons are recorded in the system-specific evidence files and in the file called 'perturbation-log.md'.

## Reflection

The file `reflection-brief.md` gives the final reflection and relates the observations made to the evidence collected during the execution.

The results that are reported here are based on the actual executions included in this pack and not on any live API results which were unavailable.
