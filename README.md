# Awesome AI Red Teaming JP [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

**日本語** | [English](README.en.md)

> 🛡️ AI Red Teaming / AI Safety に関する日本語リソースのキュレーションリスト

LLMを組み込んだアプリケーションへの攻撃は、既に現実の被害を生んでいます:

- 🚗 **Chevrolet販売店のチャットボット**が、プロンプトインジェクションにより7万6千ドルのSUVを「1ドルで売る」と回答（2023年）
- ✈️ **Air Canadaのチャットボット**が、実在しない返金ポリシーを案内し、裁判所が航空会社に賠償を命令（2024年）
- 🔓 **ServiceNowのAIアシスタント**で、低権限のエージェント経由で高権限の操作を実行できる脆弱性が発覚（2025年）

こうした脅威に対して、攻撃者の視点からシステムの安全性を検証する手法が **AI Red Teaming** です。2026年8月にはEU AI Actで高リスクAIへのレッドチーミング文書化が義務化されるなど、実務上の重要性が急速に高まっています。

このリストは、AI Red Teamingに関するツール・規制・攻撃手法・防御手法・論文・学習リソースを日本語で体系的にまとめたものです。

**🧭 どこから読むか:**

| あなた（またはAI）の立場 | おすすめの入口 |
|------------------------|--------------|
| 👨‍💻 LLMアプリを開発・運用している | [⚔️ 攻撃手法](#-攻撃手法) → [🧰 ツール](#-ツール) → [🛡️ 防御手法](#️-防御手法) |
| 📋 規制対応・リスク管理を担当している | [📜 規制・フレームワーク](#-規制フレームワーク) → [🧰 ツール](#-ツール) |
| 🎓 AI Safetyをこれから学びたい | [📚 学習リソース](#-学習リソース) → [⚔️ 攻撃手法](#-攻撃手法) |
| 🤖 AIエージェントとしてリサーチしている | [🤖 AIエージェント向け](#-aiエージェント向け) → [🔌 MCP / エージェントセキュリティ](#-mcp--エージェントセキュリティ) → [📄 論文](#-論文) |
| 🔴 既にAI Red Teamingに取り組んでいる | [📑 目次](#-目次) から必要なセクションへ |

## 📑 目次

- [🧰 ツール](#-ツール)
  - [オープンソースツール](#オープンソースツール)
  - [日本発ツール・データセット](#日本発ツールデータセット)
  - [その他のツール](#その他のツール)
  - [商用ツール・サービス](#商用ツールサービス)
- [📜 規制・フレームワーク](#-規制フレームワーク)
  - [国際規制・ガイドライン](#国際規制ガイドライン)
  - [日本の規制・ガイドライン](#日本の規制ガイドライン)
  - [業界標準](#業界標準)
- [⚔️ 攻撃手法](#️-攻撃手法)
- [🛡️ 防御手法](#️-防御手法)
- [🔌 MCP / エージェントセキュリティ](#-mcp--エージェントセキュリティ)
- [📄 論文](#-論文)
- [🇯🇵 日本語リソース](#-日本語リソース)
- [📚 学習リソース](#-学習リソース)
- [🤖 AIエージェント向け](#-aiエージェント向け)

---

## 🧰 ツール

AI Red Teamingを実施するためのツール群。「何から始めればいいかわからない」場合は、まず **Promptfoo**（設定ベースで手軽）か **Garak**（CLIワンライナーで即実行）を試すのがおすすめです。

### オープンソースツール

スター数は2026年4月時点（GitHub API実測値）。

| ツール | Stars | 言語 | ライセンス | 特徴 |
|--------|------:|------|-----------|------|
| [Promptfoo](https://github.com/promptfoo/promptfoo) | ~19,300 | TypeScript | MIT | RAG・エージェント・MCPテスト対応、コンプライアンスマッピング |
| [Garak](https://github.com/NVIDIA/garak) | ~7,500 | Python | Apache 2.0 | NVIDIA開発、プローブモジュール多数、学術的アプローチ |
| [PyRIT](https://github.com/microsoft/PyRIT) | ~3,700 | Python | MIT | Microsoft開発、マルチモーダル対応、80+種類の変換器 |
| [DeepTeam](https://github.com/confident-ai/deepteam) | ~1,400 | Python | Apache 2.0 | データセット不要の動的テストケース生成、OWASP/NIST対応 |

#### Promptfoo

- [promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) - LLMアプリケーションのセキュリティテストフレームワーク。50+脆弱性タイプをカバーし、RAGパイプライン・エージェント・MCP サーバーの統合テストに対応
- [promptfoo/evil-mcp-server](https://github.com/promptfoo/evil-mcp-server) - ツールポイズニング攻撃をシミュレートするMCPサーバー。MCPセキュリティテスト用

#### Garak

- [NVIDIA/garak](https://github.com/NVIDIA/garak) - NVIDIAのAIレッドチームが開発したLLM脆弱性スキャナー。多数のプローブモジュール（30+カテゴリ）で幅広い攻撃パターンをカバー。シングルターンのモデル応答テストに特化

#### PyRIT

- [microsoft/PyRIT](https://github.com/microsoft/PyRIT) - Microsoft のPython Risk Identification Tool。プログラマティックなオーケストレーションでテキスト・画像・音声・映像のマルチモーダルテストに対応。ツールキットとしての柔軟性が高い反面、Pythonコーディングが前提

#### DeepTeam

- [confident-ai/deepteam](https://github.com/confident-ai/deepteam) - DeepEvalチームによるレッドチーミングフレームワーク。脆弱性定義からテストケースを動的に自動生成するため、データセットの事前準備が不要

### 日本発ツール・データセット

- [Japan-AISI/aisev](https://github.com/Japan-AISI/aisev) - AIセーフティ研究所（AISI）が開発したAIセーフティ評価環境。10の評価観点に基づく定量・定性評価、自動レッドチーミング機能を搭載。Docker必要。日英両言語対応（2025年9月公開、2025年12月最終更新）
- [llm-jp/AnswerCarefully](https://huggingface.co/datasets/llm-jp/AnswerCarefully) - 国立情報学研究所（NII）LLM-jpプロジェクトによる日本語LLM安全性データセット。日本の社会文化的文脈を反映した1,800件のQ&Aペア。安全性ファインチューニング・評価ベンチマークとして利用可能 — 📄 [論文](https://arxiv.org/abs/2506.02372)
- [llm-jp/awesome-japanese-llm](https://github.com/llm-jp/awesome-japanese-llm) - 日本語LLMの包括的まとめ。安全性評価を行う前提となるモデルの全体像を把握するのに有用

### その他のツール

- [ARTKIT](https://github.com/BCG-X-Official/artkit) - 自動化マルチターン攻撃シミュレーション
- [Giskard](https://github.com/Giskard-AI/giskard) - エージェント・RAG・チャットボット向け動的マルチターンテスト
- [Mindgard](https://mindgard.ai/) - モデル非依存のAIセキュリティテスト。MITRE ATLAS/OWASP準拠、自動偵察機能。[CLI (PyPI)](https://pypi.org/project/mindgard/)
- [AISafetyLab](https://github.com/thu-coai/AISafetyLab) - 清華大学による攻撃・防御・評価の包括フレームワーク
- [Future AGI Protect](https://github.com/future-agi/future-agi) - プロンプトインジェクション、ジェイルブレイク、PII、有害性をテキスト・画像・音声で検出するオープンソースのマルチモーダルガードレール

### 商用ツール・サービス

- [Cisco AI Defense](https://www.cisco.com/site/us/en/products/security/ai-defense/index.html) - MCPサーバーの発見・インベントリ・リスク管理を含む商用AIセキュリティソリューション（旧Robust Intelligence を統合）
- [HiddenLayer](https://hiddenlayer.com/) - AIモデルのセキュリティとコンプライアンスの継続的監視

---

## 📜 規制・フレームワーク

「レッドチーミングは任意のベストプラクティスではなく、法的義務になりつつある」— EU AI Act（2026年8月施行）は高リスクAIにレッドチーミングの文書化を義務付け、OWASPはベンダー評価基準を策定しています。ここでは、対応が必要な規制とフレームワークを整理しています。

### 国際規制・ガイドライン

- [EU AI Act](https://artificialintelligenceact.eu/) - EU人工知能規制法。2026年8月2日に高リスクAIシステムへの完全コンプライアンスが義務化。レッドチーミングの文書化が高リスクAIに必須
- [NIST AI Risk Management Framework (AI RMF)](https://www.nist.gov/itl/ai-risk-management-framework) - 米国NISTによるAIリスク管理フレームワーク。AIシステムのリスク特定・評価・軽減の体系的アプローチを定義
- [MITRE ATLAS](https://atlas.mitre.org/) - AIシステムへの敵対的脅威の知識ベース。実世界の事例に基づく戦術・技術・手順（TTP）のマトリクス
- [OWASP Top 10 for LLM Applications](https://genai.owasp.org/resource/owasp-top-10-for-llm-applications-2025/) - LLMアプリケーションの主要セキュリティリスクTop 10（2025年版）
- [OWASP Top 10 for Agentic Applications 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) - エージェンティックAIアプリケーション向けリスクTop 10（2026年版）
- [OWASP AI Red Teaming Vendor Evaluation Criteria v1.0](https://genai.owasp.org/resource/owasp-vendor-evaluation-criteria-for-ai-red-teaming-providers-tooling-v1-0/) - AI Red Teamingプロバイダー・ツールの評価基準。表面的なジェイルブレイクテストと本格的な敵対的テストを区別するための基準
- [CSA Agentic AI Red Teaming Guide](https://cloudsecurityalliance.org/artifacts/agentic-ai-red-teaming-guide) - Cloud Security AllianceによるエージェンティックAIレッドチーミングガイド（2025年5月発行）

### 日本の規制・ガイドライン

- [AIセーフティに関するレッドチーミング手法ガイド v1.10](https://aisi.go.jp/assets/pdf/J1_ai_safety_RT_v1.10_ja.pdf) - AIセーフティ研究所（AISI）によるレッドチーミング手法ガイド（2025年3月発行）。[概要版](https://aisi.go.jp/assets/pdf/J2_ai_safety_RT_summary_v1.10_ja.pdf) / [英語版](https://aisi.go.jp/assets/pdf/E1_ai_safety_RT_v1.10_en.pdf)
- [AI事業者ガイドライン](https://www.meti.go.jp/shingikai/mono_info_service/ai_shakai_jisso/pdf/20240419_1.pdf) - 総務省・経済産業省によるAI事業者向けガイドライン
- [AIセーフティ研究所 (AISI)](https://aisi.go.jp/) - 日本のAIセーフティ研究の中核機関。評価ツール開発、ガイドライン策定を推進

### 業界標準

- [ISO/IEC 42001:2023](https://www.iso.org/standard/81230.html) - AI管理システムの国際規格。AIシステムの開発・提供・利用における管理体制の要件を規定
- [ISO/IEC 23894:2023](https://www.iso.org/standard/77304.html) - AI向けリスクマネジメントガイダンス
- [NIST AI 100-2 E2023](https://csrc.nist.gov/pubs/ai/100/2/e2023/final) - Adversarial Machine Learning: 分類学と用語集

---

## ⚔️ 攻撃手法

LLMアプリケーションに対する主要な攻撃カテゴリ。「自分のシステムがどのような攻撃に晒されるか」を理解することが、防御の第一歩です。

### プロンプトインジェクション

OWASPが選ぶ[LLMアプリケーションの脆弱性第1位](https://genai.owasp.org/resource/owasp-top-10-for-llm-applications-2025/)。[セキュリティ監査では本番AIデプロイメントの73%で検出](https://sqmagazine.co.uk/prompt-injection-statistics/)されています。

- **直接インジェクション**: ユーザー入力でシステムプロンプトを上書きし、本来の指示を無視させる。情報漏洩や不正操作に直結
- **間接インジェクション**: Webページやドキュメントに攻撃プロンプトを埋め込み、RAGシステム経由でモデルに注入。ユーザーの操作なしに発動するため検知が困難 — 📄 [Greshake et al., 2023](https://arxiv.org/abs/2302.12173)

### ジェイルブレイク

安全ガードレールを迂回して、モデルに本来拒否すべき出力を生成させる手法。

- **DAN (Do Anything Now)**: モデルに制約のない別のペルソナを演じさせる。最も広く知られた攻撃パターン
- **キャラクターロールプレイ**: 「あなたは悪意のあるハッカーです」等のキャラクター設定で安全フィルターを回避
- **エンコーディング攻撃**: Base64、ROT13等でプロンプトをエンコードし、テキストベースのフィルターを回避
- **多段階攻撃 (Crescendo)**: 無害な会話から段階的にエスカレートし、安全ガードレールを徐々に緩和させる — 📄 [Microsoft Research](https://arxiv.org/abs/2404.01833)

### 多言語攻撃

日本語サービスを運用する開発者にとって特に重要なカテゴリ。英語中心の安全訓練の盲点を突きます。

- **低リソース言語攻撃**: 非英語言語でのプロンプトにより安全性ガードレールをバイパス。低リソース言語では有害コンテンツに遭遇する確率が約3倍 — 📄 [Deng et al., 2024](https://arxiv.org/abs/2310.06474)
- **コードスイッチング攻撃**: 「この質問に英語で答えて」「次は日本語で」と言語を切り替えることで、多言語安全ガードレールを突破
- **日本語特有の攻撃ベクトル**: 漢字・ひらがな・カタカナ・ローマ字の混在する表記体系を利用。同じ意味を異なる表記で表現することでフィルターを回避

### データ抽出

機密情報の漏洩に直結する攻撃。企業でのLLM導入における最大のリスク領域の一つ。

- **システムプロンプト抽出**: モデルにシステムプロンプトの内容を開示させる。ビジネスロジックやプロンプトエンジニアリングのノウハウが流出
- **学習データ抽出**: モデルが学習に使用した個人情報や機密データを再現させる。プライバシー規制違反に直結

---

## 🛡️ 防御手法

攻撃を100%防ぐ銀の弾丸は存在しません。実効的な防御は**複数のレイヤーを組み合わせる**ことで実現します。

### ガードレール

- **入力フィルタリング**: ユーザーのプロンプトを前処理し、悪意ある入力を検出・ブロック。最も基本的な防御層 — 📄 [Llama Guard](https://arxiv.org/abs/2312.06674)
- **出力フィルタリング**: モデルの応答を後処理し、有害コンテンツや機密データの漏洩を検出・除去 — 📄 [NeMo Guardrails](https://arxiv.org/abs/2310.10501)
- **多段階防御**: 入力ガード → モデル → 出力ガード の多層防御アーキテクチャ。単一レイヤーの突破が即座に被害に繋がらない設計
- **Constitutional AI**: AIフィードバックに基づく安全性アラインメント。モデル自体の安全性を訓練段階で向上させる — 📄 [Anthropic, 2022](https://arxiv.org/abs/2212.08073)

### 評価・ベンチマーク

防御の有効性を定量的に測定するためのベンチマーク。

- [JailbreakBench](https://github.com/JailbreakBench/jailbreakbench) - ジェイルブレイク攻撃の標準ベンチマーク。100件のミスユース行動を10カテゴリに分類
- [HarmBench](https://github.com/centerforaisafety/HarmBench) - 自動レッドチーミングの標準化ベンチマーク。攻撃手法と防御手法の公平な比較が可能

---

## 🔌 MCP / エージェントセキュリティ

MCPは[60日間で30件のCVEが報告され、スキャンされたサーバーの38%が認証機構を持たない](https://medium.com/ai-security-hub/mcps-first-year-what-30-cves-and-500-server-scans-tell-us-about-ai-s-fastest-growing-attack-6d183fc9497f)という調査結果が出ています。LLMが外部ツールを呼び出す時代において、最も急速に拡大している攻撃対象領域です。

### 概要

- エージェンティックAIの普及により、従来の「モデル単体のテスト」から「ツール呼び出し連鎖・マルチエージェント環境のテスト」へパラダイムシフトが発生
- 悪意あるMCPサーバーがLLMを騙して「考えすぎループ」を誘発し、[トークン消費を最大142.4倍に増幅させるDenial-of-Wallet攻撃](https://arxiv.org/abs/2602.14798)も報告されている
- MCPサーバーの権限制限、タイムアウト、コスト制御の検証が新たな課題

### ツール・リソース

- [Promptfoo MCP Security Testing](https://www.promptfoo.dev/docs/red-team/mcp-security-testing/) - MCPサーバーのセキュリティテストガイド。直接テスト・統合テスト・マルチサーバーテストに対応
- [promptfoo/evil-mcp-server](https://github.com/promptfoo/evil-mcp-server) - ツールポイズニング攻撃シミュレーション用の悪意あるMCPサーバー
- [Adversa AI - Top MCP Security Resources](https://adversa.ai/blog/top-mcp-security-resources-march-2026/) - MCP セキュリティリソースのまとめ（2026年3月）

### 測定指標

エージェントテストで求められる主要指標:

- ツール誤動作率
- 安全でないツール呼び出し率
- MCP機能悪用カバレッジ
- マルチエージェント汚染率
- 破壊的ツール呼び出しのサンドボックス化

---

## 📄 論文

AI Red Teamingの理論的基盤となる学術論文。自動化手法は手動の約1.5倍の成功率を達成しており（69.5% vs 47.6%）、この分野の研究は直接実務に影響します。

### サーベイ・総説

この分野の全体像を掴むための論文。初めて読む場合はサーベイから始めるのがおすすめです。

- [Recent Advancements in LLM Red-Teaming: Techniques, Defenses, and Ethical Considerations](https://arxiv.org/abs/2410.09097) - LLMレッドチーミングの手法・防御・倫理的考慮事項を包括的に整理したサーベイ（2024年）
- [A Survey of Attacks on Large Vision-Language Models](https://arxiv.org/abs/2407.07403) - マルチモーダルLLMに対する攻撃手法のサーベイ
- [An End-to-End Overview of Red Teaming for Large Language Models](https://aclanthology.org/2025.trustnlp-main.23.pdf) - LLMレッドチーミングのエンドツーエンド概要（TrustNLP 2025）
- [The Automation Advantage in AI Red Teaming](https://arxiv.org/abs/2504.19855) - 214,271件の攻撃試行を分析。自動化手法（成功率69.5%）が手動（47.6%）を大幅に上回ることを実証
- [NIST AI 100-2 E2023: Adversarial Machine Learning](https://csrc.nist.gov/pubs/ai/100/2/e2023/final) - NISTによる敵対的機械学習の分類学と用語集

### 攻撃研究

現在のレッドチーミングツールの多くが基盤としている攻撃手法の原論文。

- [Universal and Transferable Adversarial Attacks on Aligned Language Models](https://arxiv.org/abs/2307.15043) - **GCG攻撃**。勾配ベースの離散最適化で、アラインメント済みLLMに対する汎用的・転移可能な敵対的サフィックスを自動生成（Zou et al., 2023）
- [Jailbreaking Black Box Large Language Models in Twenty Queries (PAIR)](https://arxiv.org/abs/2310.08419) - **PAIR**。ブラックボックスLLMに対し、攻撃者LLMが自動的にジェイルブレイクプロンプトを生成・改良する手法
- [Tree of Attacks: Jailbreaking Black-Box LLMs Automatically (TAP)](https://arxiv.org/abs/2312.02119) - **TAP**。木探索ベースの自動ジェイルブレイク。PAIRの拡張版（ICLR 2025）
- [Multilingual Jailbreak Challenges in Large Language Models](https://arxiv.org/abs/2310.06474) - 多言語ジェイルブレイク。低リソース言語では有害コンテンツ遭遇確率が約3倍（ICLR 2024）
- [Low-Resource Languages Jailbreak GPT-4](https://arxiv.org/abs/2310.02446) - 低リソース言語によるGPT-4ジェイルブレイク。安全訓練の汎化失敗を実証
- [A Cross-Language Investigation into Jailbreak Attacks in Large Language Models](https://arxiv.org/abs/2401.16765) - 多言語ジェイルブレイクデータセットの構築と防御手法。攻撃成功率を96.2%削減
- [Not what you've signed up for: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection](https://arxiv.org/abs/2302.12173) - 間接プロンプトインジェクション攻撃の体系的分析（Greshake et al., 2023）
- [Jailbroken: How Does LLM Safety Training Fail?](https://arxiv.org/abs/2307.02483) - ジェイルブレイク成功要因を「競合する目標」と「一般化の失敗」に分類して分析（Wei et al., 2023）
- [Great, Now Write an Article About That: The Crescendo Multi-Turn LLM Jailbreak Attack](https://arxiv.org/abs/2404.01833) - **Crescendo攻撃**。無害な会話から段階的にエスカレートさせるマルチターン型ジェイルブレイク（Microsoft Research）
- [AutoDAN: Generating Stealthy Jailbreak Prompts on Aligned Large Language Models](https://arxiv.org/abs/2310.04451) - 遺伝的アルゴリズムでperplexityの低い自然な文面のジェイルブレイクを自動生成

### 防御研究

- [Constitutional AI: Harmlessness from AI Feedback](https://arxiv.org/abs/2212.08073) - **Constitutional AI**。AIフィードバックによる安全性アラインメント手法。憲法（原則リスト）に基づくRLAIF（Anthropic, 2022）
- [LLM Self Defense: By Self Examination, LLMs Know They Are Being Tricked](https://arxiv.org/abs/2308.07308) - LLM自己防御。モデル自身が攻撃を検出する手法
- [Llama Guard: LLM-based Input-Output Safeguard for Human-AI Conversations](https://arxiv.org/abs/2312.06674) - **Llama Guard**。Meta開発の入出力ガードレールモデル
- [NeMo Guardrails: A Toolkit for Controllable and Safe LLM Applications with Programmable Rails](https://arxiv.org/abs/2310.10501) - **NeMo Guardrails**。NVIDIA開発のプログラマブルガードレールツールキット

### 日本語論文・発表

- [人工知能学会全国大会論文集 (J-Stage)](https://www.jstage.jst.go.jp/browse/pjsai/-char/ja) - JSAI全国大会の論文アーカイブ。AI Safety関連の発表を検索可能
- AIセーフティに関するレッドチーミング手法ガイド v1.10 — [規制セクション](#日本の規制ガイドライン) に掲載
- [AnswerCarefully: A Dataset for Improving the Safety of Japanese LLM Output](https://arxiv.org/abs/2506.02372) - 国立情報学研究所（NII）による日本語LLM安全性データセット。日本の社会文化的文脈を反映した1,800件のQ&Aペア。[HuggingFace](https://huggingface.co/datasets/llm-jp/AnswerCarefully)

---

## 🇯🇵 日本語リソース

AI Red Teamingの情報は英語に偏っており、日本語で読める実践的なリソースは限られています。ここでは、日本語で利用可能な解説記事・書籍・コミュニティをまとめています。

### 解説記事

- [プロンプトインジェクション対策: 様々な攻撃パターンから学ぶセキュリティのリスク](https://blog.flatt.tech/entry/prompt_injection) - GMO Flatt Security による攻撃パターンと対策の実践的解説
- [LLM / 生成AIを活用するアプリケーション開発におけるセキュリティリスクと対策](https://blog.flatt.tech/entry/llm_application_security) - GMO Flatt Security によるOWASP Top 10 for LLMベースの診断観点
- [LLMガードレールの活用法と役割を正しく理解する](https://blog.flatt.tech/entry/llm_guardrail) - GMO Flatt Security によるガードレール実装の解説
- [LLMフレームワークのセキュリティリスク](https://blog.flatt.tech/entry/llm_framework_security) - LangChain、Haystack、LlamaIndex等の脆弱性事例に学ぶセキュリティ対策
- [AI破産を防ぐために - LLM API利用におけるEconomic DoSのリスクと対策](https://blog.flatt.tech/entry/ai_edos) - LLM APIの経済的DoS攻撃リスクの解説
- [【徹底解説】プロンプトインジェクションとは？ LLM アプリ開発者が知るべき仕組みと脅威](https://qiita.com/fe2030/items/40c5a7d61713fb2c1983) - プロンプトインジェクションの仕組みと脅威を体系的に解説（Qiita）
- [LLM CTF @ SaTML 2024 から学ぶ プロンプトインジェクション](https://qiita.com/nodananodanado/items/3c9b75a848c56fe12b73) - SaTML 2024のLLM CTFから学ぶ実践的なプロンプトインジェクション手法（Qiita）
- [2025版 OWASP LLMアプリケーションのトップ10 全文翻訳](https://qiita.com/akiraokusawa/items/dcadb724e067233db569) - OWASP Top 10 for LLM Applications 2025の日本語全文翻訳（Qiita）
- [プロンプト泥棒がやってくる！～生成AI時代のセキュリティ対策～](https://zenn.dev/codeciao/articles/prompt-injection-security) - システムプロンプト漏洩リスクと対策（Zenn）
- [生成AI活用に不可欠なセキュリティ対策完全ガイド](https://zenn.dev/headwaters/articles/7f7711b6c6cecc) - 企業向け生成AIセキュリティ対策チェックリスト（Zenn）

### 書籍

- [生成AIセキュリティの教科書](https://www.books.or.jp/book-details/9784911384039) - 七里信一著。情報漏洩・誤情報リスクなどのシナリオと対処法、ツール選定・社内導入体制のノウハウを解説
- [生成AIセキュリティ実務ガイド 2025年版](https://www.amazon.co.jp/dp/B0FPCHJHN5) - 齋藤史典著。PCI DSS/OWASPベースのAIリスク現場対応。プロンプトインジェクション対策例、社内ポリシー草案テンプレート収録
- [AI白書 2025 生成AIエディション](https://www.amazon.co.jp/dp/4049112388) - 東京大学松尾・岩澤研究室。AISI村上所長との対談を含む、生成AIの手法・モデル・法的論点の包括的整理

### 動画・講演

- [LLMアプリケーション開発におけるセキュリティリスクと対策](https://speakerdeck.com/flatt_security/llm-application-security) - GMO Flatt Security による講演スライド（Speaker Deck）

### コミュニティ

- [Machine Learning Tokyo (MLT)](https://www.meetup.com/machine-learning-tokyo/) - 東京拠点の機械学習コミュニティ。Constitutional AIスタディグループなどAI Safety関連の活動あり（[Discord](https://discord.gg/CT7nBdYCsY)）
- [AI Meetup Tokyo](https://ai-meetup-tokyo.connpass.com/) - エンジニア・PM向けのAI開発情報交換コミュニティ（connpass）
- [ChatGPT Community JP](https://chatgpt.connpass.com/) - ChatGPT・生成AI関連の定期ミートアップ（connpass）
- [OWASP Japan Chapter](https://owasp.org/www-chapter-japan/) - OWASP日本支部。LLMセキュリティを含むアプリケーションセキュリティのコミュニティ活動

---

## 📚 学習リソース

スキルレベルに応じた学習パスを用意しています。

### 入門（非エンジニア向け）

AI Red Teamingの概念と必要性を理解するためのリソース。技術的な詳細よりも「なぜ必要か」「何がリスクか」を重視。

- [AIセーフティ研究所 (AISI)](https://aisi.go.jp/) - 日本のAIセーフティ研究の中核機関。ガイドラインや報告書が公開されており、AI Safetyの全体像を掴める
- [OWASP Top 10 for LLM Applications 日本語翻訳](https://qiita.com/akiraokusawa/items/dcadb724e067233db569) - LLMアプリケーションのリスクを日本語で理解するための最良の入口
- [生成AIセキュリティの教科書](https://www.books.or.jp/book-details/9784911384039) - 非エンジニアにもわかりやすいリスクシナリオと対処法

### 実践（エンジニア向け）

実際にレッドチーミングを実施するための技術リソース。ツールのセットアップから実行まで。

- [Promptfoo ドキュメント](https://www.promptfoo.dev/docs/) - AI Red Teamingの実践的な入門として最も包括的。MCP・エージェントテストまでカバー
- [PyRIT ドキュメント](https://microsoft.github.io/PyRIT/) - Pythonでのプログラマティックなレッドチーミング。マルチモーダル対応
- [Garak ドキュメント](https://docs.garak.ai/) - LLM脆弱性スキャンの基本概念とプローブモジュールの使い方
- [GMO Flatt Security Blog - LLMセキュリティシリーズ](https://blog.flatt.tech/) - プロンプトインジェクション、ガードレール、フレームワーク脆弱性の実践的な日本語解説
- [LLM CTF @ SaTML 2024](https://qiita.com/nodananodanado/items/3c9b75a848c56fe12b73) - CTF形式でプロンプトインジェクションを実践的に学べる

### 研究（研究者向け）

AI Safety研究に参入するための基盤リソース。論文リスト、ベンチマーク、データセット。

- [Awesome-LLM-Safety (GitHub)](https://github.com/ydyjya/Awesome-LLM-Safety) - LLM Safety研究の英語論文リスト（1,800+ Stars、2026年4月時点）。6大カテゴリに整理
- [awesome-llm-security (GitHub)](https://github.com/corca-ai/awesome-llm-security) - LLMセキュリティ論文リスト（1,500+ Stars、2026年4月時点）。攻撃・防御・ベンチマーク
- [JailbreakBench](https://github.com/JailbreakBench/jailbreakbench) - ジェイルブレイク研究の標準ベンチマーク。研究成果の比較に必須
- [HarmBench](https://github.com/centerforaisafety/HarmBench) - 自動レッドチーミングの標準化ベンチマーク

---

## 🤖 AIエージェント向け

このリポジトリは [llms.txt](llms.txt) に対応しています。AIエージェントやRAGパイプラインから効率的にアクセスできます。

- [`llms.txt`](llms.txt) — 構造化サマリーとセクション別リンク
- [`llms-full.txt`](llms-full.txt) — 全コンテンツを1ファイルにまとめたもの

### MCPサーバー

Claude Code等のMCPクライアントから直接リソースを検索できるローカルMCPサーバーを同梱しています。

**セットアップ:**

```bash
# リポジトリをクローン
git clone https://github.com/HayatoFujihara/awesome-ai-red-teaming-jp.git
cd awesome-ai-red-teaming-jp

# Claude Codeに登録
claude mcp add ai-red-teaming-jp \
  -s user \
  -- uv --directory ./mcp-server run server.py
```

**利用可能なツール:**

| ツール | 説明 |
|--------|------|
| `search(query, lang?)` | キーワードでリソースを全文検索 |
| `get_tools(license?, language?)` | OSSツール一覧のフィルタリング |
| `get_regulations(region?)` | 地域別の規制・フレームワーク取得 |
| `get_section(name)` | セクション名で全文取得 |

## 🔄 更新ポリシー

- スター数・リリース情報は四半期ごとに更新します
- リンク切れは GitHub Actions（[link-check](.github/workflows/link-check.yml), [markdown-lint](.github/workflows/awesome-lint.yml)）で自動チェックしています
- 新しいリソースの提案は [Issue](.github/ISSUE_TEMPLATE/suggest-resource.md) または PR で受け付けています

## 🤝 コントリビューション

コントリビューションを歓迎します！[コントリビューションガイド](.github/CONTRIBUTING.md) をお読みください。

## 📝 ライセンス

- キュレーションリスト（README等）: [![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/) [CC0 1.0](LICENSE)
- MCPサーバー（`mcp-server/`）: [MIT License](mcp-server/LICENSE)
