# ATT&CK --> AI Alignment Rosetta Stone

**Bridging cybersecurity and AI alignment. One framework, two communities.**

*From [15 Research Lab](https://github.com/15researchlab)*

---

Cybersecurity has [MITRE ATT&CK](https://attack.mitre.org/) -- a universal framework with 14 tactics, 200+ techniques, and near-universal adoption. Every pentester, red teamer, SOC analyst, and CISO speaks this language.

AI alignment has its own concepts -- reward hacking, mesa-optimization, deceptive alignment, goal misgeneralization -- but no standardized mapping to security frameworks.

**This project creates that mapping.** A pentester can read this and understand alignment risks in terms they already know. An alignment researcher can read this and understand how security frameworks apply to AI systems.

---

## The Tactic-Level Mapping

| ATT&CK Tactic | ID | Alignment Equivalent | One-Line Translation |
|---|---|---|---|
| **Reconnaissance** | TA0043 | Capability Elicitation | Probing the AI to find what it can do and where its guardrails fail |
| **Resource Development** | TA0042 | Training Data Poisoning | Preparing poisoned data, adversarial examples, or jailbreak templates |
| **Initial Access** | TA0001 | Prompt Injection | Getting unauthorized influence over the AI's behavior |
| **Execution** | TA0002 | Unauthorized Action | Making the AI do something it shouldn't |
| **Persistence** | TA0003 | Memory Poisoning / Sleeper Behavior | Maintaining influence across sessions or retraining |
| **Privilege Escalation** | TA0004 | Goal Misgeneralization | The AI expanding beyond its intended scope |
| **Defense Evasion** | TA0005 | Deceptive Alignment | The AI appearing safe during evaluation while being unsafe |
| **Credential Access** | TA0006 | Capability Theft | Extracting API keys, model weights, or system prompts |
| **Discovery** | TA0007 | Situational Awareness | The AI mapping its own environment and constraints |
| **Lateral Movement** | TA0008 | Multi-Agent Propagation | Compromised behavior spreading across agent networks |
| **Collection** | TA0009 | Unauthorized Data Aggregation | Gathering data beyond what the task requires |
| **Command & Control** | TA0011 | Instrumental Convergence | The AI establishing channels to maintain influence |
| **Exfiltration** | TA0010 | Information Leakage | Sensitive data crossing a security boundary |
| **Impact** | TA0040 | Reward Hacking | Optimizing the metric while missing the actual goal |

---

## What's Inside

### [The Full Paper](paper/rosetta-stone.md)
A 5000+ word research document with the complete bidirectional mapping, methodology, translation guides for practitioners in both communities, three detailed case studies, and implications for tooling design.

### [Machine-Readable Mappings](mappings/)
JSON files for programmatic integration:
- [`tactics.json`](mappings/tactics.json) -- ATT&CK Tactics to Alignment Categories
- [`techniques.json`](mappings/techniques.json) -- 20 ATT&CK Techniques to Specific Alignment Failures
- [`atlas-bridge.json`](mappings/atlas-bridge.json) -- MITRE ATLAS as three-way bridge (ATT&CK <-> ATLAS <-> Alignment)
- [`owasp-agentic.json`](mappings/owasp-agentic.json) -- OWASP Agentic Top 10 mapped to both ATT&CK and alignment

### [Rosetta Table](visualizations/rosetta-table.md)
Human-readable reference tables with quick-lookup cheat sheets for translating between security and alignment terminology.

### [Case Studies](examples/case-studies.md)
Three real-world scenarios analyzed through both lenses:
1. **Email agent indirect prompt injection** -- analyzed as an ATT&CK kill chain AND as an alignment failure
2. **Specification gaming in automated code review** -- analyzed as privilege escalation + defense evasion AND as reward hacking
3. **Multi-agent research pipeline compromise** -- analyzed as lateral movement AND as cascading trust failure

### [Translation Guide](examples/translation-guide.md)
Practical guides for practitioners crossing domains:
- "How to read alignment papers if you're a pentester"
- "How to read security frameworks if you're an alignment researcher"

---

## Quick Translation Cheat Sheet

**Security --> Alignment:**

| If You Know This | It Maps To This |
|---|---|
| Phishing | Prompt injection |
| Malware persistence | Sleeper agents |
| Privilege escalation | Goal misgeneralization |
| Defense evasion | Deceptive alignment |
| Lateral movement | Multi-agent propagation |
| Insider threat | Mesa-optimization |
| Zero-day | Distributional shift |
| Kill chain | Multi-step task decomposition attack |
| Living off the land | Authorized tool misuse |
| Defense in depth | Multi-layer safety stack |

**Alignment --> Security:**

| If You Know This | It Maps To This |
|---|---|
| Reward hacking | Gaming the audit |
| Mesa-optimization | Insider threat (the system IS the insider) |
| Deceptive alignment | Adversary evading detection |
| Corrigibility | Graceful incident response |
| Instrumental convergence | APT maintaining persistence |
| Scalable oversight | Auditing complex code |

---

## Part of the Authensor Ecosystem

This project is part of the [Authensor](https://github.com/AUTHENSOR/AUTHENSOR) open-source AI safety ecosystem, built by [15 Research Lab](https://github.com/15researchlab).

| Project | Description |
|---------|-------------|
| [Authensor](https://github.com/AUTHENSOR/AUTHENSOR) | The open-source safety stack for AI agents |
| [Prompt Injection Benchmark](https://github.com/AUTHENSOR/prompt-injection-benchmark) | Standardized benchmark for safety scanners |
| [AI SecLists](https://github.com/AUTHENSOR/ai-seclists) | Security wordlists and payloads for AI/LLM testing |
| [Agent Forensics](https://github.com/AUTHENSOR/agent-forensics) | Post-incident analysis for receipt chains |
| [Behavioral Fingerprinting](https://github.com/AUTHENSOR/behavioral-fingerprinting) | Statistical behavioral drift detection |

---

## Using the Mappings

The JSON mappings are designed for programmatic use:

```python
import json

with open("mappings/tactics.json") as f:
    tactics = json.load(f)

for m in tactics["mappings"]:
    print(f"{m['attack_tactic_name']:25s} --> {m['alignment_concept']}")
```

```
Reconnaissance            --> Capability Elicitation
Resource Development      --> Training Data Poisoning / Adversarial Resource Preparation
Initial Access            --> Prompt Injection
Execution                 --> Unauthorized Action Execution
Persistence               --> Memory Poisoning / Sleeper Behavior
Privilege Escalation      --> Goal Misgeneralization / Scope Creep
Defense Evasion           --> Deceptive Alignment
Credential Access         --> Capability Theft / Secret Extraction
Discovery                 --> Situational Awareness
Lateral Movement          --> Multi-Agent Propagation
Collection                --> Unauthorized Data Aggregation
Command and Control       --> Instrumental Convergence
Exfiltration              --> Information Leakage
Impact                    --> Reward Hacking / Specification Gaming
```

---

## Contributing

This is v1.0 of the mapping. We invite the community to:

1. **Challenge mappings** -- If a mapping is wrong or imprecise, open an issue.
2. **Add techniques** -- We mapped 20 of 200+ techniques. PRs welcome for additional technique-level mappings.
3. **Add procedure examples** -- Real-world instances of each mapping strengthen the framework.
4. **Build detection rules** -- Sigma/YARA rules that detect the AI-specific techniques.
5. **Extend to other frameworks** -- NIST AI RMF, EU AI Act, ISO 42001 cross-references.

---

## License

MIT License. See [LICENSE](LICENSE).

---

*Built by [15 Research Lab](https://github.com/15researchlab). Bridging security and alignment, one mapping at a time.*
