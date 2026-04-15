---
Title:          openEuler Community AI-Assisted Code Contribution Guidelines
Type:           Document
Abstract:       Guidelines for disclosure, compliance, and quality when submitting AI-assisted code in the openEuler community
Author:         Jianmin Wang (hi at jimmie.me)
Status:         Initial
No:             oEEP-0025
Create_time:    2026-02-02
Update_time:    2026-02-04
---

## Translation Note

This is a translation of the Chinese document `oEEP-0025 openEuler社区AI辅助代码提交规范.md`. In case of any inconsistency, the Chinese version prevails.

## Background / Goals / Principles

AI programming tools are rapidly adopted in the community, improving efficiency but bringing risks such as unclear provenance, license ambiguity, potential misuse of confidential information, security flaws, and increased review costs. To preserve trust, sustainable collaboration, and compliance, the community needs a minimal disclosure and accountability, with actionable review guidance.

Goals:

- Define the scope, responsibilities, and minimum compliance requirements for AI-assisted contributions.
- Establish a reviewable and traceable disclosure and self-check mechanism.
- Protect community members and contributors by reducing security and copyright risks.

Principles:

- Transparency: AI involvement should be understandable to reviewers.
- Accountability: the responsible parties are natural persons, not the tools.
- Compliance first: follow license, privacy, and security requirements.
- Minimal necessary: disclose only what is needed for review and avoid exposing sensitive information.
- Assistive role only: AI may assist submission and review but cannot replace human judgment.

## Terminology

- AI-assisted code: code, configurations, documents, or tests generated or modified based on AI suggestions.
- Critical change: changes affecting behavior, security boundaries, license statements, API compatibility, performance, or maintainability.
- Disclosure: describing AI involvement and necessary context in submission information (PR description or commit message).

## Scope / Stakeholders / Responsibilities

### Scope

- Applies to contributions of code, build scripts, spec files, configs, tests, and documentation in openEuler.
- Also applies to external patch ports or third-party code imports when AI is involved.

### Responsibilities

- Contributors: responsible for correctness, compliance, and security, and must follow community rules.
- Reviewers: review based on disclosures; may use AI for analysis, but AI must not be the sole or final decision-maker.

## Requirements

### 1. Disclosure

- For AI-assisted changes that are critical, disclosure is required in the submission information. If changes affect behavior, security boundaries, license statements, API compatibility, performance, or maintainability, they are considered critical changes.
- When there is reasonable doubt as to whether a change is critical, disclosure is recommended.
- To aid review and transparency, it is recommended to disclose the following in the submission information:
  - The scope and degree of AI involvement (e.g., main code generation, functional rewrite, test optimization, document translation).
  - When known or reasonably obtainable, provide tool and model name and version.
  - Whether human verification was performed.
- The community does not require full prompts, chat logs, or model interaction transcripts unless voluntarily provided and non-sensitive.
- Disclosure is not required for spelling fixes, mechanical formatting, or trivial autocomplete with no behavioral or logic changes.

Recommended disclosure template:

- AI usage: yes/no
- Scope: generation/rewrite/optimization/translation
- Tool, model, and version:
- Human verification: done/planned (brief notes)

### 2. Compliance and Licensing

- Contributors must, to the best of their knowledge, ensure that AI-generated content they submit does not include material that they know infringes any third-party copyright.
- Contributors must ensure that they have the legal right to submit the AI-generated content and to contribute, sublicense, and distribute such content under the project’s license.
- Contributors must ensure that the terms of use of the AI tools they use do not restrict them from contributing, sublicensing, or distributing the generated content under the project’s license.
- If contributors know or reasonably should know that the submitted content contains code fragments with identifiable origins, or is substantially similar to existing open source projects in structure, naming, comments, or implementation logic, they must clearly disclose the source and comply with the applicable license.
- Project maintainers reserve the right to request source disclosure, require modifications, or reject submissions that include AI-generated content.

### 3. Security and Quality

- Critical changes require minimal viable tests or verification notes.
- Contributors must understand and explain the submitted logic; contributions justified only by “the AI generated it” may be rejected.
- Reviewers may request additional test evidence, split submissions, or alternative implementations.

### 4. Accountability and Traceability

- All AI-generated content is treated as the contributor's contribution; the contributor bears responsibility.
- Reviewers may reject or request changes for insufficient disclosure, unclear risk, or poor quality.
- Contributors who cannot explain changes or repeatedly submit low-quality content may be handled under community rules.

## Submission and Review Process (Recommended)

1. Pre-submit self-check
   - Confirm AI usage scope, source, and licensing
   - Run necessary tests or static checks
2. Disclosure at submission
   - If disclosure is required, include `Assisted-by: <tool>` or `Generated-by: <tool>` in the submission information
   - Provide AI usage details based on the recommended disclosure template as needed
3. Review stage
   - Reviewers perform focused review based on disclosure
   - Require additional tests, split changes, or alternative implementations when needed
   - Reviewer checklist (optional)
      - Is disclosure complete and clear?
      - Can the contributor explain critical logic?
      - Are there obvious license or security risks?
      - Do tests/verification cover critical paths?
4. Post-merge follow-up
   - Handle issues via normal processes and reassess AI usage risks

## Examples

Example 1 (disclosure required):

- AI was used to generate a new scheduling algorithm, altering core logic
- Manually verified and added unit tests

Example 2 (disclosure not required):

- AI helped fix spelling errors and improve phrasing in documentation

Example 3 (disclosure recommended):

- AI was used to optimize an existing function, without interface changes but with logic adjustments

## References

- [Fedora Council Policy: AI-Assisted Contributions](https://docs.fedoraproject.org/en-US/council/policy/ai-contribution-policy/)
- [Apache Software Foundation: Generative Tooling Guidance](https://www.apache.org/legal/generative-tooling.html)
- [Linux Foundation: Generative AI Policy](https://www.linuxfoundation.org/legal/generative-ai)
- [Drupal: Proposed guidelines for AI contribution](https://www.drupal.org/project/governance/issues/3565917)
- [DigitalOcean: Contributing AI-Generated Code with Care](https://www.digitalocean.com/community/tutorials/ai-coding-tools-open-source)
- [GNOME Shell Extensions Review Guidelines](https://gjs.guide/extensions/review-guidelines/review-guidelines.html)
- [Code provenance - QEMU documentation](https://www.qemu.org/docs/master/devel/code-provenance.html)
- [NetBSD Commit Guidelines](https://www.netbsd.org/developers/commit-guidelines.html)
