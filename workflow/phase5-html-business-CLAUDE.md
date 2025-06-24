# CLAUDE.md - Phase 5: HTML生成（Business版）

## 🎯 フェーズ概要

**フェーズ名**: HTML生成（ビジネスプレゼンテーション版）
**目的**: ビジネスの現場で求められるプロフェッショナルなHTMLプレゼンテーションを構築する
**想定時間**: 30-60分
**成果物**: ビジネス標準対応プレゼンテーション + エクスポート機能
**対象者**: 
- ビジネスプレゼンテーション（営業提案・企画書・経営報告）
- 企業内発表者・ビジネスパーソン
- 営業・マーケティング・経営企画担当者
- コンサルタント・アナリスト・ストラテジスト

## 🏢 Business版の特徴

### 💼 企業プレゼンテーション特化

**ビジネス要件対応**:
- **企業ブランディング**: ロゴ・カラー・フォント統一
- **データビジュアライゼーション**: 売上・KPI・ROI分析
- **エクゼクティブサマリー**: 要点を即座に把握
- **印刷・配布対応**: PDF・PowerPoint出力
- **セキュリティ配慮**: データ保護・アクセス制御

### 📊 ビジネスデータ分析機能

**分析機能**:
- **財務分析**: P&L・キャッシュフロー・バランスシート
- **市場分析**: 競合比較・市場シェア・トレンド
- **KPI ダッシュボード**: リアルタイム指標表示
- **ROI 計算**: 投資対効果・リスク分析
- **予測モデル**: 売上予測・成長シミュレーション

## 🏗️ ビジネス特化HTML生成アーキテクチャ

### Step 1: 企業ブランディング対応

#### コーポレートアイデンティティ設定

**corporate-theme.css**:
```css
/* 企業カラーパレット */
:root {
    /* Primary Brand Colors */
    --corporate-primary: #003366;      /* コーポレートブルー */
    --corporate-secondary: #0066CC;    /* アクセントブルー */
    --corporate-accent: #FF6600;       /* オレンジアクセント */
    
    /* Neutral Colors */
    --corporate-gray-dark: #333333;
    --corporate-gray-medium: #666666;
    --corporate-gray-light: #F5F5F5;
    --corporate-white: #FFFFFF;
    
    /* Status Colors */
    --success-green: #28A745;
    --warning-yellow: #FFC107;
    --danger-red: #DC3545;
    --info-blue: #17A2B8;
    
    /* Typography */
    --font-primary: 'Arial', 'Helvetica Neue', sans-serif;
    --font-secondary: 'Georgia', 'Times New Roman', serif;
    --font-data: 'Courier New', monospace;
}

/* スライド全体の余白設定 */
.reveal .slides {
    width: 80%;
    margin: 10%;
}

/* 企業ロゴ配置 */
.corporate-header {
    position: fixed;
    top: 20px;
    right: 30px;
    z-index: 1000;
    opacity: 0.8;
}

.corporate-logo {
    max-height: 60px;
    max-width: 200px;
}

/* エクゼクティブスライド */
.executive-slide {
    background: linear-gradient(135deg, var(--corporate-primary) 0%, var(--corporate-secondary) 100%);
    color: var(--corporate-white);
    padding: 40px;
}

.executive-slide h1 {
    font-size: 3em;
    font-weight: bold;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
    margin-bottom: 0.5em;
}

.executive-slide h2 {
    font-size: 1.5em;
    opacity: 0.9;
    font-weight: normal;
}

/* ビジネスKPI表示 */
.kpi-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
    margin: 30px 0;
}

.kpi-card {
    background: var(--corporate-white);
    border-left: 5px solid var(--corporate-primary);
    padding: 20px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    border-radius: 8px;
    transition: transform 0.3s ease;
}

.kpi-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 5px 20px rgba(0,0,0,0.15);
}

.kpi-value {
    font-size: 2.5em;
    font-weight: bold;
    color: var(--corporate-primary);
    margin-bottom: 5px;
}

.kpi-label {
    color: var(--corporate-gray-medium);
    font-size: 0.9em;
    text-transform: uppercase;
    letter-spacing: 1px;
}

.kpi-trend {
    font-size: 0.8em;
    margin-top: 10px;
}

.trend-up { color: var(--success-green); }
.trend-down { color: var(--danger-red); }
.trend-stable { color: var(--corporate-gray-medium); }
```

