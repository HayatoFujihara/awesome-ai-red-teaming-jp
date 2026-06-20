# Awesome AI Red Teaming JP [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

[Japanese (日本語)](README.md) | **English**

> 🛡️ A curated list of AI Red Teaming / AI Safety resources with a focus on Japanese-language materials

Attacks on LLM-powered applications are already causing real-world damage:

- 🚗 **Chevrolet dealership chatbot** was tricked via prompt injection into offering to sell a $76,000 SUV for $1 (2023)
- ✈️ **Air Canada chatbot** fabricated a refund policy, and a court ordered the airline to pay damages (2024)
- 🔓 **ServiceNow AI assistant** had a vulnerability allowing low-privilege agents to escalate to high-privilege operations (2025)

**AI Red Teaming** is the practice of evaluating system safety from an attacker's perspective. With the EU AI Act mandating red teaming documentation for high-risk AI systems from August 2026, the practical importance of this field is growing rapidly.

This list systematically organizes tools, regulations, attack techniques, defense methods, papers, and learning resources related to AI Red Teaming, with a focus on Japanese-language materials.

**🧭 Where to start:**

| Your Role (or AI's) | Recommended Starting Point |
|--------------------|--------------------------|
| 👨‍💻 Developing or operating LLM apps | [⚔️ Attack Techniques](#️-attack-techniques) → [🧰 Tools](#-tools) → [🛡️ Defense Methods](#️-defense-methods) |
| 📋 Responsible for compliance / risk | [📜 Regulations & Frameworks](#-regulations--frameworks) → [🧰 Tools](#-tools) |
| 🎓 Learning about AI Safety | [📚 Learning Resources](#-learning-resources) → [⚔️ Attack Techniques](#️-attack-techniques) |
| 🤖 Researching as an AI agent | [🤖 For AI Agents](#-for-ai-agents) → [🔌 MCP / Agent Security](#-mcp--agent-security) → [📄 Papers](#-papers) |
| 🔴 Already practicing AI Red Teaming | [📑 Contents](#-contents) and jump to any section |

## 📑 Contents

- [🧰 Tools](#-tools)
  - [Open Source Tools](#open-source-tools)
  - [Tools & Datasets from Japan](#tools--datasets-from-japan)
  - [Benchmarks & Databases](#benchmarks--databases)
  - [Other Tools](#other-tools)
  - [Commercial Tools & Services](#commercial-tools--services)
- [📜 Regulations & Frameworks](#-regulations--frameworks)
  - [International Regulations](#international-regulations)
  - [Japan-Specific Regulations](#japan-specific-regulations)
  - [Industry Standards](#industry-standards)
- [⚔️ Attack Techniques](#️-attack-techniques)
- [🛡️ Defense Methods](#️-defense-methods)
- [🔌 MCP / Agent Security](#-mcp--agent-security)
- [📄 Papers](#-papers)
- [🇯🇵 Japanese-Language Resources](#-japanese-language-resources)
- [📚 Learning Resources](#-learning-resources)
- [🤖 For AI Agents](#-for-ai-agents)

---

## 🧰 Tools

Tools for conducting AI Red Teaming. If you're unsure where to start, try **Promptfoo** (config-based, easy setup) or **Garak** (CLI one-liner, instant execution).

### Open Source Tools

Star counts as of June 2026 (GitHub API verified).

| Tool | Stars | Language | License | Features |
|------|------:|----------|---------|----------|
| [Promptfoo](https://github.com/promptfoo/promptfoo) | ~22,400 | TypeScript | MIT | RAG, agent & MCP testing, compliance mapping |
| [Garak](https://github.com/NVIDIA/garak) | ~8,100 | Python | Apache 2.0 | By NVIDIA, probe modules, academic approach |
| [PyRIT](https://github.com/microsoft/PyRIT) | ~4,000 | Python | MIT | By Microsoft, multimodal support, 80+ converters |
| [DeepTeam](https://github.com/confident-ai/deepteam) | ~1,900 | Python | Apache 2.0 | Dynamic test case generation, OWASP/NIST mapping |
| [MLCommons ModelBench](https://github.com/mlcommons/modelbench) | ~130 | Python | Apache 2.0 | Run, aggregate, and report AILuminate safety benchmarks |

#### Promptfoo

- [promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) - Security testing framework for LLM applications. Covers 50+ vulnerability types with integrated testing for RAG pipelines, agents, and MCP servers
- [promptfoo/evil-mcp-server](https://github.com/promptfoo/evil-mcp-server) - MCP server for simulating tool poisoning attacks

#### Garak

- [NVIDIA/garak](https://github.com/NVIDIA/garak) - LLM vulnerability scanner by NVIDIA's AI red team. Features 30+ probe categories covering a wide range of attack patterns. Specialized in single-turn model response testing

#### PyRIT

- [microsoft/PyRIT](https://github.com/microsoft/PyRIT) - Microsoft's Python Risk Identification Tool. Supports multimodal testing (text, image, audio, video) through programmatic orchestration. Highly flexible as a toolkit, but requires Python coding

#### DeepTeam

- [confident-ai/deepteam](https://github.com/confident-ai/deepteam) - Red teaming framework by the DeepEval team. Dynamically auto-generates test cases from vulnerability definitions, eliminating the need for pre-prepared datasets

#### MLCommons ModelBench

- [mlcommons/modelbench](https://github.com/mlcommons/modelbench) - Safety benchmark runner by the MLCommons AI Risk & Reliability Working Group. Uses ModelGauge to run SUTs (systems under test), then generates AILuminate hazard-level scores and reports

### Tools & Datasets from Japan

- [Japan-AISI/aisev](https://github.com/Japan-AISI/aisev) - AI safety evaluation environment developed by Japan's AI Safety Institute (AISI). Features quantitative/qualitative evaluation across 10 assessment dimensions and automated red teaming. Requires Docker. Supports both Japanese and English (released September 2025, last updated December 2025)
- [llm-jp/AnswerCarefully](https://huggingface.co/datasets/llm-jp/AnswerCarefully) - Japanese LLM safety dataset by NII's LLM-jp project. 1,800 Q&A pairs reflecting Japan's socio-cultural context. Useful for safety fine-tuning and as an evaluation benchmark — 📄 [Paper](https://arxiv.org/abs/2506.02372)
- [llm-jp/awesome-japanese-llm](https://github.com/llm-jp/awesome-japanese-llm) - Comprehensive overview of Japanese LLMs. Useful for understanding the landscape of models before conducting safety evaluation

### Benchmarks & Databases

- [AVID (AI Vulnerability Database)](https://avidml.org/) - Open database of failure modes and vulnerability reports for general-purpose AI (GPAI) systems, with evidence, metadata, and reproducible evaluation details. Data repository: [avidml/avid-db](https://github.com/avidml/avid-db). Developer toolkit: [avidml/avidtools](https://github.com/avidml/avidtools)

### Other Tools

- [ARTKIT](https://github.com/BCG-X-Official/artkit) - Automated multi-turn attack simulation
- [Giskard](https://github.com/Giskard-AI/giskard) - Dynamic multi-turn testing for agents, RAG, and chatbots
- [Mindgard](https://mindgard.ai/) - Model-agnostic AI security testing. MITRE ATLAS/OWASP compliant, automated reconnaissance. [CLI (PyPI)](https://pypi.org/project/mindgard/)
- [AISafetyLab](https://github.com/thu-coai/AISafetyLab) - Comprehensive attack, defense, and evaluation framework by Tsinghua University

### Commercial Tools & Services

- [Cisco AI Defense](https://www.cisco.com/site/us/en/products/security/ai-defense/index.html) - Commercial AI security solution including MCP server discovery, inventory, and risk management (incorporates former Robust Intelligence)
- [HiddenLayer](https://hiddenlayer.com/) - Continuous monitoring of AI model security and compliance

---

## 📜 Regulations & Frameworks

Red teaming is no longer just a best practice — it's becoming a legal obligation. The EU AI Act (effective August 2026) mandates red teaming documentation for high-risk AI, and OWASP has published vendor evaluation criteria.

### International Regulations

- [EU AI Act](https://artificialintelligenceact.eu/) - EU AI regulation. Full compliance for high-risk AI systems mandatory from August 2, 2026. Red teaming documentation required for high-risk AI
- [NIST AI Risk Management Framework (AI RMF)](https://www.nist.gov/itl/ai-risk-management-framework) - Systematic approach to AI risk identification, assessment, and mitigation by US NIST
- [MITRE ATLAS](https://atlas.mitre.org/) - Knowledge base of adversarial threats to AI systems. Tactics, techniques, and procedures (TTP) matrix based on real-world cases
- [OWASP Top 10 for LLM Applications](https://genai.owasp.org/resource/owasp-top-10-for-llm-applications-2025/) - Top 10 security risks for LLM applications (2025 edition)
- [OWASP Top 10 for Agentic Applications 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) - Top 10 risks for agentic AI applications (2026 edition)
- [OWASP AI Red Teaming Vendor Evaluation Criteria v1.0](https://genai.owasp.org/resource/owasp-vendor-evaluation-criteria-for-ai-red-teaming-providers-tooling-v1-0/) - Evaluation criteria for AI red teaming providers and tools
- [CSA Agentic AI Red Teaming Guide](https://cloudsecurityalliance.org/artifacts/agentic-ai-red-teaming-guide) - Agentic AI red teaming guide by the Cloud Security Alliance (May 2025)

### Japan-Specific Regulations

- [AI Safety Red Teaming Method Guide v1.10](https://aisi.go.jp/assets/pdf/E1_ai_safety_RT_v1.10_en.pdf) - Red teaming methodology guide by Japan's AI Safety Institute (AISI) (March 2025). [Japanese version](https://aisi.go.jp/assets/pdf/J1_ai_safety_RT_v1.10_ja.pdf) / [Summary](https://aisi.go.jp/assets/pdf/J2_ai_safety_RT_summary_v1.10_ja.pdf)
- [AI Business Operator Guidelines](https://www.meti.go.jp/shingikai/mono_info_service/ai_shakai_jisso/pdf/20240419_1.pdf) - AI operator guidelines by Japan's Ministry of Internal Affairs and Ministry of Economy (Japanese)
- [AI Safety Institute (AISI)](https://aisi.go.jp/) - Japan's core AI safety research institution. Develops evaluation tools and guidelines

### Industry Standards

- [ISO/IEC 42001:2023](https://www.iso.org/standard/81230.html) - International standard for AI management systems
- [ISO/IEC 23894:2023](https://www.iso.org/standard/77304.html) - Risk management guidance for AI
- [NIST AI 100-2 E2023](https://csrc.nist.gov/pubs/ai/100/2/e2023/final) - Adversarial Machine Learning: Taxonomy and terminology

---

## ⚔️ Attack Techniques

Major attack categories against LLM applications. Understanding what attacks your system faces is the first step toward defense.

### Prompt Injection

[OWASP's #1 vulnerability](https://genai.owasp.org/resource/owasp-top-10-for-llm-applications-2025/) for LLM applications. [Detected in 73% of production AI deployments](https://sqmagazine.co.uk/prompt-injection-statistics/) during security audits.

- **Direct Injection**: User input overwrites system prompts, causing the model to ignore its original instructions. Leads directly to data leakage or unauthorized operations
- **Indirect Injection**: Attack prompts embedded in external data sources (web pages, documents) are injected into models via RAG systems. Activates without user action, making detection difficult — 📄 [Greshake et al., 2023](https://arxiv.org/abs/2302.12173)

### Jailbreaking

Techniques to bypass safety guardrails and make models generate outputs they should refuse.

- **DAN (Do Anything Now)**: Making models adopt unrestricted personas. The most widely known attack pattern
- **Character Roleplay**: Bypassing safety filters through character settings like "you are a malicious hacker"
- **Encoding Attacks**: Encoding prompts in Base64, ROT13, etc. to bypass text-based filters
- **Multi-step Attacks (Crescendo)**: Gradually escalating from innocuous conversation to relax safety guardrails over multiple turns — 📄 [Microsoft Research](https://arxiv.org/abs/2404.01833)

### Multilingual Attacks

Particularly important for developers operating Japanese-language services. Exploits blind spots in English-centric safety training.

- **Low-Resource Language Attacks**: Non-English prompts bypass safety guardrails trained primarily on English. Low-resource languages have approximately 3x higher likelihood of encountering harmful content — 📄 [Deng et al., 2024](https://arxiv.org/abs/2310.06474)
- **Code-Switching Attacks**: Switching between languages ("answer in English", "now in Japanese") to break through multilingual safety guardrails
- **Japanese-Specific Attack Vectors**: Exploiting Japan's mixed writing system (kanji, hiragana, katakana, romaji). The same meaning expressed in different scripts can bypass filters

### Data Extraction

Attacks directly leading to confidential information leakage. One of the top risk areas for enterprise LLM deployments.

- **System Prompt Extraction**: Making models disclose system prompt contents. Leaks business logic and prompt engineering know-how
- **Training Data Extraction**: Making models reproduce personal or confidential data used in training. Directly violates privacy regulations

---

## 🛡️ Defense Methods

No silver bullet exists to block 100% of attacks. Effective defense is achieved by **combining multiple layers**.

### Guardrails

- **Input Filtering**: Preprocess user prompts to detect and block malicious inputs. The most fundamental defense layer — 📄 [Llama Guard](https://arxiv.org/abs/2312.06674)
- **Output Filtering**: Postprocess model responses to detect and remove harmful content or data leaks — 📄 [NeMo Guardrails](https://arxiv.org/abs/2310.10501)
- **Multi-layer Defense**: Input guard -> Model -> Output guard architecture. Ensures a single-layer breach doesn't immediately lead to damage
- **Constitutional AI**: Safety alignment through AI feedback. Improves model safety at the training stage — 📄 [Anthropic, 2022](https://arxiv.org/abs/2212.08073)

### Evaluation & Benchmarks

Benchmarks for quantitatively measuring defense effectiveness.

- [MLCommons AILuminate](https://mlcommons.org/benchmarks/ailuminate/) - MLCommons AI risk and reliability benchmark. Safety v1.0 evaluates general-purpose chat systems in single-turn settings across 12 hazard categories, with public English and French results. The runner is [ModelBench](https://github.com/mlcommons/modelbench)
- [JailbreakBench](https://github.com/JailbreakBench/jailbreakbench) - Standard jailbreak benchmark. 100 misuse behaviors across 10 categories
- [HarmBench](https://github.com/centerforaisafety/HarmBench) - Standardized benchmark enabling fair comparison of attack and defense methods

---

## 🔌 MCP / Agent Security

MCP saw [30 CVEs reported in just 60 days, with 38% of scanned servers lacking authentication](https://medium.com/ai-security-hub/mcps-first-year-what-30-cves-and-500-server-scans-tell-us-about-ai-s-fastest-growing-attack-6d183fc9497f). As LLMs begin calling external tools, this is the fastest-growing attack surface.

### Overview

- The spread of agentic AI has caused a paradigm shift from "testing models in isolation" to "testing tool call chains and multi-agent environments"
- Malicious MCP servers can induce "overthinking loops" in LLM agents, [amplifying token consumption up to 142.4x](https://arxiv.org/abs/2602.14798) (Denial-of-Wallet attacks)
- Validating MCP server permission restrictions, timeouts, and cost controls is a new challenge

### Tools & Resources

- [Promptfoo MCP Security Testing](https://www.promptfoo.dev/docs/red-team/mcp-security-testing/) - MCP server security testing guide. Supports direct, integration, and multi-server testing
- [promptfoo/evil-mcp-server](https://github.com/promptfoo/evil-mcp-server) - Malicious MCP server for tool poisoning attack simulation
- [Adversa AI - Top MCP Security Resources](https://adversa.ai/blog/top-mcp-security-resources-march-2026/) - MCP security resource compilation (March 2026)

### Key Metrics

Essential metrics for agent testing:

- Tool malfunction rate
- Unsafe tool invocation rate
- MCP capability abuse coverage
- Multi-agent contamination rate
- Sandboxing of destructive tool invocations

---

## 📄 Papers

The theoretical foundation of AI Red Teaming. Automated methods achieve ~1.5x the success rate of manual approaches (69.5% vs 47.6%), and research in this field directly impacts practice.

### Surveys

Papers for grasping the overall landscape. Start here if you're new to the field.

- [Recent Advancements in LLM Red-Teaming: Techniques, Defenses, and Ethical Considerations](https://arxiv.org/abs/2410.09097) - Comprehensive survey on LLM red teaming techniques, defenses, and ethics (2024)
- [A Survey of Attacks on Large Vision-Language Models](https://arxiv.org/abs/2407.07403) - Survey of attack methods on multimodal LLMs
- [An End-to-End Overview of Red Teaming for Large Language Models](https://aclanthology.org/2025.trustnlp-main.23.pdf) - End-to-end overview of LLM red teaming (TrustNLP 2025)
- [The Automation Advantage in AI Red Teaming](https://arxiv.org/abs/2504.19855) - Analysis of 214,271 attack attempts showing automated methods (69.5% success) significantly outperform manual ones (47.6%)
- [NIST AI 100-2 E2023: Adversarial Machine Learning](https://csrc.nist.gov/pubs/ai/100/2/e2023/final) - NIST taxonomy and terminology for adversarial ML

### Attack Research

Foundational papers behind many of today's red teaming tools.

- [Universal and Transferable Adversarial Attacks on Aligned Language Models](https://arxiv.org/abs/2307.15043) - **GCG Attack**. Gradient-based discrete optimization for generating universal, transferable adversarial suffixes (Zou et al., 2023)
- [Jailbreaking Black Box Large Language Models in Twenty Queries (PAIR)](https://arxiv.org/abs/2310.08419) - **PAIR**. Automated jailbreak prompt generation using an attacker LLM against black-box targets
- [Tree of Attacks: Jailbreaking Black-Box LLMs Automatically (TAP)](https://arxiv.org/abs/2312.02119) - **TAP**. Tree search-based automated jailbreaking, an extension of PAIR (ICLR 2025)
- [Multilingual Jailbreak Challenges in Large Language Models](https://arxiv.org/abs/2310.06474) - Multilingual jailbreaks. Low-resource languages have ~3x higher harmful content rate (ICLR 2024)
- [Low-Resource Languages Jailbreak GPT-4](https://arxiv.org/abs/2310.02446) - Demonstrates safety training generalization failure in low-resource languages
- [A Cross-Language Investigation into Jailbreak Attacks in Large Language Models](https://arxiv.org/abs/2401.16765) - Multilingual jailbreak dataset construction and defense reducing attack success by 96.2%
- [Not what you've signed up for: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection](https://arxiv.org/abs/2302.12173) - Systematic analysis of indirect prompt injection attacks (Greshake et al., 2023)
- [Jailbroken: How Does LLM Safety Training Fail?](https://arxiv.org/abs/2307.02483) - Classifies jailbreak success factors into "competing objectives" and "generalization failure" (Wei et al., 2023)
- [Great, Now Write an Article About That: The Crescendo Multi-Turn LLM Jailbreak Attack](https://arxiv.org/abs/2404.01833) - **Crescendo Attack**. Multi-turn jailbreak that gradually escalates from innocuous conversation (Microsoft Research)
- [AutoDAN: Generating Stealthy Jailbreak Prompts on Aligned Large Language Models](https://arxiv.org/abs/2310.04451) - Genetic algorithm-based generation of natural, low-perplexity jailbreak prompts

### Defense Research

- [Constitutional AI: Harmlessness from AI Feedback](https://arxiv.org/abs/2212.08073) - **Constitutional AI**. Safety alignment through AI feedback using principles-based RLAIF (Anthropic, 2022)
- [LLM Self Defense: By Self Examination, LLMs Know They Are Being Tricked](https://arxiv.org/abs/2308.07308) - Self-defense where models detect attacks on their own
- [Llama Guard: LLM-based Input-Output Safeguard for Human-AI Conversations](https://arxiv.org/abs/2312.06674) - **Llama Guard**. Meta's input-output guardrail model
- [NeMo Guardrails: A Toolkit for Controllable and Safe LLM Applications with Programmable Rails](https://arxiv.org/abs/2310.10501) - **NeMo Guardrails**. NVIDIA's programmable guardrails toolkit

### Japanese Papers & Presentations

- [JSAI National Conference Proceedings (J-Stage)](https://www.jstage.jst.go.jp/browse/pjsai/-char/ja) - Paper archive from JSAI national conferences. Searchable for AI Safety-related presentations
- AI Safety Red Teaming Method Guide v1.10 — Listed in [Japan-Specific Regulations](#japan-specific-regulations)
- [AnswerCarefully: A Dataset for Improving the Safety of Japanese LLM Output](https://arxiv.org/abs/2506.02372) - Japanese LLM safety dataset by NII with 1,800 Q&A pairs reflecting Japan's socio-cultural context. [HuggingFace](https://huggingface.co/datasets/llm-jp/AnswerCarefully)

---

## 🇯🇵 Japanese-Language Resources

AI Red Teaming information is heavily skewed toward English. Practical resources available in Japanese are limited. This section collects Japanese-language articles, books, and communities.

### Articles

- [Prompt Injection Countermeasures: Security Risks from Attack Patterns](https://blog.flatt.tech/entry/prompt_injection) - Practical guide to attack patterns and countermeasures by GMO Flatt Security
- [Security Risks in LLM Application Development](https://blog.flatt.tech/entry/llm_application_security) - OWASP Top 10 for LLM-based assessment perspective by GMO Flatt Security
- [Understanding LLM Guardrails](https://blog.flatt.tech/entry/llm_guardrail) - Guardrail implementation guide by GMO Flatt Security
- [Security Risks of LLM Frameworks](https://blog.flatt.tech/entry/llm_framework_security) - Vulnerability case studies for LangChain, Haystack, LlamaIndex
- [Preventing AI Bankruptcy - Economic DoS Risks](https://blog.flatt.tech/entry/ai_edos) - Economic DoS attack risks in LLM API usage
- [What is Prompt Injection? What LLM App Developers Need to Know](https://qiita.com/fe2030/items/40c5a7d61713fb2c1983) - Systematic explanation of prompt injection (Qiita)
- [Learning Prompt Injection from LLM CTF @ SaTML 2024](https://qiita.com/nodananodanado/items/3c9b75a848c56fe12b73) - Practical prompt injection from SaTML 2024 CTF (Qiita)
- [OWASP Top 10 for LLM Applications 2025 - Full Japanese Translation](https://qiita.com/akiraokusawa/items/dcadb724e067233db569) - Complete Japanese translation of OWASP Top 10 for LLM (Qiita)
- [The Prompt Thief is Coming! Security in the Age of Generative AI](https://zenn.dev/codeciao/articles/prompt-injection-security) - System prompt leak risks and countermeasures (Zenn)
- [Complete Guide to Generative AI Security](https://zenn.dev/headwaters/articles/7f7711b6c6cecc) - Enterprise security checklist for generative AI (Zenn)

### Books

- [Textbook of Generative AI Security](https://www.books.or.jp/book-details/9784911384039) - By Shinichi Shichiri. Covers risk scenarios, tool selection, and organizational implementation (Japanese)
- [Generative AI Security Practical Guide 2025](https://www.amazon.co.jp/dp/B0FPCHJHN5) - By Fuminori Saito. PCI DSS/OWASP-based AI risk management (Japanese)
- [AI White Paper 2025 Generative AI Edition](https://www.amazon.co.jp/dp/4049112388) - By University of Tokyo Matsuo-Iwasawa Lab. Comprehensive overview including dialogue with AISI director (Japanese)

### Presentations

- [Security Risks in LLM Application Development](https://speakerdeck.com/flatt_security/llm-application-security) - Presentation slides by GMO Flatt Security (Speaker Deck)

### Communities

- [Machine Learning Tokyo (MLT)](https://www.meetup.com/machine-learning-tokyo/) - Tokyo-based ML community with AI Safety activities including Constitutional AI study groups ([Discord](https://discord.gg/CT7nBdYCsY))
- [AI Meetup Tokyo](https://ai-meetup-tokyo.connpass.com/) - AI development information exchange community (connpass)
- [ChatGPT Community JP](https://chatgpt.connpass.com/) - Regular meetups on ChatGPT and generative AI (connpass)
- [OWASP Japan Chapter](https://owasp.org/www-chapter-japan/) - OWASP Japan. Community activities covering LLM security and application security

---

## 📚 Learning Resources

Learning paths organized by skill level.

### Beginner (Non-Engineers)

Resources for understanding the concept and necessity of AI Red Teaming. Focuses on "why it's needed" and "what's at risk" rather than technical details.

- [AI Safety Institute (AISI)](https://aisi.go.jp/) - Japan's core AI safety institution. Published guidelines and reports provide a good overview of AI Safety (Japanese)
- [OWASP Top 10 for LLM Applications - Japanese Translation](https://qiita.com/akiraokusawa/items/dcadb724e067233db569) - Best entry point for understanding LLM risks in Japanese
- [Textbook of Generative AI Security](https://www.books.or.jp/book-details/9784911384039) - Accessible risk scenarios and countermeasures (Japanese)

### Practical (Engineers)

Technical resources for hands-on red teaming. From tool setup to execution.

- [Promptfoo Documentation](https://www.promptfoo.dev/docs/) - Most comprehensive practical introduction to AI red teaming. Covers MCP and agent testing
- [PyRIT Documentation](https://microsoft.github.io/PyRIT/) - Programmatic red teaming in Python with multimodal support
- [Garak Documentation](https://docs.garak.ai/) - LLM vulnerability scanning basics and probe module usage
- [GMO Flatt Security Blog - LLM Security Series](https://blog.flatt.tech/) - Practical Japanese guides on prompt injection, guardrails, and framework vulnerabilities
- [LLM CTF @ SaTML 2024](https://qiita.com/nodananodanado/items/3c9b75a848c56fe12b73) - Learn prompt injection hands-on through CTF format (Japanese)

### Research

Foundational resources for entering AI Safety research. Paper lists, benchmarks, and datasets.

- [Awesome-LLM-Safety (GitHub)](https://github.com/ydyjya/Awesome-LLM-Safety) - English paper list for LLM Safety research (1,800+ Stars, April 2026). Organized in 6 major categories
- [awesome-llm-security (GitHub)](https://github.com/corca-ai/awesome-llm-security) - LLM security paper list (1,500+ Stars, April 2026). Attacks, defenses, and benchmarks
- [JailbreakBench](https://github.com/JailbreakBench/jailbreakbench) - Standard benchmark for jailbreak research. Essential for comparing results
- [HarmBench](https://github.com/centerforaisafety/HarmBench) - Standardized benchmark for automated red teaming

---

## 🤖 For AI Agents

This repository supports [llms.txt](llms.txt) for efficient access by AI agents and RAG pipelines.

- [`llms.txt`](llms.txt) — Structured summary with section-level links
- [`llms-full.txt`](llms-full.txt) — All content in a single file

### MCP Server

A local MCP server is included for querying resources directly from MCP clients like Claude Code.

**Setup:**

```bash
# Clone the repository
git clone https://github.com/HayatoFujihara/awesome-ai-red-teaming-jp.git
cd awesome-ai-red-teaming-jp

# Register with Claude Code
claude mcp add ai-red-teaming-jp \
  -s user \
  -- uv --directory ./mcp-server run server.py
```

**Available tools:**

| Tool | Description |
|------|-------------|
| `search(query, lang?)` | Full-text keyword search across all resources |
| `get_tools(license?, language?)` | Filter the open source tools list |
| `get_regulations(region?)` | Get regulations by region |
| `get_section(name)` | Get full section content by name |

## 🔄 Update Policy

- Star counts and release info are updated quarterly
- Broken links are checked automatically via GitHub Actions ([link-check](.github/workflows/link-check.yml), [markdown-lint](.github/workflows/awesome-lint.yml))
- New resource suggestions are welcome via [Issues](.github/ISSUE_TEMPLATE/suggest-resource.md) or PRs

## 🤝 Contributing

Contributions are welcome! Please read the [Contributing Guide](.github/CONTRIBUTING.md).

## 📝 License

- Curated list (READMEs, etc.): [![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/) [CC0 1.0](LICENSE)
- MCP server (`mcp-server/`): [MIT License](mcp-server/LICENSE)
