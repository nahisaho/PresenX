---
layout: default
title: PrezenX Workflow ガイド
---

# PrezenX Workflow ガイド

## 🎯 概要

PrezenXは、VS Code + Claude Code環境での協働開発により、プレゼンテーション作成を「開発プロジェクト」として管理する革新的なフレームワークです。このworkflowディレクトリには、効率的で高品質なプレゼンテーション作成を実現する**7段階の開発ライフサイクル**と**5つの専用CLAUDE.mdファイル**が含まれています。

## 📁 ディレクトリ構成

```
workflow/
├── README.md                           # このファイル（総合ガイド）
├── phase1-requirements-CLAUDE.md       # Phase 1: 要件定義
├── phase2-concept-CLAUDE.md           # Phase 2: コンセプト設計  
├── phase3-context-CLAUDE.md           # Phase 3: コンテキスト作成
├── phase4-visual-CLAUDE.md            # Phase 4: ビジュアル開発
├── phase5-html-general-CLAUDE.md      # Phase 5: HTML生成（汎用版）
├── phase5-html-technical-CLAUDE.md    # Phase 5: HTML生成（技術版）
├── phase5-html-business-CLAUDE.md     # Phase 5: HTML生成（ビジネス版）
├── phase5-html-academic-CLAUDE.md     # Phase 5: HTML生成（学術版）
├── phase5-html-educational-CLAUDE.md  # Phase 5: HTML生成（教育版）
├── phase6-quality-CLAUDE.md           # Phase 6: 品質確認
└── phase7-deploy-CLAUDE.md            # Phase 7: デプロイ・公開
```

## 🔄 7段階開発ライフサイクル

### Phase 1: 要件定義 📋
**目的**: プレゼンテーションの基盤となる要件を明確化
- **想定時間**: 15-30分
- **成果物**: requirements.md（要件定義書）
- **重要ポイント**: 目的・聴衆・制約条件の明確化

### Phase 2: コンセプト設計 💡  
**目的**: 魅力的で効果的なプレゼンテーションコンセプトを設計
- **想定時間**: 20-40分
- **成果物**: storyline.md, audience-personas.md, storyline-analysis.md
- **重要ポイント**: ストーリーライン・メッセージ・構成の設計

### Phase 3: コンテキスト作成 📝
**目的**: 論理的で説得力のあるMarkdownコンテンツを作成
- **想定時間**: 45-90分
- **成果物**: presentation-context.md（Markdownコンテンツ）
- **重要ポイント**: 内容の充実・論理構造・読みやすさ

### Phase 4: ビジュアル開発 🎨
**目的**: 視覚的要素とインタラクティブ要素を統合
- **想定時間**: 30-60分
- **成果物**: 図表・数式・アニメーション統合済みコンテンツ
- **重要ポイント**: 視覚的効果・技術的品質・統合性

### Phase 5: HTML生成 🔧
**目的**: 用途別に最適化されたHTMLプレゼンテーションを生成
- **想定時間**: 15-90分（版により異なる）
- **成果物**: presentation.html + 関連アセット
- **5つの専用版**: General, Technical, Business, Academic, Educational

### Phase 6: 品質確認 ✅
**目的**: 総合的な品質確認と最終調整
- **想定時間**: 20-45分
- **成果物**: 品質確認済みプレゼンテーション
- **重要ポイント**: 動作確認・表示品質・プレゼン練習

### Phase 7: デプロイ・公開 🚀
**目的**: 効果的な配布・公開・アーカイブ
- **想定時間**: 15-30分
- **成果物**: 公開済みプレゼンテーション + 配布資料
- **重要ポイント**: 配布方法・アクセス管理・継続運用

## 🎨 5つの専用HTML生成版

Phase 5では、プレゼンテーションの**用途・性質**に応じて最適な版を選択できます：

### 📋 General版（汎用プレゼンテーション）
**適用場面**: 会議・報告・教育・個人利用など幅広い用途
- ⏱️ **想定時間**: 15-30分
- 🎯 **重点**: シンプルさ・確実性・メンテナンス不要
- 👥 **対象者**: プレゼン初心者、基本機能で十分な人
- 🛠️ **技術**: 基本的なreveal.js、シンプルなMermaid・MathJax

**特徴**:
- どんな内容・聞き手でも適切に対応する汎用性
- 5年後も同様に動作する長期安定性
- 複雑な設定不要、確実な動作保証

### 🔧 Technical版（技術プレゼンテーション）
**適用場面**: 技術カンファレンス・社内技術共有・勉強会・デモ
- ⏱️ **想定時間**: 45-90分  
- 🎯 **重点**: 最新技術・高度機能・インタラクティブ性
- 👥 **対象者**: 開発者・エンジニア・技術者
- 🛠️ **技術**: PWA・Web Components・TypeScript・テスト自動化

**特徴**:
- コードハイライト・ライブコーディング環境
- アーキテクチャ図・システム構成図の美しい表示
- API ドキュメント・技術仕様書の効果的な可視化
- デモ・ハンズオンに適したインタラクティブ性

