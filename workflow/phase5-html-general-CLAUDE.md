---
layout: default
title: "Phase 5: HTML生成（General版）"
---

# CLAUDE.md - Phase 5: HTML生成（General版）

## 🎯 フェーズ概要

**フェーズ名**: HTML生成（汎用版）
**目的**: どんな種類のプレゼンテーションでも確実に美しく表示できるHTMLを生成する
**想定時間**: 15-30分
**成果物**: presentation.html（汎用的で使いやすいプレゼンテーション）
**対象者**: 
- 一般的なプレゼンテーション（会議・報告・説明）
- プレゼン初心者・ITに不慣れな人
- 確実性・安定性を重視する人
- 複雑な機能は不要な人

## 🌟 General版の特徴

### 🎨 汎用プレゼンテーションに最適化

**適用場面**:
- **会議・報告**: 部署会議、進捗報告、業務説明
- **教育・研修**: 社内研修、説明会、マニュアル説明
- **一般発表**: イベント、セミナー、プロジェクト発表
- **個人利用**: 趣味、学習発表、家族向け

**基本方針**:
- **見た目の美しさ**: 誰が見ても「きれい」と感じるデザイン
- **操作の簡単さ**: 複雑な機能は排除、基本操作のみ
- **確実な動作**: どの環境でも確実に表示される
- **メンテナンス不要**: 一度作れば長期間使用可能

### 📱 対応環境・ブラウザ

**完全対応**:
- **デスクトップ**: Windows, Mac, Linux
- **ブラウザ**: Chrome, Firefox, Safari, Edge（最新版）
- **モバイル**: iPhone, Android（基本的な表示のみ）
- **プロジェクター**: 1920x1080, 4:3比率

## 🏗️ HTML生成プロセス

### Step 1: 基本HTMLテンプレート

#### シンプルなreveal.js設定

**base.html**:
```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>[プレゼンテーションタイトル]</title>
    
    <!-- reveal.js（シンプル版） -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@4.3.1/dist/reveal.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@4.3.1/dist/theme/white.css">
    
    <!-- 基本的な数式表示 -->
    <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
    
    <!-- 基本図表 -->
    <script src="https://cdn.jsdelivr.net/npm/mermaid@9.4.3/dist/mermaid.min.js"></script>
    
    <!-- カスタムスタイル -->
    <style>
        /* シンプルで読みやすいスタイル */
        .reveal .slides section {
            text-align: left;
            font-family: 'Arial', 'Helvetica', sans-serif;
            line-height: 1.6;
        }
        
        .reveal h1, .reveal h2, .reveal h3 {
            color: #2c5282;
            text-transform: none;
            margin-bottom: 0.5em;
        }
        
        .reveal h1 { font-size: 2.5em; }
        .reveal h2 { font-size: 2em; }
        .reveal h3 { font-size: 1.5em; }
        
        /* 表の基本スタイル */
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            font-size: 0.9em;
        }
        
        table th {
            background-color: #2c5282;
            color: white;
            padding: 12px;
            text-align: center;
            font-weight: bold;
        }
        
        table td {
            padding: 10px;
            border: 1px solid #ddd;
            text-align: left;
        }
        
        table tr:nth-child(even) {
            background-color: #f8f9fa;
        }
        
        /* 強調表示 */
        .highlight {
            background-color: #fff3cd;
            padding: 2px 6px;
            border-radius: 4px;
            font-weight: bold;
        }
        
        .important {
            color: #dc3545;
            font-weight: bold;
        }
        
        .success {
            color: #28a745;
            font-weight: bold;
        }
        
        /* リストの見た目改善 */
        .reveal ul, .reveal ol {
            margin-left: 1em;
        }
        
        .reveal li {
            margin-bottom: 0.5em;
        }
        
        /* 図表の中央寄せ */
        .mermaid {
            text-align: center;
            margin: 20px 0;
        }
        
        /* プレゼン時の見やすさ重視 */
        .reveal .slides section {
            font-size: 1.2em;
        }
        
        /* スライド全体の余白設定 */
        .reveal .slides {
            width: 80%;
            margin: 10%;
        }
        
        @media (max-width: 768px) {
            .reveal .slides section {
                font-size: 1em;
                padding: 15px;
            }
            
            table {
                font-size: 0.8em;
            }
        }
    </style>
</head>
<body>
    <div class="reveal">
        <div class="slides">
            <!-- スライド内容がここに挿入されます -->
        </div>
    </div>
    
    <script src="https://cdn.jsdelivr.net/npm/reveal.js@4.3.1/dist/reveal.js"></script>
    <script>
        // シンプルなreveal.js設定
        Reveal.initialize({
            hash: true,
            controls: true,
            progress: true,
            center: false,
            transition: 'slide',
            transitionSpeed: 'default',
            
            // 発表者に優しい設定
            keyboard: true,
            overview: true,
            loop: false,
            shuffle: false,
            
            // MathJax設定
            math: {
                mathjax: 'https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js',
                config: 'TeX-AMS_HTML-full'
            },
            
            plugins: [ RevealMath ]
        });
        
        // Mermaidの基本設定
        mermaid.initialize({
            startOnLoad: true,
            theme: 'default',
            themeVariables: {
                primaryColor: '#2c5282',
                primaryTextColor: '#ffffff',
                primaryBorderColor: '#2c5282',
                lineColor: '#333333',
                sectionBkColor: '#f8f9fa',
                altSectionBkColor: '#ffffff',
                gridColor: '#cccccc'
            }
        });
        
        // 数式の設定
        window.MathJax = {
            tex: {
                inlineMath: [['$', '$'], ['\\(', '\\)']],
                displayMath: [['$$', '$$'], ['\\[', '\\]']]
            },
            chtml: {
                scale: 1.1,
                minScale: 0.8
            }
        };
    </script>
</body>
</html>
```

