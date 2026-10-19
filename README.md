<div align="center">

# 🎫 AI-Powered Support Ticket Classifier

### Human-in-the-Loop Review System — Implementation Specification

![Document](https://img.shields.io/badge/Document-Project%20Planning%20%26%20Management-1e3a8a?style=for-the-badge)
![Year](https://img.shields.io/badge/Academic%20Year-2026-2563eb?style=for-the-badge)
![Scope](https://img.shields.io/badge/Scope-5--Week%20Sprint-0ea5e9?style=for-the-badge)

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat-square&logo=mlflow&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white)

</div>

---

## 1️⃣ Executive Summary & Overview

Customer support operations in modern organizations face a persistent operational bottleneck: thousands of incoming support tickets must be manually read, categorized, and routed to the correct department. Industry estimates indicate that support teams waste **30–40%** of operational capacity on manual triage rather than resolving customer issues.

Current automated solutions fail by adopting rigid extremes: fully manual routing is slow and error-prone, while fully automated ML routing poses silent risks when handling ambiguous inputs.

> [!IMPORTANT]
> This project delivers an operational ML pipeline combining classical NLP (**TF-IDF + Logistic Regression**) with a **Human-in-the-Loop (HITL)** review mechanism for balanced efficiency and precision.

### Core System Workflow

<table align="center">
  <tr>
    <td align="center" width="25%"><h3>1</h3><b>Classifies</b><br>tickets automatically</td>
    <td align="center" width="25%"><h3>2</h3><b>Assigns</b><br>probability confidence scores</td>
    <td align="center" width="25%"><h3>3</h3><b>Escalates</b><br>low-confidence tickets (&lt;70%) to a Review Queue</td>
    <td align="center" width="25%"><h3>4</h3><b>Logs</b><br>all decisions in an Audit Log for feedback</td>
  </tr>
</table>

---

## 2️⃣ Project Problem & Core Capabilities

### 2.1 Key Operational Challenges

<table>
  <tr>
    <td width="50%">
      <h4>🐌 Manual Triage Bottleneck</h4>
      High ticket volume creates response delays.
    </td>
    <td width="50%">
      <h4>⚠️ Automation Risk</h4>
      Unverified models produce silent misclassifications.
    </td>
  </tr>
  <tr>
    <td width="50%">
      <h4>🔁 Missing Feedback Loop</h4>
      Manual corrections are rarely logged for retraining.
    </td>
    <td width="50%">
      <h4>🧑‍⚖️ Human Oversight Gap</h4>
      Autonomous AI lacks escalation mechanisms.
    </td>
  </tr>
</table>

### 2.2 Technical Solution Delivery

<table>
  <tr>
    <td width="50%">
      <h4>🧠 NLP Classification</h4>
      NLTK/spaCy text cleaning + TF-IDF representation.
    </td>
    <td width="50%">
      <h4>📊 Confidence Thresholds</h4>
      <code>predict_proba()</code> scoring with a 70% threshold.
    </td>
  </tr>
  <tr>
    <td width="50%">
      <h4>🖥️ Streamlit HITL Dashboard</h4>
      Real-time Review Queue for human validation.
    </td>
    <td width="50%">
      <h4>🧾 Traceable Audit Log</h4>
      SQLite/CSV record of reviewer actions &amp; timestamps.
    </td>
  </tr>
</table>

---

## 3️⃣ System Workflow Architecture

```mermaid
flowchart TD
    A["📩 Incoming Ticket<br/>Subject + Body Text"] --> B["🧹 NLP Preprocessing<br/>Clean / Lemma / TF-IDF"]
    B --> C["🤖 Classification Model<br/>Logistic Reg / Naive Bayes"]
    C --> D{"Confidence<br/>≥ 70%?"}
    D -->|"Yes (Auto)"| E["✅ Auto-Assign + Audit Log"]
    D -->|"No (Review)"| F["🙋 Review Queue (HITL)"]
    F --> G["📝 Human Review → Audit Log"]

    classDef input fill:#dbeafe,stroke:#1e3a8a,color:#1e3a8a,stroke-width:2px
    classDef process fill:#e0f2fe,stroke:#0369a1,color:#0c4a6e,stroke-width:2px
    classDef decision fill:#fef3c7,stroke:#d97706,color:#78350f,stroke-width:2px
    classDef auto fill:#dcfce7,stroke:#15803d,color:#14532d,stroke-width:2px
    classDef human fill:#fee2e2,stroke:#b91c1c,color:#7f1d1d,stroke-width:2px

    class A input
    class B,C process
    class D decision
    class E auto
    class F,G human
```

---

<div align="center">
<sub>Project Planning & Management Document — 2026</sub>
</div>
