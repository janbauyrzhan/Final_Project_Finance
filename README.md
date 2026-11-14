Educational project for the course Introduction to Finance. Not a real product, service or investment offer. Do not use with real funds.

# AgriChain Final Project

Team 02, group SE-2517. This is the Final Project continuation of the team's AgriChain Endterm concept: traceability of synthetic grain and oilseed batches. The team adds the final report, investor presentation, local blockchain prototype and course requirements in separate commits from the respective members' accounts.

Repository: https://github.com/janbauyrzhan/Final_Project_Finance

## Initial upload status

This first commit contains README.md, CONTRIBUTIONS.md and LICENSE. The other team members add the remaining materials from their own accounts. The material links below become available as those files are uploaded.

## Submission materials

- [Final report PDF](deliverables/Team02_FP_Report.pdf): 15 pages from Introduction to Conclusion, plus references and Appendices A–E.
- [PowerPoint presentation](deliverables/Team02_FP_Presentation.pptx): 14 main slides and 3 backup slides, with speaker notes and editable tables, charts and a sequence diagram.
- [Individual self-evaluation template](deliverables/Team02_FP_SelfEval_TEMPLATE.pdf): each student must enter their own actual contribution.
- [Presentation speaking notes and finance questions](deliverables/Team02_Defense_Notes.txt).
- [Separate scripts for the four team members](deliverables/scripts_for_four).
- [Course requirements](requirements/Final_Project_Requirements.docx).
- [Instructor's BlockSupply example](requirements/Final_Project_Example_BlockSupply.docx): a separate course reference, not our startup or financial model.
- [Submission checklist](SUBMISSION_CHECKLIST.md).


## Demonstration video

The video is shared separately and is intentionally excluded from this repository and its download archives, as requested by the team. Its public viewing link still needs to be inserted on the report title page, title slide and in this README before Moodle submission.

Video link: **pending separate upload**.

The locally prepared demonstration is 1 minute 58 seconds long and shows actual local compilation, deployment, the core workflow and all 15 tests passing, with explanatory captions. The course permits voice-over or captions and requires one team video of up to 3 minutes.

## Install and run the local prototype

Install Node.js and npm, then run in this repository:

```text
npm ci
npm test
npm run demo
```

On Windows, `RUN_TESTS.cmd` and `RUN_DEMO.cmd` provide the test and demonstration commands. The first run installs the locked dependencies when needed. Solidity 0.8.24 is pinned as an npm dependency, so compilation uses the local compiler after installation.

For a persistent local node, run `npm run node` in one terminal, then `npm run deploy:local` or `npm run demo:local` in another. The configured networks are local Hardhat and localhost, chain ID 31337.

## Implemented workflow and evidence

The custodian registers G001 with 100,000 kg of synthetic wheat and attaches a document fingerprint. A sender dispatches it and a different receiver confirms receipt. A mismatched split is rejected. A valid split creates G001A and G001B with 50,000 kg each. A reviewer flags and resolves an issue. An unrelated account cannot register a batch.

- [Contract](contracts/AgriChainRegistry.sol)
- [Core tests](test/AgriChainRegistry.test.js)
- [Additional validation tests](test/Validation.test.js)
- [Automatic demonstration](scripts/demo.js)
- [Actual test output](evidence/test-results.txt)
- [Actual demo output](evidence/demo-results.txt)
- [Recorded demonstration events](evidence/demo-events.json)

The verified run on November 14, 2026 passed all 15 unit tests. All test data and accounts are synthetic. No tokens, payments, real funds, private keys or personal data appear in the prototype.

## Financial model

`python finance_model.py` uses Python's standard library to reproduce the annual and monthly scenarios. Monetary amounts are KZT million. The base case has three-year NPV **-36.75m** at 25%, with no payback within three operating years. A monthly liquidity check raises the original annual-only funding floor from **53.40m** to **55.5878m**, rounded upward to a **55.59m** classroom ask for 20% hypothetical equity. The two downside monthly funding floors are **76.51m** and **64.32m**. Inputs remain educational assumptions, not customer observations or supplier quotations.

## Boundaries

Hardhat is a local EVM demonstration. The conceptual Hyperledger Fabric consortium has not been deployed; porting Solidity logic to Fabric would require a new implementation and tests. Fingerprints can reveal a later file mismatch but do not certify source-document truth or physical grain quality. Role revocation, organisation-level ownership restrictions, confidential reads, multisignature administration and production recovery are absent. An issue flag does not automatically pause business actions. No independent security audit has occurred.

## Team contributions and AI disclosure

Responsibility areas follow the supplied team draft in [CONTRIBUTIONS.md](CONTRIBUTIONS.md). Every student must confirm actual work and make genuine commits from their own GitHub account. This upload does not fabricate a four-person commit history or contribution percentages.

OpenAI ChatGPT and Codex (GPT-6) assisted with text revisions, verification of the supplied financial model, the monthly liquidity extension, routine test and demonstration code, presentation preparation and supporting materials. Each student must independently review and explain the adopted design, assumptions, calculations and conclusions. See [AI disclosure](AI_DISCLOSURE.md).

## Licence

The supplied educational contract retains its [MIT licence](LICENSE). No OpenZeppelin contract implementation is copied. Hardhat, its plugins and other dependencies retain their own licences and notices. The instructor's files in `requirements/` remain attributed course reference materials and are not presented as original Team 02 work.
