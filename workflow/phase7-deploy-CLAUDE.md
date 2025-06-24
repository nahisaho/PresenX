# CLAUDE.md - Phase 7: デプロイ・公開

## 🎯 フェーズ概要

**フェーズ名**: デプロイ・公開
**目的**: 品質確認済みのプレゼンテーションを本番環境にデプロイし、発表・公開・共有を実現する
**想定時間**: 15分
**成果物**: 公開URL、共有可能プレゼンテーション、発表後のフィードバック収集

## 🚀 デプロイ要件

### Phase 6からの引き継ぎ情報

**品質確認済み成果物**:
- **品質評価結果**: [総合スコア87点、発表可能レベル]
- **最終版プレゼンテーション**: [index.html + assets/]
- **技術仕様**: [オフライン対応、ブラウザ互換性確認済み]
- **発表準備**: [チェックリスト、トラブル対応手順]

### デプロイ方針

**多段階デプロイ戦略**:
1. **GitHub Pages**: メイン公開環境
2. **ローカル環境**: 発表当日のバックアップ
3. **配布版**: PDF・PowerPoint形式での共有
4. **アーカイブ**: 長期保存・再利用版

## 🔧 デプロイプロセス

### Step 1: GitHub Pages デプロイ

#### リポジトリ準備

**GitHubリポジトリ構成**:
```
presentation-repo/
├── index.html              # メインプレゼンテーション
├── assets/
│   ├── css/custom.css      # カスタムスタイル
│   ├── js/presentation.js  # プレゼンテーション制御
│   └── data/               # データファイル
├── docs/
│   ├── speaker-notes.html  # 発表者ノート
│   └── README.md           # 使用方法・技術仕様
├── backup/
│   ├── presentation.pdf    # PDFバックアップ
│   └── presentation.pptx   # PowerPointバックアップ
└── .github/
    └── workflows/
        └── deploy.yml      # 自動デプロイ設定
```

#### 自動デプロイ設定

**.github/workflows/deploy.yml**:
```yaml
name: Deploy Presentation to GitHub Pages

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    
    steps:
    - name: Checkout Repository
      uses: actions/checkout@v3
      
    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'
        
    - name: Install Dependencies
      run: |
        npm install -g @mermaid-js/mermaid-cli
        npm install -g html-minifier
        
    - name: Optimize Assets
      run: |
        # HTMLの最適化
        html-minifier --collapse-whitespace --remove-comments --minify-css --minify-js index.html -o index.min.html
        mv index.min.html index.html
        
        # CSSの最適化
        find assets/css -name "*.css" -exec sed -i 's/\/\*.*\*\///g' {} \;
        
    - name: Deploy to GitHub Pages
      uses: peaceiris/actions-gh-pages@v3
      if: github.ref == 'refs/heads/main'
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./
        cname: your-domain.com  # カスタムドメインがある場合
        
    - name: Notify Deployment Success
      run: |
        echo "Presentation deployed successfully!"
        echo "URL: https://username.github.io/repository-name/"
```

#### カスタムドメイン設定（オプション）

**CNAME設定**:
```
# CNAMEファイル
presentation.your-company.com
```

**DNS設定例**:
```
# DNSレコード設定
presentation.your-company.com CNAME username.github.io
```

### Step 2: ローカル環境準備

#### 発表当日用のオフライン版

**offline-setup.sh**:
```bash
#!/bin/bash
# オフライン版セットアップスクリプト

echo "PrezenX オフライン版準備中..."

# 依存ライブラリをローカルにダウンロード
mkdir -p assets/lib

# reveal.js
curl -o assets/lib/reveal.min.js https://cdn.jsdelivr.net/npm/reveal.js@4.3.1/dist/reveal.min.js
curl -o assets/lib/reveal.min.css https://cdn.jsdelivr.net/npm/reveal.js@4.3.1/dist/reveal.min.css

# MathJax
curl -o assets/lib/mathjax.min.js https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.min.js

# Chart.js
curl -o assets/lib/chart.min.js https://cdn.jsdelivr.net/npm/chart.js@3.9.1/dist/chart.min.js

# Mermaid
curl -o assets/lib/mermaid.min.js https://cdn.jsdelivr.net/npm/mermaid@9.4.3/dist/mermaid.min.js

# HTMLファイルのCDNリンクをローカルリンクに変更
sed -i 's|https://cdn.jsdelivr.net/npm/reveal.js@4.3.1/dist/reveal.js|assets/lib/reveal.min.js|g' index.html
sed -i 's|https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js|assets/lib/mathjax.min.js|g' index.html
sed -i 's|https://cdn.jsdelivr.net/npm/chart.js@3.9.1/dist/chart.min.js|assets/lib/chart.min.js|g' index.html
sed -i 's|https://cdn.jsdelivr.net/npm/mermaid@9.4.3/dist/mermaid.min.js|assets/lib/mermaid.min.js|g' index.html

echo "オフライン版準備完了!"
echo "ローカルサーバー起動中..."

# ローカルサーバー起動
python3 -m http.server 8000
```

