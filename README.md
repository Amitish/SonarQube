# 🚀 Application CI Pipeline – SonarQube Integration

This repository demonstrates **end-to-end SonarQube integration** with an **Azure DevOps (ADO) Application CI pipeline** to enforce **code quality, security, and maintainability** using automated **Quality Gates**.

The focus of this repo is **application-level analysis only** (Frontend / Backend code), independent of Infrastructure as Code.

---

## 🎯 Objective

The primary objective of this project is to:

* Shift-left **code quality & security**
* Detect bugs and vulnerabilities early in CI
* Enforce **Quality Gates** before merge/deploy
* Provide visibility via **SonarQube Dashboard**

---

## 🧠 What is SonarQube?

SonarQube is a **static code analysis platform** that continuously inspects application source code to detect:

* Bugs
* Code smells
* Security vulnerabilities
* Security hotspots
* Code duplication
* Test coverage issues

It integrates seamlessly with **Azure DevOps pipelines** and acts as a **quality gatekeeper** in the CI/CD process.

---

## 🔍 What We Scan in This Pipeline

Depending on the application stack, SonarQube analyzes:

### ✅ Code Quality

* Unused variables
* Complex logic
* Bad coding practices
* Maintainability issues (technical debt)

### ✅ Security

* OWASP Top 10 vulnerabilities
* Hardcoded secrets
* Insecure coding patterns
* Injection & auth-related issues

### ✅ Reliability

* Logical bugs
* Error-prone code paths

### ✅ Maintainability

* Code smells
* Cyclomatic complexity
* Duplicated blocks

---

## 🚦 SonarQube Quality Gates

Quality Gates are configured to **fail the pipeline automatically** if the code does not meet predefined standards.

### 🔐 Enforced Quality Gate Conditions

| Metric                     | Threshold |
| -------------------------- | --------- |
| New Bugs                   | = 0       |
| New Vulnerabilities        | = 0       |
| Security Hotspots Reviewed | 100%      |
| Code Smells                | Rating A  |
| Coverage on New Code       | ≥ 80%     |
| Duplications on New Code   | < 3%      |
| Reliability Rating         | A         |
| Security Rating            | A         |
| Maintainability Rating     | A         |

🛑 **If any condition fails → pipeline fails**

---

## 🔁 Azure DevOps CI Pipeline Flow

```text
Code Push / Pull Request
        ↓
Azure DevOps Pipeline Triggered
        ↓
SonarQube Prepare Analysis
        ↓
Run SonarQube Scan
        ↓
Publish Quality Gate Result
        ↓
Quality Gate Validation
        ↓
Pipeline Pass / Fail
```

✔ No deployment or merge is allowed if the Quality Gate fails

---

## ⚙️ SonarQube Pipeline Tasks Used (ADO)

* **SonarQubePrepare** – Configure scanner & project metadata
* **SonarQubeAnalyze** – Perform static code analysis
* **SonarQubePublish** – Fetch Quality Gate status

These tasks ensure **tight CI enforcement** of code standards.

---

## 📊 SonarQube Dashboard Output

After pipeline execution, analysis results are available on the **SonarQube dashboard**, including:

* Overall code health score
* Bugs & vulnerabilities trend
* File-level issue breakdown
* Technical debt estimation
* Coverage & duplication metrics

This enables continuous improvement and long-term code quality tracking.

---

## 🧩 Benefits of This Integration

✅ Early detection of issues (shift-left)
✅ Automated quality enforcement
✅ Improved security posture
✅ Reduced production bugs
✅ Clean & maintainable codebase

---

## 🧠 Real-World Use Case

In enterprise environments, SonarQube acts as a **mandatory quality gate** where:

* Developers cannot merge PRs with failed gates
* Releases are blocked on security issues
* Technical debt is tracked sprint over sprint

This repository mirrors the same **real-world CI standards**.

---