### Step 2: 高度なビジネスチャート

#### Chart.js ビジネス設定

**business-charts.js**:
```javascript
// ビジネス用Chart.jsテーマ設定
Chart.defaults.font.family = 'Arial, Helvetica Neue, sans-serif';
Chart.defaults.font.size = 12;
Chart.defaults.color = '#333333';

// 企業カラーパレット
const CORPORATE_COLORS = {
    primary: '#003366',
    secondary: '#0066CC',
    accent: '#FF6600',
    success: '#28A745',
    warning: '#FFC107',
    danger: '#DC3545',
    neutral: ['#E8F4FD', '#D1E9FC', '#B9DDFB', '#A2D2FA']
};

// 売上推移チャート（詳細版）
function createSalesChart(canvasId, data) {
    const ctx = document.getElementById(canvasId);
    return new Chart(ctx, {
        type: 'line',
        data: {
            labels: data.periods,
            datasets: [{
                label: '売上（百万円）',
                data: data.revenue,
                borderColor: CORPORATE_COLORS.primary,
                backgroundColor: 'rgba(0, 51, 102, 0.1)',
                borderWidth: 3,
                tension: 0.4,
                pointRadius: 6,
                pointHoverRadius: 8
            }, {
                label: '予算（百万円）',
                data: data.budget,
                borderColor: CORPORATE_COLORS.secondary,
                backgroundColor: 'rgba(0, 102, 204, 0.1)',
                borderWidth: 2,
                borderDash: [10, 5],
                tension: 0.4,
                pointRadius: 4
            }]
        },
        options: {
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
                title: {
                    display: true,
                    text: '売上実績 vs 予算推移',
                    font: { size: 18, weight: 'bold' },
                    color: CORPORATE_COLORS.primary
                },
                legend: {
                    position: 'top',
                    labels: {
                        usePointStyle: true,
                        padding: 20
                    }
                },
                tooltip: {
                    mode: 'index',
                    intersect: false,
                    callbacks: {
                        label: function(context) {
                            return context.dataset.label + ': ¥' + 
                                   context.parsed.y.toLocaleString() + '百万円';
                        }
                    }
                }
            },
            scales: {
                x: {
                    title: {
                        display: true,
                        text: '期間'
                    },
                    grid: {
                        display: false
                    }
                },
                y: {
                    title: {
                        display: true,
                        text: '売上（百万円）'
                    },
                    beginAtZero: true,
                    ticks: {
                        callback: function(value) {
                            return '¥' + value.toLocaleString();
                        }
                    }
                }
            },
            interaction: {
                mode: 'nearest',
                axis: 'x',
                intersect: false
            }
        }
    });
}

// 市場シェア分析（ドーナツチャート）
function createMarketShareChart(canvasId, data) {
    const ctx = document.getElementById(canvasId);
    return new Chart(ctx, {
        type: 'doughnut',
        data: {
            labels: data.companies,
            datasets: [{
                data: data.shares,
                backgroundColor: [
                    CORPORATE_COLORS.primary,
                    CORPORATE_COLORS.secondary,
                    CORPORATE_COLORS.accent,
                    '#9C27B0',
                    '#607D8B'
                ],
                borderWidth: 3,
                borderColor: '#FFFFFF',
                hoverOffset: 10
            }]
        },
        options: {
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
                title: {
                    display: true,
                    text: '市場シェア分析',
                    font: { size: 18, weight: 'bold' },
                    color: CORPORATE_COLORS.primary
                },
                legend: {
                    position: 'right',
                    labels: {
                        padding: 20,
                        usePointStyle: true
                    }
                },
                tooltip: {
                    callbacks: {
                        label: function(context) {
                            return context.label + ': ' + context.parsed + '%';
                        }
                    }
                }
            },
            cutout: '50%'
        }
    });
}

// ROI分析チャート（複合チャート）
function createROIChart(canvasId, data) {
    const ctx = document.getElementById(canvasId);
    return new Chart(ctx, {
        type: 'bar',
        data: {
            labels: data.projects,
            datasets: [{
                type: 'bar',
                label: '投資額（百万円）',
                data: data.investment,
                backgroundColor: 'rgba(220, 53, 69, 0.7)',
                borderColor: CORPORATE_COLORS.danger,
                borderWidth: 2,
                yAxisID: 'y'
            }, {
                type: 'bar',
                label: '収益（百万円）',
                data: data.revenue,
                backgroundColor: 'rgba(40, 167, 69, 0.7)',
                borderColor: CORPORATE_COLORS.success,
                borderWidth: 2,
                yAxisID: 'y'
            }, {
                type: 'line',
                label: 'ROI (%)',
                data: data.roi,
                borderColor: CORPORATE_COLORS.accent,
                backgroundColor: 'rgba(255, 102, 0, 0.1)',
                borderWidth: 3,
                tension: 0.4,
                yAxisID: 'y1',
                pointRadius: 6
            }]
        },
        options: {
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
                title: {
                    display: true,
                    text: 'プロジェクト別ROI分析',
                    font: { size: 18, weight: 'bold' },
                    color: CORPORATE_COLORS.primary
                },
                legend: {
                    position: 'top'
                }
            },
            scales: {
                x: {
                    title: {
                        display: true,
                        text: 'プロジェクト'
                    }
                },
                y: {
                    type: 'linear',
                    display: true,
                    position: 'left',
                    title: {
                        display: true,
                        text: '金額（百万円）'
                    }
                },
                y1: {
                    type: 'linear',
                    display: true,
                    position: 'right',
                    title: {
                        display: true,
                        text: 'ROI (%)'
                    },
                    grid: {
                        drawOnChartArea: false
                    }
                }
            }
        }
    });
}
```

