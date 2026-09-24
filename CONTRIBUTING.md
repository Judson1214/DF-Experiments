# Contributing to DF-Experiments

Thank you for your interest in contributing to the **Digital Forensics Laboratory (DF-Experiments)** repository! We welcome contributions from students, researchers, educators, and forensic analysts aiming to expand our laboratory manual, improve explanations, or update tool procedures.

---

## 📋 Table of Contents
- [Code of Conduct](#code-of-conduct)
- [How to Contribute](#how-to-contribute)
  - [Reporting Bugs or Suggesting Improvements](#reporting-bugs-or-suggesting-improvements)
  - [Updating Existing Lab Manuals](#updating-existing-lab-manuals)
  - [Adding New Forensic Experiments](#adding-new-forensic-experiments)
- [Documentation & Markdown Guidelines](#documentation--markdown-guidelines)
- [Evidence & Screenshot Standards](#evidence--screenshot-standards)
- [Pull Request Process](#pull-request-process)

---

## Code of Conduct
This repository follows standard academic and open-source ethics. All interactions and contributions must remain professional, respectful, and strictly aligned with **authorized educational cybersecurity research**.

---

## How to Contribute

### Reporting Bugs or Suggesting Improvements
- Search existing [GitHub Issues](https://github.com/Judson1214/DF-Experiments/issues) to ensure the topic hasn't already been discussed.
- Open a new issue with a clear description, reproduction steps, or suggested enhancements.

### Updating Existing Lab Manuals
If a tool command syntax changes (e.g., in a new version of Volatility 3 or Ghidra):
1. Fork this repository.
2. Create a topic branch: `git checkout -b fix/exp-tool-update`.
3. Modify the corresponding `Experiment-X/README.md`.
4. Ensure all links and image references remain intact.
5. Submit a Pull Request with a clear description of the version changes.

### Adding New Forensic Experiments
If you are contributing an additional laboratory module:
1. Create a dedicated folder: `Experiment-XX/` (e.g., `Experiment-11/`).
2. Include an `images/` directory storing compressed, high-resolution `.png` or `.jpeg` screenshots.
3. Structure `README.md` following our standard template:
   - Header & Badges
   - Navigation links
   - 1. Aim / Objective
   - 2. Software & Tools Required (with platform and versions)
   - 3. Theoretical Background & Forensic Concepts
   - 4. Step-by-Step Procedure (with annotated screenshots)
   - 5. Observations & Forensic Findings
   - 6. Academic Assessment Rubrics
   - 7. Verified Result / Conclusion
4. Update the root `README.md` master syllabus table.

---

## Documentation & Markdown Guidelines
- Write in standard **GitHub Flavored Markdown (GFM)**.
- Use explicit language specifiers for all code blocks (e.g., `bash`, `cmd`, `text`, `python`).
- Structure tables cleanly using aligned pipes (`|`).
- Use relative links for repository assets (e.g., `./images/image1.png`).

---

## Evidence & Screenshot Standards
- **Resolution:** Crisp, readable screenshots showing relevant window panes and command outputs.
- **Redaction:** Redact personally identifiable information (PII), proprietary credentials, or sensitive institutional IP addresses.
- **File Names:** Use descriptive lowercase names or sequential numbers (e.g., `image1.png`, `image2.png`).

---

## Pull Request Process
1. Commit your changes with descriptive commit messages following conventional commits (e.g., `docs(exp-06): update tsk command syntax`).
2. Push your branch to your fork.
3. Open a Pull Request pointing to `main`.
4. Respond to review comments if requested.