### Step 2: 汎用スライド構造の生成

#### 汎用プレゼンテーション向けスライドパターン

**1. タイトルスライド（どんなプレゼンでも使える）**:
```html
<section>
    <h1>[プレゼンテーションタイトル]</h1>
    <h3>[サブタイトル・目的]</h3>
    <p>
        <strong>[発表者名]</strong><br>
        [所属・部署]<br>
        [日付・場所]
    </p>
</section>
```

**2. 通常のコンテンツスライド**:
```html
<section>
    <h2>[セクションタイトル]</h2>
    <ul>
        <li>ポイント1</li>
        <li>ポイント2</li>
        <li>ポイント3</li>
    </ul>
</section>
```

**3. 表組みスライド**:
```html
<section>
    <h2>[表のタイトル]</h2>
    <table>
        <thead>
            <tr>
                <th>項目</th>
                <th>値</th>
                <th>説明</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>項目1</td>
                <td><span class="success">○</span></td>
                <td>説明文</td>
            </tr>
        </tbody>
    </table>
</section>
```

**4. 図表スライド**:
```html
<section>
    <h2>[図表タイトル]</h2>
    <div class="mermaid">
        graph TD
            A[開始] --> B[処理]
            B --> C[終了]
    </div>
</section>
```

### Step 3: よく使うパターンの実装

#### 強調表示のパターン

```html
<!-- 重要ポイントの強調 -->
<p>通常のテキストですが、<span class="highlight">ここは重要</span>なポイントです。</p>

<!-- 成功・警告の表示 -->
<p><span class="success">✓ 成功例</span></p>
<p><span class="important">⚠ 注意点</span></p>

<!-- 番号付きのポイント -->
<ol>
    <li><strong>第一のポイント</strong>: 説明文</li>
    <li><strong>第二のポイント</strong>: 説明文</li>
    <li><strong>第三のポイント</strong>: 説明文</li>
</ol>
```