#### 発表者用チェックリスト

**presentation-checklist.md**:
```markdown
# 発表当日チェックリスト

## ⏰ 発表30分前
- [ ] プロジェクター接続確認
- [ ] 音響設備確認（必要に応じて）
- [ ] インターネット接続確認
- [ ] バックアップUSB準備確認

## ⏰ 発表15分前
- [ ] プレゼンテーション表示確認
- [ ] スライド切り替え動作確認
- [ ] 図表・グラフ表示確認
- [ ] 数式レンダリング確認

## ⏰ 発表5分前
- [ ] フルスクリーンモード設定
- [ ] 発表者ノート画面準備
- [ ] タイマー・時計確認
- [ ] 緊急時対応手順確認

## 🆘 トラブル時の対応
### インターネット接続不良
1. オフライン版への切り替え（assets/lib使用）
2. USBバックアップからの起動
3. PDF版での代替発表

### プロジェクター表示問題
1. 解像度設定の調整
2. カラープロファイル調整
3. HDMIケーブル交換
4. 代替表示デバイス使用

### ソフトウェア動作不良
1. ブラウザの再起動
2. 代替ブラウザでの表示
3. PDF版での発表継続
4. PowerPoint版への切り替え
```

### Step 3: 配布版作成

#### PDF版生成

**generate-pdf.js**:
```javascript
// Puppeteerを使用したPDF生成スクリプト
const puppeteer = require('puppeteer');

async function generatePDF() {
    const browser = await puppeteer.launch();
    const page = await browser.newPage();
    
    // プレゼンテーションを読み込み
    await page.goto('http://localhost:8000/index.html', {
        waitUntil: 'networkidle2'
    });
    
    // PDF生成設定
    const pdf = await page.pdf({
        format: 'A4',
        landscape: true,
        printBackground: true,
        margin: {
            top: '20px',
            bottom: '20px',
            left: '20px',
            right: '20px'
        }
    });
    
    await browser.close();
    return pdf;
}

// 実行
generatePDF().then(pdf => {
    require('fs').writeFileSync('backup/presentation.pdf', pdf);
    console.log('PDF生成完了: backup/presentation.pdf');
});
```

#### PowerPoint版変換

**markdown-to-pptx.js**:
```javascript
// Markdownからhopefully readable PowerPoint形式への変換
const fs = require('fs');
const pptxgen = require('pptxgenjs');

function convertToPowerPoint() {
    const pptx = new pptxgen();
    
    // スライド1: タイトル
    const slide1 = pptx.addSlide();
    slide1.addText("プレゼンテーションタイトル", {
        x: 1, y: 1, w: 8, h: 1,
        fontSize: 32, bold: true, color: '1976d2'
    });
    
    // 他のスライドも同様に追加...
    
    // PowerPoint保存
    pptx.writeFile('backup/presentation.pptx');
    console.log('PowerPoint版生成完了: backup/presentation.pptx');
}

convertToPowerPoint();
```

### Step 4: 共有・アクセス管理

#### アクセス制御設定

**access-control.yml**:
```yaml
# GitHub Pages アクセス制御設定
access_control:
  public: true  # 一般公開する場合
  
  # 限定公開の場合
  private_access:
    - username1@company.com
    - username2@company.com
    
  # 組織内限定の場合
  organization_only: true
  
# SEO設定
seo:
  title: "プレゼンテーションタイトル - 会社名"
  description: "効果的なシステム自動化による業務効率化提案"
  keywords: "自動化, 効率化, ROI, コスト削減"
  robots: "noindex, nofollow"  # 検索エンジン非表示
```

#### 共有URL生成

**sharing-urls.md**:
```markdown
# PrezenX プレゼンテーション共有情報

## 🌐 アクセスURL
- **メインURL**: https://username.github.io/presentation-repo/
- **発表者ノート**: https://username.github.io/presentation-repo/docs/speaker-notes.html
- **モバイル版**: https://username.github.io/presentation-repo/?mobile=true

## 📱 QRコード共有
[QRコード画像を生成・挿入]

## 📧 メール共有テンプレート
件名: プレゼンテーション資料共有 - [タイトル]

いつもお世話になっております。

本日のプレゼンテーション資料を共有いたします。

🌐 オンライン版: https://username.github.io/presentation-repo/
📄 PDF版: [添付ファイル]
📊 PowerPoint版: [添付ファイル]

ご質問等ございましたらお気軽にお声がけください。

## 🔒 アクセス期限
- 公開期間: 2024年X月X日 ～ 2024年Y月Y日
- アーカイブ: 社内文書管理システムに保存
```

## 🗣️ Claude Code協働方針

### このフェーズでClaude Codeに期待すること

1. **デプロイ作業の自動化**
   - GitHub Pages設定の最適化
   - CI/CDパイプラインの構築
   - エラー対応・トラブルシューティング

2. **配布版作成の支援**
   - PDF/PowerPoint変換の品質確認
   - フォーマット最適化
   - 互換性確保