### Step 3: エクゼクティブサマリー機能

#### ダッシュボード機能

**executive-dashboard.js**:
```javascript
// エクゼクティブダッシュボード
class ExecutiveDashboard {
    constructor(containerId) {
        this.container = document.getElementById(containerId);
        this.data = null;
        this.init();
    }

    init() {
        this.createDashboardStructure();
        this.loadData();
        this.setupRealTimeUpdate();
    }

    createDashboardStructure() {
        this.container.innerHTML = `
            <div class="dashboard-header">
                <h2>エクゼクティブサマリー</h2>
                <div class="dashboard-controls">
                    <select id="period-selector">
                        <option value="q1">Q1 2024</option>
                        <option value="q2">Q2 2024</option>
                        <option value="q3">Q3 2024</option>
                        <option value="q4">Q4 2024</option>
                    </select>
                    <button id="export-dashboard" class="btn-primary">
                        PDF出力
                    </button>
                </div>
            </div>
            
            <div class="kpi-grid">
                <div class="kpi-card" id="revenue-kpi">
                    <div class="kpi-value">¥0</div>
                    <div class="kpi-label">売上高</div>
                    <div class="kpi-trend"></div>
                </div>
                
                <div class="kpi-card" id="profit-kpi">
                    <div class="kpi-value">¥0</div>
                    <div class="kpi-label">営業利益</div>
                    <div class="kpi-trend"></div>
                </div>
                
                <div class="kpi-card" id="margin-kpi">
                    <div class="kpi-value">0%</div>
                    <div class="kpi-label">利益率</div>
                    <div class="kpi-trend"></div>
                </div>
                
                <div class="kpi-card" id="growth-kpi">
                    <div class="kpi-value">0%</div>
                    <div class="kpi-label">成長率</div>
                    <div class="kpi-trend"></div>
                </div>
            </div>
            
            <div class="dashboard-charts">
                <div class="chart-section">
                    <canvas id="executive-trend-chart"></canvas>
                </div>
                <div class="chart-section">
                    <canvas id="executive-breakdown-chart"></canvas>
                </div>
            </div>
        `;
    }

    updateKPI(kpiId, value, trend, percentage) {
        const kpiCard = document.getElementById(kpiId);
        const valueElement = kpiCard.querySelector('.kpi-value');
        const trendElement = kpiCard.querySelector('.kpi-trend');
        
        // 数値のアニメーション
        this.animateValue(valueElement, 0, value, 1000);
        
        // トレンド表示
        const trendClass = percentage > 0 ? 'trend-up' : 
                          percentage < 0 ? 'trend-down' : 'trend-stable';
        const trendIcon = percentage > 0 ? '↗' : 
                         percentage < 0 ? '↘' : '→';
        
        trendElement.className = `kpi-trend ${trendClass}`;
        trendElement.innerHTML = `${trendIcon} ${Math.abs(percentage).toFixed(1)}%`;
    }

    animateValue(element, start, end, duration) {
        const range = end - start;
        const startTime = performance.now();
        
        const step = (currentTime) => {
            const elapsed = currentTime - startTime;
            const progress = Math.min(elapsed / duration, 1);
            const current = start + (range * progress);
            
            if (element.textContent.includes('¥')) {
                element.textContent = '¥' + Math.floor(current).toLocaleString();
            } else if (element.textContent.includes('%')) {
                element.textContent = current.toFixed(1) + '%';
            } else {
                element.textContent = Math.floor(current).toLocaleString();
            }
            
            if (progress < 1) {
                requestAnimationFrame(step);
            }
        };
        
        requestAnimationFrame(step);
    }

    setupRealTimeUpdate() {
        // 期間選択の変更処理
        document.getElementById('period-selector').addEventListener('change', (e) => {
            this.loadData(e.target.value);
        });

        // PDF出力機能
        document.getElementById('export-dashboard').addEventListener('click', () => {
            this.exportToPDF();
        });
    }

    exportToPDF() {
        // PDF出力処理（html2pdf.jsライブラリを使用）
        const element = this.container;
        const opt = {
            margin: 1,
            filename: 'executive-summary.pdf',
            image: { type: 'jpeg', quality: 0.98 },
            html2canvas: { scale: 2 },
            jsPDF: { unit: 'in', format: 'letter', orientation: 'landscape' }
        };
        
        html2pdf().from(element).set(opt).save();
    }
}
```