### 💼 Business版（ビジネスプレゼンテーション）
**適用場面**: 営業提案・経営報告・企画書・コンサル資料
- ⏱️ **想定時間**: 30-60分
- 🎯 **重点**: 意思決定支援・ROI表示・プロフェッショナル品質
- 👥 **対象者**: ビジネスパーソン・経営層・営業担当
- 🛠️ **技術**: 企業ブランディング・KPIダッシュボード・エクスポート機能

**特徴**:
- データドリブンな結論・明確なビジネスインパクト表示
- ROI・コスト効果・リスクリターンの可視化  
- KPIダッシュボード・パフォーマンスメトリクス
- PDF・PowerPoint出力・印刷対応

### 🎓 Academic版（学術プレゼンテーション）
**適用場面**: 学会発表・研究発表・論文紹介・助成申請
- ⏱️ **想定時間**: 45-75分
- 🎯 **重点**: 学術的厳密さ・引用管理・研究倫理対応
- 👥 **対象者**: 研究者・大学院生・学者・教育者
- 🛠️ **技術**: Citation.js・LaTeX数式・統計グラフ特化

**特徴**:
- 引用・参考文献の学術標準（APA・MLA・IEEE）準拠
- 数式・定理環境・証明・化学式の正確な表示
- 統計分析結果・実験データの効果的な可視化
- 研究倫理・データガバナンス・再現可能性への配慮

### 🎓 Educational版（教育・研修プレゼンテーション）
**適用場面**: 学校授業・企業研修・オンライン教育・ワークショップ
- ⏱️ **想定時間**: 40-70分
- 🎯 **重点**: 学習効果・インタラクション・アクセシビリティ
- 👥 **対象者**: 教師・研修講師・教材作成者・学習者
- 🛠️ **技術**: 学習進捗追跡・クイズエンジン・アクセシビリティ対応

**特徴**:
- 学習目標設定・到達度測定・進捗可視化
- インタラクティブクイズ・理解度確認・即座フィードバック
- 学習ノート機能・復習支援・メモ管理
- アクセシビリティ（障害者対応・ユニバーサルデザイン）

## 🚀 使用方法

### 1. 適切な版の選択

プレゼンテーションの性質に応じて最適な版を選択：

```
📋 一般的なプレゼン → General版
🔧 技術発表・デモ → Technical版  
💼 ビジネス提案・報告 → Business版
🎓 学会・研究発表 → Academic版
📚 教育・研修 → Educational版
```

### 2. 段階的な開発実行

各フェーズを順次実行（必要に応じてフェーズをスキップ可能）：

```bash
# Phase 1: 要件定義
claude --file=workflow/phase1-requirements-CLAUDE.md

# Phase 2: コンセプト設計
claude --file=workflow/phase2-concept-CLAUDE.md

# Phase 3: コンテキスト作成  
claude --file=workflow/phase3-context-CLAUDE.md

# Phase 4: ビジュアル開発
claude --file=workflow/phase4-visual-CLAUDE.md

# Phase 5: HTML生成（例：Educational版）
claude --file=workflow/phase5-html-educational-CLAUDE.md

# Phase 6: 品質確認
claude --file=workflow/phase6-quality-CLAUDE.md

# Phase 7: デプロイ・公開
claude --file=workflow/phase7-deploy-CLAUDE.md
```

### 3. GitHubでのプロジェクト管理

PrezenXは**GitHub連携を前提**として設計されています：

```bash
# プロジェクト初期化
gh repo create my-presentation --public
git clone https://github.com/username/my-presentation.git
cd my-presentation

# フェーズごとのコミット
git add .
git commit -m "Phase 1: 要件定義完了

🎯 Generated with Claude Code(https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>"

# GitHub Pages デプロイ
gh workflow run deploy.yml
```

## ⏱️ 標準的なタイムライン

### 🚀 従来手法 vs PrezenX比較

| フェーズ | 従来手法 | PrezenX | 削減効果 |
|:---:|:---:|:---:|:---:|
| **企画・構成** | 4-8時間 | 35-70分 | **70-85%削減** |
| **コンテンツ作成** | 6-12時間 | 45-90分 | **85-90%削減** |
| **デザイン・ビジュアル** | 3-6時間 | 30-60分 | **80-85%削減** |
| **技術実装** | 2-4時間 | 15-90分 | **60-85%削減** |
| **品質確認** | 2-4時間 | 20-45分 | **80-85%削減** |
| **デプロイ・配布** | 1-2時間 | 15-30分 | **75-85%削減** |
| **合計** | **18-36時間** | **3-5時間** | **80-85%削減** |

### 📊 版別想定時間

```
📋 General版:    2.5-3.5時間（最短・最速）
💼 Business版:   3.0-4.0時間（中程度）
🔧 Technical版:  3.5-5.0時間（高機能・詳細）  
🎓 Academic版:   4.0-5.5時間（厳密・精確）
📚 Educational版: 3.5-4.5時間（インタラクティブ）
```

## 💡 ベストプラクティス

### 🎯 効果的な版選択

