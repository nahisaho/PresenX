# PrezenX

**VS Code + Claude Code で実現する次世代プレゼンテーション開発フレームワーク**

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live-brightgreen)](https://nahisaho.github.io/PresenX/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE.txt)
[![VS Code](https://img.shields.io/badge/VS%20Code-Integrated-blue)](https://code.visualstudio.com/)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Powered-purple)](https://claude.ai/code)

---

## 🚀 プレゼンテーション作成を80%高速化

PrezenXは、**VS Code + Claude Code協働開発モデル**により、従来20時間かかっていたプレゼンテーション作成を**3-5時間で完成**させる革新的なフレームワークです。

### ⚡ 驚異的な時間短縮実績

| 従来手法 | PrezenX | 削減率 |
|:---:|:---:|:---:|
| **20時間** | **3-5時間** | **80%削減** |

*筆者の実体験に基づく実測値*

---

## 🎯 特徴

### ✅ 7フェーズ開発ライフサイクル
- 📋 **Phase 1**: 要件定義（15-30分）
- 💡 **Phase 2**: コンセプト設計（20-40分）  
- 📝 **Phase 3**: コンテキスト作成（45-90分）
- 🎨 **Phase 4**: ビジュアル開発（30-60分）
- 🔧 **Phase 5**: HTML生成（15-30分）
- ✅ **Phase 6**: 品質確認（20-45分）
- 🚀 **Phase 7**: デプロイ・公開（15分）

### ✅ 5つの専用HTML生成版
- 🏢 **General版**: 汎用プレゼンテーション
- 💻 **Technical版**: 技術発表・デモ
- 💼 **Business版**: ビジネス提案・報告
- 🎓 **Academic版**: 学術発表・論文紹介
- 📚 **Educational版**: 教育・研修

### ✅ 22種類のデザインサンプル
- Fluent Design、Material Design、Dark Mode
- Glassmorphism、Minimalist、Chalkboard
- 他16種類のプロフェッショナルデザイン

### ✅ 技術統合
- **Mermaid**: 図表・フローチャート
- **MathJax**: 数式・化学式
- **Chart.js**: データビジュアライゼーション
- **reveal.js**: 現代的なプレゼンテーション

### ✅ 開発方法の選択
- 🏠 **ローカルGit開発**: 個人・機密資料向け
- 🌐 **GitHub連携開発**: 共同・公開資料向け

---

## 🏁 クイックスタート

### 前提条件
- Windows 10/11 + WSL2
- VS Code + Remote-WSL拡張機能
- Claude Code for VSCode拡張機能
- Git & GitHub CLI（GitHub連携の場合）

### 🚀 3分で始める

```bash
# 1. プロジェクト作成（個人開発の場合）
mkdir my-presentation && cd my-presentation
git init

# 2. PrezenXテンプレートをクローン
git clone https://github.com/nahisaho/PresenX.git templates
cp -r templates/workflow .

# 3. VS Codeで開いてClaude Codeと開発開始
code .
```

詳細な環境構築は **[📖 環境構築ガイド](05-environment-setup.md)** をご覧ください。

---

## 📚 ドキュメント

### 📋 基本ドキュメント
| ドキュメント | 内容 | 対象読者 |
|:---:|:---:|:---:|
| [📊 エグゼクティブサマリー](01-executive-summary.md) | 価値提案・ROI分析 | 経営層・意思決定者 |
| [🎯 背景と課題](02-background-challenges.md) | 解決する課題 | 全ての利用者 |
| [🏗️ 技術アーキテクチャ](03-technical-architecture.md) | 技術的仕組み | 開発者・技術者 |
| [✨ 機能仕様](04-features-specifications.md) | 全機能の詳細 | 利用者・開発者 |
| [🛠️ 環境構築](05-environment-setup.md) | セットアップ手順 | 初回利用者 |
| [📋 実装方法論](06-implementation-methodology.md) | 開発手法・ワークフロー | 全ての利用者 |
| [📊 パフォーマンス評価](07-performance-evaluation.md) | 効果測定・実績 | 導入検討者 |
| [🌟 エピローグ](08-epilogue.md) | 将来展望・コミュニティ | 全ての利用者 |

### 🔄 ワークフロー
| フェーズ | 専用CLAUDE.md | 説明 |
|:---:|:---:|:---:|
| Phase 1 | [phase1-requirements-CLAUDE.md](workflow/phase1-requirements-CLAUDE.md) | 要件定義 |
| Phase 2 | [phase2-concept-CLAUDE.md](workflow/phase2-concept-CLAUDE.md) | コンセプト設計 |
| Phase 3 | [phase3-context-CLAUDE.md](workflow/phase3-context-CLAUDE.md) | コンテキスト作成 |
| Phase 4 | [phase4-visual-CLAUDE.md](workflow/phase4-visual-CLAUDE.md) | ビジュアル開発 |
| Phase 5 | [5つの専用版](workflow/#phase-5-html生成) | HTML生成（用途別特化） |
| Phase 6 | [phase6-quality-CLAUDE.md](workflow/phase6-quality-CLAUDE.md) | 品質確認 |
| Phase 7 | [phase7-deploy-CLAUDE.md](workflow/phase7-deploy-CLAUDE.md) | デプロイ・公開 |

詳細は **[📁 ワークフローガイド](workflow/README.md)** をご覧ください。

### 🎨 デザインサンプル
22種類のプロフェッショナルなデザインテンプレートから選択可能。詳細は **[🎨 デザインサンプル集](design_samples/README.md)** をご覧ください。

---

## 🌟 実績・効果

### 📊 筆者の実体験データ
- **作成時間**: 平均80.6%削減（18時間→3.5時間）
- **品質向上**: 総合満足度52.7%向上（59.2点→90.4点）
- **効率性**: 作成効率125%向上（40点→90点）

### 🎯 期待される効果
- ⏱️ **時間削減**: 従来手法の1/5の時間で完成
- 📈 **品質向上**: Claude Codeとの協働で論理性・説得力が向上
- 🔄 **継続改善**: Git履歴による組織的学習
- 💰 **ROI**: 1,000%以上の投資対効果

詳細は **[📊 パフォーマンス評価](07-performance-evaluation.md)** をご覧ください。

---

## 🎥 使用例

### 💼 ビジネスプレゼンテーション
```bash
# Business版で営業提案資料を作成
cp workflow/phase5-html-business-CLAUDE.md ./CLAUDE.md
# → KPIダッシュボード・ROI分析付きプレゼン
```

### 💻 技術発表
```bash
# Technical版で技術カンファレンス資料を作成
cp workflow/phase5-html-technical-CLAUDE.md ./CLAUDE.md
# → PWA・Web Components・ライブコーディング環境
```

### 🎓 学術発表
```bash
# Academic版で学会発表資料を作成
cp workflow/phase5-html-academic-CLAUDE.md ./CLAUDE.md
# → Citation.js・LaTeX数式・統計グラフ
```

---

## 🛠️ 技術仕様

### 💻 開発環境
- **エディタ**: VS Code + Remote-WSL
- **AI協働**: Claude Code for VSCode
- **バージョン管理**: Git / GitHub
- **プレゼン**: reveal.js + HTML5

### 🔧 技術統合
- **図表**: Mermaid.js
- **数式**: MathJax
- **グラフ**: Chart.js
- **デプロイ**: GitHub Pages
- **言語**: Markdown → HTML

### 📦 システム要件
- Windows 10/11 + WSL2
- VS Code (最新版)
- Node.js 18+
- Git 2.30+
- Modern Browser (Chrome/Firefox/Safari/Edge)

---

## 🤝 コントリビューション

PrezenXは継続的に改善されています。以下の方法で貢献できます：

### 📝 フィードバック
- [GitHub Issues](https://github.com/nahisaho/PresenX/issues) でバグ報告・機能要望
- [Discussions](https://github.com/nahisaho/PresenX/discussions) で使用例・改善提案

### 🔧 開発参加
```bash
# リポジトリをフォーク
gh repo fork nahisaho/PresenX

# 機能追加・改善
git checkout -b feature/new-design-template
# ... 開発作業 ...
git commit -m "新しいデザインテンプレートを追加"

# プルリクエスト作成
gh pr create --title "新しいデザインテンプレート" --body "..."
```

### 📚 ドキュメント改善
- 誤字・脱字の修正
- 使用例の追加
- 翻訳への協力

---

## 📜 ライセンス

[MIT License](LICENSE.txt) - 自由にご利用ください。

---

## 🔗 リンク

- **🌐 公式サイト**: https://nahisaho.github.io/PresenX/
- **📂 GitHub**: https://github.com/nahisaho/PresenX
- **🐛 バグ報告**: https://github.com/nahisaho/PresenX/issues
- **💬 ディスカッション**: https://github.com/nahisaho/PresenX/discussions
- **📖 Claude Code**: https://claude.ai/code

---

## 🙏 謝辞

PrezenXは以下の素晴らしいオープンソースプロジェクトの上に構築されています：

- [reveal.js](https://revealjs.com/) - モダンプレゼンテーションフレームワーク
- [Mermaid](https://mermaid.js.org/) - 図表生成ライブラリ
- [MathJax](https://www.mathjax.org/) - 数式表示エンジン
- [Chart.js](https://www.chartjs.org/) - データビジュアライゼーション
- [VS Code](https://code.visualstudio.com/) - 開発環境
- [Claude Code](https://claude.ai/code) - AI協働パートナー

---

**🎯 あなたの次のプレゼンテーションが、キャリアを変える転機になる**

PrezenXと共に、プレゼンテーションの新時代を切り開きませんか？

---

> **🤖 Generated with [Claude Code](https://claude.ai/code)**
> 
> **Co-Authored-By: Claude <noreply@anthropic.com>**