#### 簡単な数式表示

```html
<!-- インライン数式 -->
<p>利益率は $\frac{売上 - 費用}{売上} \times 100$ で計算されます。</p>

<!-- 独立した数式 -->
<p>二次方程式の解は次の公式で求められます：</p>
$$x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$$
```

#### 基本的なMermaid図表

```html
<!-- フローチャート -->
<div class="mermaid">
graph TD
    A[問題発見] --> B[原因分析]
    B --> C[解決策検討]
    C --> D[実行]
    D --> E[結果評価]
</div>

<!-- 組織図 -->
<div class="mermaid">
graph TD
    A[社長] --> B[営業部]
    A --> C[技術部]
    A --> D[管理部]
    B --> E[営業1課]
    B --> F[営業2課]
</div>

<!-- ガントチャート -->
<div class="mermaid">
gantt
    title プロジェクトスケジュール
    dateFormat  YYYY-MM-DD
    section フェーズ1
    要件定義     :2024-01-01, 30d
    設計         :2024-01-15, 45d
    section フェーズ2
    開発         :2024-02-15, 60d
    テスト       :2024-04-01, 30d
</div>
```

## 🗣️ Claude Code協働方針

### このフェーズでClaude Codeに期待すること

1. **汎用性の確保**
   - どんな内容でも適切に表示できるHTML生成
   - 業種・分野を問わない汎用的なデザイン
   - 初心者でも迷わない分かりやすい構造

2. **確実性の重視**
   - 100%確実に動作するコードの提供
   - 環境依存のリスクを排除
   - 長期間安定して使用可能な技術選択

3. **使いやすさの最優先**
   - 専門知識不要で操作可能
   - 直感的でわかりやすいインターフェース
   - トラブル時の自己解決可能なサポート

### 積極的に相談したいポイント

- [ ] 「どんなプレゼン内容でも適切に表示できるか？」
- [ ] 「初心者でも迷わず使えるか？」
- [ ] 「会議室・教室・講演会場で見やすいか？」
- [ ] 「5年後も同じように動作するか？」
- [ ] 「緊急時にも確実に表示されるか？」

## 🔧 品質保証チェック

### 基本動作確認

**表示確認**:
- [ ] 全スライドが正常に表示される
- [ ] 文字が読みやすいサイズで表示される
- [ ] 表組みが整理されて表示される
- [ ] 図表が適切に表示される
- [ ] 数式が正しく表示される

**操作確認**:
- [ ] キーボードの矢印キーでスライド移動できる
- [ ] マウスクリックでスライド移動できる
- [ ] タッチ操作（スマートフォン）でスライド移動できる
- [ ] フルスクリーン表示が可能
- [ ] 概要表示（ESCキー）が機能する

### ブラウザ互換性

**主要ブラウザでの確認**:
- [ ] Google Chrome（最新版）
- [ ] Mozilla Firefox（最新版）
- [ ] Microsoft Edge（最新版）
- [ ] Safari（Mac）

**古いブラウザでの基本動作**:
- [ ] Internet Explorer 11（可能な範囲で）
- [ ] 古いバージョンのSafari
- [ ] 古いバージョンのAndroid標準ブラウザ

### 発表環境対応

**プロジェクター・大画面対応**:
- [ ] 1920x1080解像度で正常表示
- [ ] 4:3比率（1024x768）で正常表示
- [ ] 明るい環境での視認性確保
- [ ] 遠距離からの文字の読みやすさ

**印刷対応**:
- [ ] ブラウザの印刷機能で適切にレイアウト
- [ ] 1ページに1スライドで印刷可能
- [ ] 白黒印刷でも内容が判読可能

## 📁 ファイル構成

### シンプルな構成

```
presentation/
├── index.html              # メインファイル（これだけで完結）
├── README.txt              # 使用方法（テキスト形式）
└── backup/
    ├── presentation.pdf    # PDF版（印刷用）
    └── slides.pptx         # PowerPoint版（バックアップ）
```

