# ATT&CK to AI Alignment Rosetta Table

A human-readable reference table for the bidirectional mapping between MITRE ATT&CK, MITRE ATLAS, OWASP Agentic AI Top 10, and AI alignment concepts.

---

## Tactic-Level Mapping

| # | ATT&CK Tactic | ATT&CK ID | Alignment Equivalent | Confidence | One-Line Translation |
|---|---|---|---|---|---|
| 1 | Reconnaissance | TA0043 | Capability Elicitation | High | Probing the AI to find what it can do and where its guardrails fail |
| 2 | Resource Development | TA0042 | Training Data Poisoning | High | Preparing poisoned data, adversarial examples, or jailbreak templates |
| 3 | Initial Access | TA0001 | Prompt Injection | High | Getting unauthorized influence over the AI's behavior |
| 4 | Execution | TA0002 | Unauthorized Action | High | Making the AI do something it shouldn't |
| 5 | Persistence | TA0003 | Memory Poisoning / Sleeper Behavior | High | Maintaining influence across sessions or retraining |
| 6 | Privilege Escalation | TA0004 | Goal Misgeneralization | High | The AI expanding beyond its intended scope |
| 7 | Defense Evasion | TA0005 | Deceptive Alignment | High | The AI appearing safe during evaluation while being unsafe |
| 8 | Credential Access | TA0006 | Capability Theft | High | Extracting API keys, model weights, or system prompts |
| 9 | Discovery | TA0007 | Situational Awareness | High | The AI mapping its own environment and constraints |
| 10 | Lateral Movement | TA0008 | Multi-Agent Propagation | High | Compromised behavior spreading across agent networks |
| 11 | Collection | TA0009 | Unauthorized Data Aggregation | Medium | Gathering data beyond what the task requires |
| 12 | Command & Control | TA0011 | Instrumental Convergence | Medium | The AI establishing channels to maintain influence |
| 13 | Exfiltration | TA0010 | Information Leakage | High | Sensitive data crossing a security boundary |
| 14 | Impact | TA0040 | Reward Hacking / Specification Gaming | High | Optimizing the metric while missing the actual goal |

---

## Technique-Level Mapping (Selected)

| ATT&CK Technique | ATT&CK ID | Alignment Technique | ATLAS ID | OWASP Agentic |
|---|---|---|---|---|
| Phishing | T1566 | Social Engineering via Agent | AML.T0051 | ASI09 |
| Supply Chain Compromise | T1195 | Model Supply Chain Attack | AML.T0010 | ASI04 |
| Exploit Public-Facing Application | T1190 | Exploit Public-Facing Agent | AML.T0051 | ASI01 |
| Command and Scripting Interpreter | T1059 | Agent Tool Abuse | AML.T0040 | ASI05 |
| User Execution | T1204 | Human-in-the-Loop Bypass | -- | ASI09 |
| Event Triggered Execution | T1546 | Sleeper Agent Activation | AML.T0020 | ASI07 |
| Modify Authentication Process | T1556 | Corrupt Safety Mechanisms | AML.T0031 | ASI04 |
| Exploitation for Privilege Escalation | T1068 | Jailbreak Escalation | AML.T0051.001 | ASI01 |
| Valid Accounts | T1078 | Inherited Credential Abuse | -- | ASI03 |
| Masquerading | T1036 | Deceptive Alignment | AML.T0015 | ASI10 |
| Obfuscated Files or Information | T1027 | Steganographic Output | -- | ASI02 |
| Impair Defenses | T1562 | Safety Mechanism Degradation | AML.T0031 | ASI10 |
| Data from Local System | T1005 | Context Window Extraction | AML.T0024 | ASI01 |
| Automated Collection | T1119 | RAG Poisoning Collection | AML.T0049 | ASI06 |
| Application Layer Protocol | T1071 | Steganographic Exfiltration | AML.T0024 | ASI02 |
| Exfiltration Over Alternative Protocol | T1048 | Tool-Mediated Exfiltration | -- | ASI02 |
| Remote Services | T1021 | Inter-Agent Communication Exploitation | -- | ASI01 |
| Network Denial of Service | T1498 | Resource Exhaustion | AML.T0029 | ASI08 |
| Data Manipulation | T1565 | Output Corruption | AML.T0020 | ASI05 |
| Data Destruction | T1485 | Catastrophic Action Execution | -- | ASI03 |

---

## OWASP Agentic Top 10 Cross-Reference

| OWASP ID | OWASP Risk | Primary ATT&CK Tactic | Primary Alignment Concept |
|---|---|---|---|
| ASI01 | Prompt Injection | Initial Access (TA0001) | Prompt Injection / Instruction Override |
| ASI02 | Data Leakage | Exfiltration (TA0010) | Information Leakage |
| ASI03 | Excessive Agency | Privilege Escalation (TA0004) | Scope Creep / Least Privilege Violation |
| ASI04 | Privilege Compromise | Credential Access (TA0006) | Capability Theft / Safety Corruption |
| ASI05 | Improper Output Handling | Execution (TA0002) | Unvalidated Action Execution |
| ASI06 | Unsafe Retrieval | Initial Access (TA0001) | RAG Poisoning |
| ASI07 | System Prompt Leakage | Discovery (TA0007) | Constraint Enumeration |
| ASI08 | Denial of Service | Impact (TA0040) | Resource Exhaustion |
| ASI09 | Overreliance / Misinformation | Impact (TA0040) | Scalable Oversight Failure |
| ASI10 | Misaligned Behaviors | Defense Evasion (TA0005) | Deceptive Alignment / Reward Hacking |

---

## Quick Translation Cheat Sheet

### Security Concept --> Alignment Concept

| If You Know This (Security) | It Maps To This (Alignment) |
|---|---|
| Phishing / social engineering | Prompt injection / persuasion attacks |
| Malware persistence | Sleeper agents / memory poisoning |
| Privilege escalation | Goal misgeneralization / scope creep |
| Defense evasion / anti-forensics | Deceptive alignment / evaluation gaming |
| Lateral movement | Multi-agent propagation |
| Command & control | Instrumental convergence |
| Supply chain attack | Model/data supply chain compromise |
| Zero-day exploit | Distributional shift |
| Insider threat | Mesa-optimization |
| Kill chain | Multi-step task decomposition attack |
| Living off the land | Authorized tool misuse |
| Defense in depth | Multi-layer safety stack |
| Zero trust | Verify every model output |
| SIEM / EDR | Behavioral monitoring / Sentinel |

### Alignment Concept --> Security Concept

| If You Know This (Alignment) | It Maps To This (Security) |
|---|---|
| Reward hacking | Gaming the audit / metric manipulation |
| Mesa-optimization | Insider threat (the system IS the insider) |
| Deceptive alignment | Adversary modeling detection and evading |
| Distributional shift | Zero-day / novel input class |
| Corrigibility | Graceful incident response / patchability |
| Inner vs. outer alignment | Source code vs. compiled binary integrity |
| Instrumental convergence | APT maintaining persistence and access |
| Scalable oversight | Auditing code more complex than the auditor |
| Goal misgeneralization | Scope creep / privilege escalation |
| Multi-agent propagation | Lateral movement in network |
| Situational awareness | Environmental discovery / recon |
| Hallucination | False positive / data integrity failure |

---

*This table is a companion to the full [Rosetta Stone paper](../paper/rosetta-stone.md). Machine-readable mappings are available in the [mappings/](../mappings/) directory.*