### Step 4: 印刷・エクスポート機能

#### マルチフォーマット対応

**export-functionality.js**:
```javascript
// エクスポート機能管理
class PresentationExporter {
    constructor() {
        this.setupExportButtons();
    }

    setupExportButtons() {
        // PDF出力ボタン
        this.addExportButton('PDF出力', 'pdf', () => this.exportToPDF());
        
        // PowerPoint出力ボタン
        this.addExportButton('PowerPoint出力', 'pptx', () => this.exportToPowerPoint());
        
        // 印刷用HTML出力
        this.addExportButton('印刷用HTML', 'print', () => this.exportToPrint());
        
        // データCSV出力
        this.addExportButton('データCSV', 'csv', () => this.exportToCSV());
    }

    addExportButton(text, type, handler) {
        const toolbar = document.querySelector('.reveal .controls') || 
                       document.body;
        
        const button = document.createElement('button');
        button.textContent = text;
        button.className = `export-btn export-${type}`;
        button.addEventListener('click', handler);
        
        toolbar.appendChild(button);
    }

    exportToPDF() {
        // reveal.js PDF出力モード + html2pdf
        const slides = document.querySelectorAll('.reveal .slides section');
        const pdfContainer = document.createElement('div');
        pdfContainer.className = 'pdf-export-container';
        
        slides.forEach((slide, index) => {
            const slideClone = slide.cloneNode(true);
            slideClone.style.pageBreakAfter = 'always';
            slideClone.style.height = '297mm';
            slideClone.style.width = '210mm';
            pdfContainer.appendChild(slideClone);
        });
        
        document.body.appendChild(pdfContainer);
        
        html2pdf().from(pdfContainer).set({
            margin: 0,
            filename: 'business-presentation.pdf',
            image: { type: 'jpeg', quality: 0.95 },
            html2canvas: { scale: 2, useCORS: true },
            jsPDF: { unit: 'mm', format: 'a4', orientation: 'landscape' }
        }).save().then(() => {
            document.body.removeChild(pdfContainer);
        });
    }

    exportToPowerPoint() {
        // PptxGenJSライブラリを使用
        const pptx = new PptxGenJS();
        const slides = document.querySelectorAll('.reveal .slides section');
        
        slides.forEach((slide, index) => {
            const pptxSlide = pptx.addSlide();
            
            // タイトル抽出
            const title = slide.querySelector('h1, h2, h3');
            if (title) {
                pptxSlide.addText(title.textContent, {
                    x: 0.5, y: 0.5, w: 9, h: 1,
                    fontSize: 28, bold: true,
                    color: '003366'
                });
            }
            
            // コンテンツ抽出
            const contents = slide.querySelectorAll('p, li');
            let yPos = 1.5;
            
            contents.forEach(content => {
                pptxSlide.addText(content.textContent, {
                    x: 0.5, y: yPos, w: 9, h: 0.5,
                    fontSize: 16
                });
                yPos += 0.6;
            });
            
            // チャート処理（base64画像として埋め込み）
            const charts = slide.querySelectorAll('canvas');
            charts.forEach(chart => {
                const imageData = chart.toDataURL('image/png');
                pptxSlide.addImage({
                    data: imageData,
                    x: 0.5, y: yPos, w: 9, h: 5
                });
            });
        });
        
        pptx.writeFile({ fileName: 'business-presentation.pptx' });
    }

    exportToPrint() {
        // 印刷最適化HTML生成
        const printWindow = window.open('', '_blank');
        const slides = document.querySelectorAll('.reveal .slides section');
        
        let printHTML = `
            <!DOCTYPE html>
            <html>
            <head>
                <title>Business Presentation - Print Version</title>
                <style>
                    @media print {
                        body { margin: 0; font-family: Arial, sans-serif; }
                        .slide { page-break-after: always; padding: 2cm; }
                        .slide:last-child { page-break-after: avoid; }
                        h1, h2, h3 { color: #003366; }
                        table { border-collapse: collapse; width: 100%; }
                        th, td { border: 1px solid #ddd; padding: 8px; }
                        .chart-placeholder {
                            border: 2px dashed #ccc;
                            height: 200px;
                            display: flex;
                            align-items: center;
                            justify-content: center;
                            color: #999;
                        }
                    }
                </style>
            </head>
            <body>
        `;
        
        slides.forEach((slide, index) => {
            printHTML += `<div class="slide">`;
            printHTML += slide.innerHTML;
            printHTML += `</div>`;
        });
        
        printHTML += `</body></html>`;
        
        printWindow.document.write(printHTML);
        printWindow.document.close();
        printWindow.focus();
        printWindow.print();
    }

    exportToCSV() {
        // プレゼンテーション内のデータをCSV形式で出力
        const tables = document.querySelectorAll('table');
        let csvContent = '';
        
        tables.forEach((table, tableIndex) => {
            csvContent += `Table ${tableIndex + 1}\n`;
            
            const rows = table.querySelectorAll('tr');
            rows.forEach(row => {
                const cells = row.querySelectorAll('th, td');
                const rowData = Array.from(cells).map(cell => 
                    `"${cell.textContent.replace(/"/g, '""')}"`
                ).join(',');
                csvContent += rowData + '\n';
            });
            
            csvContent += '\n';
        });
        
        // CSV ダウンロード
        const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
        const link = document.createElement('a');
        link.href = URL.createObjectURL(blob);
        link.download = 'presentation-data.csv';
        link.click();
    }
}
```

## 🗣️ Claude Code協働方針

### このフェーズでClaude Codeに期待すること

1. **ビジネス要件の理解**
   - 企業プレゼンテーションの標準的な構成要素の把握
   - 業界別・職種別のプレゼンテーション特性の考慮
   - エクゼクティブレベルの要求水準への対応

2. **データビジュアライゼーション**
   - 財務データの適切な可視化手法の選択
   - KPI・ROI分析の効果的な表現方法
   - 複雑なビジネスデータの理解しやすい整理

3. **企業品質の確保**
   - プロフェッショナルなデザイン品質の維持
   - 企業ブランドガイドラインへの準拠
   - 配布・印刷時の品質確保

### 積極的に相談したいポイント

- [ ] 「ビジネスインパクトが明確に伝わるか？」
- [ ] 「ステークホルダーが求める情報が網羅されているか？」
- [ ] 「意思決定に必要なデータが効果的に表示されているか？」
- [ ] 「競合他社・業界標準と比べて遥色ないクオリティか？」
- [ ] 「法務・コンプライアンス・セキュリティ要件を満たしているか？」

## 🔧 品質保証チェック

### ビジネス品質確認

**プロフェッショナル性**:
- [ ] 企業ロゴ・ブランドカラーが統一されている
- [ ] フォント・レイアウトが企業標準に準拠
- [ ] 数値・データの表示精度が適切
- [ ] グラフ・チャートの読みやすさが確保されている

**機能性確認**:
- [ ] PDF出力が高品質で生成される
- [ ] PowerPoint形式での出力が可能
- [ ] 印刷時のレイアウトが適切
- [ ] データのCSVエクスポートが機能する

### エクゼクティブレビュー

**意思決定支援**:
- [ ] 重要な数値・KPIが即座に把握可能
- [ ] トレンド・傾向が視覚的に明確
- [ ] 問題点・機会が効果的にハイライト
- [ ] アクションアイテムが明確に提示

**プレゼンテーション効果**:
- [ ] ストーリーラインが論理的で説得力がある
- [ ] 聴衆の関心・疑問に的確に応答
- [ ] 時間内で要点を効率的に伝達
- [ ] フォローアップ資料が適切に準備

## 📁 ファイル構成

### ビジネス版成果物

```
business-presentation/
├── index.html                  # メインプレゼンテーション
├── assets/
│   ├── corporate/
│   │   ├── logo.png           # 企業ロゴ
│   │   ├── brand-colors.css   # ブランドカラー設定
│   │   └── corporate-theme.css
│   ├── charts/
│   │   ├── business-charts.js
│   │   ├── financial-data.js
│   │   └── kpi-dashboard.js
│   ├── export/
│   │   ├── pdf-styles.css
│   │   ├── print-layout.css
│   │   └── export-functions.js
│   └── data/
│       ├── financial-data.json
│       ├── market-data.json
│       └── kpi-data.json
├── exports/
│   ├── presentation.pdf       # PDF版
│   ├── presentation.pptx      # PowerPoint版
│   ├── handout.pdf           # 配布資料
│   └── data-export.csv       # データCSV
├── templates/
│   ├── executive-summary.html
│   ├── financial-review.html
│   ├── market-analysis.html
│   └── action-plan.html
└── docs/
    ├── brand-guidelines.md
    ├── data-sources.md
    └── presentation-guide.md