3. **発表後のフォローアップ**
   - フィードバック収集方法の提案
   - アクセス解析設定
   - 改善点の抽出

### 積極的に相談したいポイント

- [ ] 「デプロイは正常に完了したか？」
- [ ] 「すべてのバックアップが機能するか？」
- [ ] 「共有設定は適切か？」
- [ ] 「発表後のフォローアップ計画は十分か？」
- [ ] 「アーカイブ・保存方法は適切か？」

## 📊 発表後フィードバック収集

### フィードバック収集システム

**feedback-form.html**:
```html
<!-- 簡易フィードバックフォーム -->
<div id="feedback-section" style="margin-top: 50px; padding: 20px; background: #f5f5f5;">
    <h3>📝 フィードバックをお聞かせください</h3>
    
    <form id="feedbackForm">
        <div>
            <label>理解度:</label>
            <input type="range" min="1" max="5" id="understanding" />
            <span id="understandingValue">3</span>
        </div>
        
        <div>
            <label>有用性:</label>
            <input type="range" min="1" max="5" id="usefulness" />
            <span id="usefulnessValue">3</span>
        </div>
        
        <div>
            <label>コメント:</label>
            <textarea id="comments" rows="3" style="width: 100%;"></textarea>
        </div>
        
        <button type="submit">フィードバック送信</button>
    </form>
</div>

<script>
// フィードバック処理
document.getElementById('feedbackForm').addEventListener('submit', function(e) {
    e.preventDefault();
    
    const feedback = {
        understanding: document.getElementById('understanding').value,
        usefulness: document.getElementById('usefulness').value,
        comments: document.getElementById('comments').value,
        timestamp: new Date().toISOString()
    };
    
    // Google Forms または 社内システムに送信
    console.log('Feedback:', feedback);
    alert('フィードバックをありがとうございました！');
});
</script>
```

### アクセス解析設定

**analytics.js**:
```javascript
// Google Analytics設定（プライバシー配慮版）
gtag('config', 'GA_MEASUREMENT_ID', {
    anonymize_ip: true,
    cookie_flags: 'SameSite=None;Secure'
});

// カスタムイベント追跡
function trackSlideView(slideNumber) {
    gtag('event', 'slide_view', {
        slide_number: slideNumber,
        presentation_id: 'prezenx-demo-2024'
    });
}

function trackEngagement(action) {
    gtag('event', 'engagement', {
        action: action,
        presentation_id: 'prezenx-demo-2024'
    });
}

// 発表完了トラッキング
function trackPresentationComplete() {
    gtag('event', 'presentation_complete', {
        presentation_id: 'prezenx-demo-2024',
        duration: Date.now() - startTime
    });
}
```

## ✅ デプロイ・公開完了チェックリスト

### Claude Codeとの協働確認
- [ ] GitHub Pages自動デプロイ動作確認完了
- [ ] 全バックアップ手段動作確認完了
- [ ] 共有・アクセス設定確認完了
- [ ] フィードバック収集システム確認完了

### 人間による最終確認
- [ ] 公開URL動作確認完了
- [ ] アクセス権限設定確認完了
- [ ] 発表当日準備最終確認完了
- [ ] 関係者への共有情報送信完了

### 発表準備確認
- [ ] オフライン版動作確認完了
- [ ] PDF/PowerPoint版生成確認完了
- [ ] 発表者チェックリスト準備完了
- [ ] トラブル対応手順確認完了

## 🎆 プロジェクト完了

### 最終成果物リスト

```markdown
## PrezenX プロジェクト完了報告

### 🏆 完成成果物
1. **HTMLプレゼンテーション**: https://username.github.io/presentation-repo/
2. **発表者ノート**: speaker-notes.html
3. **PDF版**: presentation.pdf
4. **PowerPoint版**: presentation.pptx
5. **オフライン版**: 完全自己完結版

### 📊 品質評価結果
- **総合評価**: A- (87/100点)
- **技術品質**: A (91/100)
- **コンテンツ品質**: A- (86/100)
- **ユーザビリティ**: B+ (84/100)

### ⏱️ プロジェクト実績
- **総開発時間**: 3.5時間 (目標: 3-5時間)
- **品質レベル**: 企業発表レベル達成
- **目標達成度**: 95%

### 🚀 今後の展開
- **発表実施**: 2024年X月X日 14:00-14:20
- **フィードバック収集**: 発表後1週間
- **改善版作成**: フィードバック反映版
- **テンプレート化**: 他プロジェクトでの再利用
```

---

**📝 記入のコツ**:
- 発表当日の安心感を最優先にする
- バックアップ手段を必ず複数準備する
- 共有・アクセス管理を適切に設定する

**🤖 Claude Codeへの指示**:
このフェーズでは、発表の成功と安全性を最重視してください。技術的なトラブルが発生しても対応できるよう、あらゆるバックアップ手段を準備し、発表者が安心して発表できる環境を整えてください。