### README.txt の内容

```
プレゼンテーション使用方法

【基本操作】
- 右矢印キー または スペースキー: 次のスライド
- 左矢印キー: 前のスライド
- ESCキー: 全体表示
- Fキー: フルスクリーン

【推奨ブラウザ】
- Google Chrome（最新版）
- Microsoft Edge（最新版）
- Mozilla Firefox（最新版）

【トラブル対応】
1. スライドが表示されない
   → ブラウザを最新版に更新してください
   → インターネット接続を確認してください

2. 図表が表示されない
   → 5-10秒お待ちください（読み込み中）
   → ページを再読み込み（F5キー）してください

3. 数式が表示されない
   → ページを再読み込み（F5キー）してください
   → 数秒お待ちください

【発表時の注意点】
- 発表前に必ず表示テストを行ってください
- プロジェクターの解像度設定を確認してください
- backup/フォルダのPDF版も準備してください

【問い合わせ】
技術的な問題が発生した場合は、[連絡先]までご連絡ください。
```

## ✅ HTML生成完了チェックリスト

### Claude Codeとの協働確認
- [ ] HTMLコードがシンプルで理解しやすい
- [ ] すべての機能が基本的で確実に動作する
- [ ] エラーメッセージがわかりやすい
- [ ] ファイル構成が整理されている

### 発表者による確認
- [ ] 見た目が美しく、プロフェッショナル
- [ ] 操作が簡単で直感的
- [ ] 発表の流れがスムーズ
- [ ] バックアップ手段が準備されている

### 技術的最終確認
- [ ] すべてのブラウザで表示確認完了
- [ ] プロジェクター環境でのテスト完了
- [ ] 印刷レイアウト確認完了
- [ ] モバイル端末での基本表示確認完了

## 🎯 General版の利点

### 🌟 汎用プレゼンテーションに最適

**どんな用途でも対応**:
- 業種・分野を問わない汎用デザイン
- 会議から講演まで幅広く対応
- 内容の種類に依存しない構造
- 聞き手を選ばない読みやすさ

**初心者に優しい**:
- 複雑な設定が不要
- わかりやすい操作方法
- 確実に動作する安心感
- 豊富なサポート情報

**長期利用可能**:
- 標準的な技術のみ使用
- ブラウザの更新に左右されにくい
- メンテナンスが不要
- 将来的な互換性確保

### 💼 実用性重視

**発表での安心感**:
- 技術トラブルのリスク最小
- どの環境でも確実に表示
- バックアップ手段の充実
- プロフェッショナルな見た目

**コストパフォーマンス**:
- 短時間での作成可能
- 追加ツールが不要
- 学習コストが少ない
- 高い再利用性

## 🚀 次フェーズへの申し送り

### Phase 6（品質確認）への重要事項
- **完成HTML**: index.html（単一ファイル構成）
- **動作要件**: モダンブラウザ + インターネット接続
- **操作ガイド**: README.txtファイル
- **バックアップ**: PDF版・PowerPoint版

### 特記事項
- **安定性重視**: 複雑な機能は排除、基本機能に特化
- **互換性確保**: 幅広いブラウザ・環境での動作確認済み
- **使いやすさ**: 初心者でも迷わない操作性
- **プロ品質**: シンプルだが美しいデザイン

---

**📝 General版のコンセプト**:
「汎用性と確実性を両立した、あらゆるプレゼンテーションに対応できるスタンダード」
どんな内容・用途・聞き手でも適切に対応でき、誰でも確実に使える高品質なプレゼンテーションを目指します。

**🤖 Claude Codeへの指示**:
このGeneral版では、「汎用性」「確実性」「使いやすさ」を最優先してください。特定の分野に偏らず、どんなプレゼンテーションでも美しく表示でき、初心者でも安心して使用できるスタンダードな品質を確保してください。