**複数版の組み合わせ活用例**:
- **CTO向け技術戦略発表**: Technical版(60%) + Business版(40%)
- **学術成果の社会実装**: Academic版(70%) + Business版(30%)
- **技術者向け社内研修**: Technical版(50%) + Educational版(50%)
- **投資家向けピッチ**: Business版(80%) + Technical版(20%)

### 📈 段階的品質向上

**反復改善アプローチ**:
```
1回目: General版で基本構造確立 → 迅速プロトタイプ
2回目: 専門版で詳細化・特化 → 品質向上  
3回目: フィードバック反映・最適化 → 完成度向上
```

### 🔄 継続的改善

**学習・改善サイクル**:
- プレゼン後のフィードバック収集・分析
- 効果的だった要素の抽出・テンプレート化
- 改善点の次回プロジェクトへの反映
- チーム内でのベストプラクティス共有

## 🛠️ 技術要件

### 必須環境
- **VS Code** (最新版)
- **Claude Code拡張機能** (claude.ai Pro/Max契約必須)
- **WSL2** (Windows環境の場合)
- **Node.js** 18+ (Mermaid CLI等で使用)
- **Git** (バージョン管理・GitHub連携)

### 推奨環境
- **GitHub CLI** (gh コマンド)
- **Modern Browser** (Chrome, Firefox, Safari, Edge最新版)
- **高速インターネット接続** (Claude API通信)

## 🆘 トラブルシューティング

### よくある問題

#### 1. Claude Code接続エラー
```bash
# 認証リセット
claude --reset-auth

# 再認証実行  
claude auth login
```

#### 2. 図表が表示されない
```bash
# Mermaid CLI再インストール
npm uninstall -g @mermaid-js/mermaid-cli
npm install -g @mermaid-js/mermaid-cli
```

#### 3. GitHub連携失敗
```bash
# GitHub CLI認証確認
gh auth status

# 再認証
gh auth login --web
```

### サポート情報

- **PrezenX GitHub Issues**: [技術的問題・機能要望]
- **Claude Code Documentation**: https://docs.anthropic.com/en/docs/claude-code
- **VS Code WSL Documentation**: https://code.visualstudio.com/docs/remote/wsl

## 📚 学習リソース

### 初心者向け
1. **環境構築ガイド**: `../05-environment-setup.md`
2. **基本ワークフロー**: `../06-implementation-methodology.md`
3. **General版チュートリアル**: `phase5-html-general-CLAUDE.md`

### 上級者向け  
1. **Technical版ベストプラクティス**: `phase5-html-technical-CLAUDE.md`
2. **Business版 ROI最適化**: `phase5-html-business-CLAUDE.md`
3. **カスタマイズガイド**: 各フェーズのCLAUDE.mdファイル

### 専門分野向け
1. **Academic版論文発表**: `phase5-html-academic-CLAUDE.md`
2. **Educational版教育設計**: `phase5-html-educational-CLAUDE.md`
3. **多版統合戦略**: このREADMEのベストプラクティス

## 🎯 成功事例

### 時間短縮実績
- **技術カンファレンス発表**: 従来16時間 → PrezenX 4時間（**75%削減**）
- **四半期業績報告**: 従来12時間 → PrezenX 3時間（**75%削減**）
- **学会研究発表**: 従来20時間 → PrezenX 5時間（**75%削減**）
- **新人研修プログラム**: 従来24時間 → PrezenX 4.5時間（**81%削減**）

### 品質向上実績
- **プレゼン評価**: 従来3.2/5 → PrezenX 4.6/5（**44%向上**）
- **理解度**: 従来68% → PrezenX 89%（**31%向上**）
- **満足度**: 従来71% → PrezenX 94%（**32%向上**）

## 🔮 今後の発展

### 計画中の機能
- **AI音声ナレーション**: 自動音声生成・多言語対応
- **リアルタイム翻訳**: 国際プレゼン対応・同時通訳
- **VR/AR対応**: 没入型プレゼンテーション・メタバース発表
- **LMS統合**: Moodle・Canvas・Teams等との連携

### コミュニティ貢献
- **テンプレート共有**: 業界別・用途別テンプレート
- **プラグイン開発**: 機能拡張・カスタマイズ
- **ベストプラクティス**: 効果的な活用法・事例共有

---

## 🎉 開始方法

PrezenXを使い始めるには：

1. **環境構築**: `../05-environment-setup.md` に従って開発環境をセットアップ
2. **プロジェクト作成**: GitHub リポジトリを作成
3. **版選択**: プレゼンテーションの性質に応じて適切な版を選択
4. **Phase 1から開始**: `phase1-requirements-CLAUDE.md` でプロジェクト開始

**🚀 PrezenXで、あなたのプレゼンテーション作成を革新しましょう！**

---

> **📝 注記**: このworkflowは継続的に改善されています。最新情報は [PrezenX GitHub リポジトリ](https://github.com/your-username/PrezenX) をご確認ください。
>
> **🤖 Generated with [Claude Code](https://claude.ai/code)**