```

## ✅ HTML生成完了チェックリスト

### Claude Codeとの協働確認
- [ ] ビジネス要件の理解と実装確認完了
- [ ] 企業ブランディング統合確認完了
- [ ] データビジュアライゼーション品質確認完了
- [ ] エクスポート機能動作確認完了

### ビジネス要件適合確認
- [ ] エクゼクティブレベルでの内容適合性確認
- [ ] 企業内発表基準への準拠確認
- [ ] データの正確性・信頼性確認
- [ ] 配布・共有用資料の品質確認

### 運用・保守確認
- [ ] データ更新の手順確認完了
- [ ] セキュリティ要件への対応確認完了
- [ ] バックアップ・アーカイブ手順確認完了
- [ ] トラブル時の対応手順確認完了

## 🚀 次フェーズへの申し送り

### Phase 6（品質確認）への重要事項
- **完成プレゼンテーション**: [ビジネス版HTML一式]
- **企業ブランド対応**: [ロゴ・カラー・フォント統合済み]
- **エクスポート機能**: [PDF・PowerPoint・印刷対応]
- **データソース**: [財務・市場・KPIデータ統合]

### ビジネス特化引き継ぎ事項
- **企業要件**: [ブランドガイドライン準拠状況]
- **データ精度**: [数値・計算式の検証状況]
- **セキュリティ**: [機密情報の取り扱い状況]
- **運用体制**: [更新・保守の手順と責任者]

---

**📝 Business版のコンセプト**:
「企業の信頼性とプロフェッショナリズムを体現する、意思決定支援に最適化されたプレゼンテーション」
ビジネスの現場で即座に活用でき、エクゼクティブレベルの要求水準を満たす高品質な成果物を目指します。

**🤖 Claude Codeへの指示**:
このBusiness版では、企業プレゼンテーションとしての完成度と実用性を最優先してください。データの正確性、ブランドの一貫性、エクスポート機能の確実性を重視し、実際のビジネス現場で安心して使用できるクオリティを確保してください。