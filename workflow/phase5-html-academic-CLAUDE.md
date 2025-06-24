---
layout: default
title: "Phase 5: HTML生成（Academic版）"
---

# CLAUDE.md - Phase 5: HTML生成（Academic版）

## 🎯 フェーズ概要

**フェーズ名**: HTML生成（学術プレゼンテーション版）
**目的**: 学術コミュニティで求められる厚密で正確なHTMLプレゼンテーションを構築する
**想定時間**: 45-75分
**成果物**: 学術發表対応プレゼンテーション + 引用・参考文献管理
**対象者**: 
- 学術プレゼンテーション（学会登壇・研究発表・論文紹介）
- 研究者・大学院生・ポスドク、学者
- 大学・研究機関教員、教育者
- 国際学会・研究コミュニティ参加者

## 🎓 Academic版の特徴

### 📚 学術プレゼンテーションに特化

**適用場面**:
- **学会發表**: 国際会議、学会大会、シンポジウム、ワークショップ
- **研究發表**: 研究室セミナー、進捗報告、博士論文発表
- **教育・講義**: 大学授業、大学院コース、学術講演
- **助成申請**: 研究計画発表、学会グラントプレゼン

**学術要件対応**:
- **学術的厚密性**: 研究方法、結果、考察の詳細記述
- **学術的正確性**: 引用、参考文献、統計的有意性の適切な表示
- **再現可能性**: データ・コード・手法の明確な記載
- **査読対応**: 査読者のチェックポインデへの先回り対応

### 🔬 研究データ可視化

**分析機能**:
- **統計グラフ**: 散布図・箱ひげ図・ヒストグラム
- **実験データ**: 時系列分析・相関分析・回帰分析
- **比較研究**: 群間比較・効果量表示
- **メタ分析**: フォレストプロット・ファンネルプロット
- **分子構造**: ChemSketch・PyMOL連携

## 🏗️ 学術特化HTML生成アーキテクチャ

### Step 1: 学術フォーマット設定

#### 学術論文スタイル設定

**academic-theme.css**:
```css
/* 学術論文標準カラーパレット */
:root {
    /* Academic Colors */
    --academic-primary: #2C3E50;       /* ダークグレーブルー */
    --academic-secondary: #34495E;     /* グレー */
    --academic-accent: #E74C3C;        /* アクセントレッド */
    
    /* Text Colors */
    --text-primary: #2C3E50;
    --text-secondary: #7F8C8D;
    --text-light: #BDC3C7;
    
    /* Background */
    --bg-primary: #FFFFFF;
    --bg-secondary: #F8F9FA;
    --bg-code: #F4F4F4;
    
    /* Academic Typography */
    --font-serif: 'Times New Roman', 'Times', serif;
    --font-sans: 'Helvetica', 'Arial', sans-serif;
    --font-mono: 'Courier New', 'Monaco', monospace;
    --font-math: 'Latin Modern Math', 'STIX Two Math', serif;
}

/* スライド全体の余白設定 */
.reveal .slides {
    width: 80%;
    margin: 10%;
}

/* 学術フォーマット基本設定 */
.reveal .slides section {
    text-align: left;
    font-family: var(--font-serif);
    line-height: 1.6;
    color: var(--text-primary);
    padding: 30px 40px;
}

/* 学術タイトル */
.academic-title {
    text-align: center;
    border-bottom: 3px solid var(--academic-primary);
    padding-bottom: 20px;
    margin-bottom: 30px;
}

.academic-title h1 {
    font-size: 2.2em;
    font-weight: bold;
    color: var(--academic-primary);
    margin-bottom: 15px;
    line-height: 1.2;
}

.academic-subtitle {
    font-size: 1.2em;
    color: var(--text-secondary);
    font-style: italic;
    margin-bottom: 20px;
}

.author-info {
    font-size: 1em;
    color: var(--text-primary);
}

.author-info .author-name {
    font-weight: bold;
    margin-bottom: 5px;
}

.author-info .affiliation {
    font-size: 0.9em;
    color: var(--text-secondary);
    margin-bottom: 5px;
}

.author-info .email {
    font-size: 0.8em;
    color: var(--academic-accent);
    font-family: var(--font-mono);
}

/* 引用・参考文献スタイル */
.citation {
    color: var(--academic-accent);
    font-weight: bold;
    cursor: pointer;
    text-decoration: none;
}

.citation:hover {
    text-decoration: underline;
}

.bibliography {
    font-size: 0.9em;
    line-height: 1.4;
    margin-top: 30px;
    padding-top: 20px;
    border-top: 2px solid var(--bg-secondary);
}

.bibliography h3 {
    color: var(--academic-primary);
    font-size: 1.2em;
    margin-bottom: 15px;
}

.bibliography ol {
    padding-left: 20px;
}

.bibliography li {
    margin-bottom: 10px;
    text-align: justify;
}

/* 数式環境 */
.theorem, .lemma, .definition, .proof {
    background: var(--bg-secondary);
    border-left: 4px solid var(--academic-primary);
    padding: 15px 20px;
    margin: 20px 0;
    border-radius: 0 5px 5px 0;
}

.theorem-title, .lemma-title, .definition-title {
    font-weight: bold;
    color: var(--academic-primary);
    font-size: 1.1em;
    margin-bottom: 10px;
}

.proof {
    border-left-color: var(--text-secondary);
}

.proof-title {
    font-weight: bold;
    color: var(--text-secondary);
    font-style: italic;
}

.qed {
    float: right;
    font-size: 1.2em;
    color: var(--academic-primary);
}

/* 図表番号・キャプション */
.figure-container, .table-container {
    margin: 25px 0;
    text-align: center;
}

.figure-caption, .table-caption {
    font-size: 0.9em;
    color: var(--text-secondary);
    font-style: italic;
    margin-top: 10px;
    text-align: justify;
    padding: 0 20px;
}

.figure-number, .table-number {
    font-weight: bold;
    color: var(--academic-primary);
}

/* 学術表スタイル */
.academic-table {
    width: 100%;
    border-collapse: collapse;
    margin: 20px 0;
    font-size: 0.9em;
    background: var(--bg-primary);
}

.academic-table th {
    background: var(--academic-primary);
    color: white;
    padding: 12px 8px;
    text-align: center;
    font-weight: bold;
    border: 1px solid var(--text-light);
}

.academic-table td {
    padding: 8px;
    text-align: center;
    border: 1px solid var(--text-light);
}

.academic-table tbody tr:nth-child(even) {
    background: var(--bg-secondary);
}

/* 統計値表示 */
.statistics {
    font-family: var(--font-mono);
    background: var(--bg-code);
    padding: 10px 15px;
    border-radius: 5px;
    margin: 15px 0;
    font-size: 0.9em;
}

.p-value {
    font-weight: bold;
}

.p-value.significant {
    color: var(--academic-accent);
}

.confidence-interval {
    font-style: italic;
}
```

### Step 2: 引用・参考文献管理

#### Citation.js 統合

**citation-manager.js**:
```javascript
// 学術引用管理システム
class AcademicCitationManager {
    constructor() {
        this.citations = new Map();
        this.citationCounter = 0;
        this.bibliography = [];
        this.citationStyle = 'apa'; // APA, MLA, Chicago, IEEE
        this.init();
    }

    init() {
        this.loadBibliography();
        this.processCitations();
        this.generateBibliography();
        this.setupCitationTooltips();
    }

    // BibTeX/JSON形式の参考文献読み込み
    loadBibliography() {
        // 外部ファイルから参考文献データを読み込み
        const bibData = [
            {
                id: 'smith2023',
                type: 'article',
                title: 'Advanced Methods in Computational Research',
                author: ['Smith, J.', 'Johnson, M.'],
                journal: 'Journal of Computational Science',
                year: 2023,
                volume: 45,
                pages: '123-145',
                doi: '10.1016/j.jocs.2023.101234'
            },
            {
                id: 'brown2022',
                type: 'book',
                title: 'Statistical Analysis in Modern Research',
                author: ['Brown, A.', 'Davis, R.'],
                publisher: 'Academic Press',
                year: 2022,
                isbn: '978-0123456789'
            },
            {
                id: 'conference2023',
                type: 'inproceedings',
                title: 'Machine Learning Applications in Data Science',
                author: ['Wilson, K.', 'Taylor, S.'],
                booktitle: 'Proceedings of the International Conference on AI',
                year: 2023,
                pages: '456-467',
                location: 'San Francisco, CA'
            }
        ];

        this.bibliography = bibData;
    }

    // 文書内の引用を処理
    processCitations() {
        const citationPattern = /\[cite:([^\]]+)\]/g;
        const textElements = document.querySelectorAll('p, li, td');
        
        textElements.forEach(element => {
            let text = element.innerHTML;
            text = text.replace(citationPattern, (match, citationId) => {
                return this.generateCitation(citationId);
            });
            element.innerHTML = text;
        });
    }

    generateCitation(citationId) {
        if (!this.citations.has(citationId)) {
            this.citationCounter++;
            this.citations.set(citationId, this.citationCounter);
        }
        
        const citationNumber = this.citations.get(citationId);
        const bibEntry = this.bibliography.find(entry => entry.id === citationId);
        
        if (bibEntry) {
            return `<span class="citation" data-citation-id="${citationId}" 
                           data-citation-number="${citationNumber}"
                           title="${this.formatCitationTooltip(bibEntry)}">
                        [${citationNumber}]
                    </span>`;
        }
        
        return `<span class="citation error">[${citationId}?]</span>`;
    }

    formatCitationTooltip(bibEntry) {
        switch (this.citationStyle) {
            case 'apa':
                return this.formatAPA(bibEntry);
            case 'mla':
                return this.formatMLA(bibEntry);
            case 'ieee':
                return this.formatIEEE(bibEntry);
            default:
                return this.formatAPA(bibEntry);
        }
    }

    formatAPA(entry) {
        const authors = entry.author.join(', ');
        if (entry.type === 'article') {
            return `${authors} (${entry.year}). ${entry.title}. ${entry.journal}, ${entry.volume}, ${entry.pages}.`;
        } else if (entry.type === 'book') {
            return `${authors} (${entry.year}). ${entry.title}. ${entry.publisher}.`;
        } else if (entry.type === 'inproceedings') {
            return `${authors} (${entry.year}). ${entry.title}. In ${entry.booktitle} (pp. ${entry.pages}). ${entry.location}.`;
        }
    }

    formatIEEE(entry) {
        const authors = entry.author.map(author => {
            const parts = author.split(', ');
            return `${parts[1]} ${parts[0]}`;
        }).join(', ');
        
        if (entry.type === 'article') {
            return `${authors}, "${entry.title}," ${entry.journal}, vol. ${entry.volume}, pp. ${entry.pages}, ${entry.year}.`;
        }
    }

    generateBibliography() {
        const bibliographyContainer = document.getElementById('bibliography-container');
        if (!bibliographyContainer) return;
        
        let bibliographyHTML = `
            <div class="bibliography">
                <h3>参考文献</h3>
                <ol>
        `;
        
        // 引用順でソート
        const sortedCitations = Array.from(this.citations.entries())
            .sort((a, b) => a[1] - b[1]);
        
        sortedCitations.forEach(([citationId, number]) => {
            const bibEntry = this.bibliography.find(entry => entry.id === citationId);
            if (bibEntry) {
                bibliographyHTML += `
                    <li id="ref-${number}">
                        ${this.formatCitationTooltip(bibEntry)}
                        ${bibEntry.doi ? `<br><small>DOI: <a href="https://doi.org/${bibEntry.doi}" target="_blank">${bibEntry.doi}</a></small>` : ''}
                    </li>
                `;
            }
        });
        
        bibliographyHTML += `
                </ol>
            </div>
        `;
        
        bibliographyContainer.innerHTML = bibliographyHTML;
    }

    setupCitationTooltips() {
        const citations = document.querySelectorAll('.citation');
        citations.forEach(citation => {
            citation.addEventListener('click', (e) => {
                const citationNumber = e.target.getAttribute('data-citation-number');
                const refElement = document.getElementById(`ref-${citationNumber}`);
                if (refElement) {
                    refElement.scrollIntoView({ behavior: 'smooth', block: 'center' });
                    refElement.style.backgroundColor = '#fffacd';
                    setTimeout(() => {
                        refElement.style.backgroundColor = '';
                    }, 2000);
                }
            });
        });
    }
}
```

### Step 3: 学術データ可視化

#### 統計グラフ特化

**academic-charts.js**:
```javascript
// 学術用Chart.js設定
const ACADEMIC_COLORS = {
    primary: '#2C3E50',
    secondary: '#34495E',
    accent: '#E74C3C',
    success: '#27AE60',
    warning: '#F39C12',
    info: '#3498DB',
    grayscale: ['#2C3E50', '#34495E', '#7F8C8D', '#95A5A6', '#BDC3C7', '#ECF0F1']
};

// 散布図（相関分析用）
function createScatterPlot(canvasId, data, options = {}) {
    const ctx = document.getElementById(canvasId);
    const config = {
        type: 'scatter',
        data: {
            datasets: [{
                label: options.label || 'データ',
                data: data.points,
                backgroundColor: ACADEMIC_COLORS.primary,
                borderColor: ACADEMIC_COLORS.primary,
                pointRadius: 5,
                pointHoverRadius: 7
            }]
        },
        options: {
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
                title: {
                    display: true,
                    text: options.title || '散布図',
                    font: { size: 16, weight: 'bold' },
                    color: ACADEMIC_COLORS.primary
                },
                tooltip: {
                    callbacks: {
                        label: function(context) {
                            return `(${context.parsed.x}, ${context.parsed.y})`;
                        },
                        afterLabel: function(context) {
                            return options.pointLabels ? options.pointLabels[context.dataIndex] : '';
                        }
                    }
                }
            },
            scales: {
                x: {
                    type: 'linear',
                    position: 'bottom',
                    title: {
                        display: true,
                        text: options.xLabel || 'X軸'
                    },
                    grid: {
                        color: 'rgba(44, 62, 80, 0.1)'
                    }
                },
                y: {
                    title: {
                        display: true,
                        text: options.yLabel || 'Y軸'
                    },
                    grid: {
                        color: 'rgba(44, 62, 80, 0.1)'
                    }
                }
            }
        }
    };

    // 回帰直線の追加
    if (options.showRegression && data.regression) {
        config.data.datasets.push({
            label: `回帰直線 (R² = ${data.regression.r2.toFixed(3)})`,
            data: data.regression.line,
            type: 'line',
            borderColor: ACADEMIC_COLORS.accent,
            backgroundColor: 'transparent',
            borderWidth: 2,
            pointRadius: 0,
            borderDash: [5, 5]
        });
    }

    return new Chart(ctx, config);
}

// 箱ひげ図
function createBoxPlot(canvasId, data, options = {}) {
    const ctx = document.getElementById(canvasId);
    
    // Chart.js用のカスタム箱ひげ図実装
    const boxplotData = data.groups.map((group, index) => ({
        label: group.name,
        data: [{
            x: index,
            min: group.min,
            q1: group.q1,
            median: group.median,
            q3: group.q3,
            max: group.max,
            outliers: group.outliers || []
        }],
        backgroundColor: ACADEMIC_COLORS.grayscale[index % ACADEMIC_COLORS.grayscale.length],
        borderColor: ACADEMIC_COLORS.primary,
        borderWidth: 2
    }));

    return new Chart(ctx, {
        type: 'boxplot',
        data: {
            datasets: boxplotData
        },
        options: {
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
                title: {
                    display: true,
                    text: options.title || '箱ひげ図',
                    font: { size: 16, weight: 'bold' },
                    color: ACADEMIC_COLORS.primary
                }
            },
            scales: {
                x: {
                    title: {
                        display: true,
                        text: options.xLabel || 'グループ'
                    }
                },
                y: {
                    title: {
                        display: true,
                        text: options.yLabel || '値'
                    }
                }
            }
        }
    });
}

// フォレストプロット（メタ分析用）
function createForestPlot(canvasId, data, options = {}) {
    const ctx = document.getElementById(canvasId);
    
    const forestData = {
        labels: data.studies.map(study => study.name),
        datasets: [
            // エラーバー（信頼区間）
            {
                label: '95% 信頼区間',
                data: data.studies.map(study => ({
                    x: study.effect,
                    y: study.name,
                    errorX: [study.effect - study.ci_lower, study.ci_upper - study.effect]
                })),
                type: 'scatter',
                pointRadius: 8,
                pointStyle: 'rectRot',
                backgroundColor: ACADEMIC_COLORS.primary,
                borderColor: ACADEMIC_COLORS.primary
            },
            // 全体効果
            {
                label: '統合効果',
                data: [{
                    x: data.overall.effect,
                    y: '統合効果'
                }],
                type: 'scatter',
                pointRadius: 12,
                pointStyle: 'diamond',
                backgroundColor: ACADEMIC_COLORS.accent,
                borderColor: ACADEMIC_COLORS.accent,
                borderWidth: 2
            }
        ]
    };

    return new Chart(ctx, {
        type: 'scatter',
        data: forestData,
        options: {
            indexAxis: 'y',
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
                title: {
                    display: true,
                    text: options.title || 'フォレストプロット',
                    font: { size: 16, weight: 'bold' },
                    color: ACADEMIC_COLORS.primary
                },
                tooltip: {
                    callbacks: {
                        label: function(context) {
                            const study = data.studies.find(s => s.name === context.label);
                            if (study) {
                                return `効果量: ${study.effect.toFixed(3)} [${study.ci_lower.toFixed(3)}, ${study.ci_upper.toFixed(3)}]`;
                            }
                            return '';
                        }
                    }
                }
            },
            scales: {
                x: {
                    title: {
                        display: true,
                        text: options.xLabel || '効果量'
                    },
                    grid: {
                        color: 'rgba(44, 62, 80, 0.1)'
                    }
                },
                y: {
                    title: {
                        display: true,
                        text: '研究'
                    }
                }
            }
        }
    });
}

// 統計検定結果表示
function displayStatisticalTest(containerId, testResult) {
    const container = document.getElementById(containerId);
    
    const html = `
        <div class="statistics">
            <h4>統計検定結果</h4>
            <table class="academic-table">
                <tr>
                    <td><strong>検定統計量</strong></td>
                    <td>${testResult.statistic.toFixed(4)}</td>
                </tr>
                <tr>
                    <td><strong>p値</strong></td>
                    <td class="p-value${testResult.pValue < 0.05 ? ' significant' : ''}">${testResult.pValue.toFixed(4)}${testResult.pValue < 0.001 ? ' ***' : testResult.pValue < 0.01 ? ' **' : testResult.pValue < 0.05 ? ' *' : ''}</td>
                </tr>
                <tr>
                    <td><strong>信頼区間 (95%)</strong></td>
                    <td class="confidence-interval">[${testResult.ci_lower.toFixed(4)}, ${testResult.ci_upper.toFixed(4)}]</td>
                </tr>
                <tr>
                    <td><strong>効果量</strong></td>
                    <td>${testResult.effectSize.toFixed(4)}</td>
                </tr>
            </table>
            <p><small>* p < 0.05, ** p < 0.01, *** p < 0.001</small></p>
        </div>
    `;
    
    container.innerHTML = html;
}
```

### Step 4: 数式・定理環境

#### LaTeX数式統合

**math-environments.js**:
```javascript
// 学術数式環境管理
class AcademicMathEnvironments {
    constructor() {
        this.theoremCounter = 0;
        this.lemmaCounter = 0;
        this.definitionCounter = 0;
        this.equationCounter = 0;
        this.init();
    }

    init() {
        this.setupMathJax();
        this.processTheoremEnvironments();
        this.numberEquations();
        this.setupMathTooltips();
    }

    setupMathJax() {
        // 学術用MathJax設定
        window.MathJax = {
            tex: {
                inlineMath: [['$', '$'], ['\\(', '\\)']],
                displayMath: [['$$', '$$'], ['\\[', '\\]']],
                packages: {
                    '[+]': ['ams', 'newcommand', 'configmacros', 'action', 'mhchem']
                },
                macros: {
                    // 学術用マクロ定義
                    RR: '{\\mathbb{R}}',
                    CC: '{\\mathbb{C}}',
                    NN: '{\\mathbb{N}}',
                    ZZ: '{\\mathbb{Z}}',
                    QQ: '{\\mathbb{Q}}',
                    norm: ['{\\left\\|#1\\right\\|}', 1],
                    abs: ['{\\left|#1\\right|}', 1],
                    set: ['{\\left\\{#1\\right\\}}', 1],
                    prob: ['{\\text{P}\\left(#1\\right)}', 1],
                    expect: ['{\\text{E}\\left[#1\\right]}', 1],
                    var: ['{\\text{Var}\\left(#1\\right)}', 1],
                    cov: ['{\\text{Cov}\\left(#1, #2\\right)}', 2]
                }
            },
            chtml: {
                scale: 1.1,
                minScale: 0.5,
                mathmlSpacing: true
            },
            options: {
                renderActions: {
                    addMenu: [0, '', '']
                }
            }
        };
    }

    processTheoremEnvironments() {
        // 定理環境の処理
        this.processEnvironment('theorem', '定理');
        this.processEnvironment('lemma', '補題');
        this.processEnvironment('definition', '定義');
        this.processEnvironment('proof', '証明');
        this.processEnvironment('example', '例');
        this.processEnvironment('remark', '注意');
    }

    processEnvironment(envName, displayName) {
        const elements = document.querySelectorAll(`.${envName}`);
        elements.forEach(element => {
            let counter;
            switch (envName) {
                case 'theorem':
                    this.theoremCounter++;
                    counter = this.theoremCounter;
                    break;
                case 'lemma':
                    this.lemmaCounter++;
                    counter = this.lemmaCounter;
                    break;
                case 'definition':
                    this.definitionCounter++;
                    counter = this.definitionCounter;
                    break;
                default:
                    counter = null;
            }

            const title = element.getAttribute('data-title') || '';
            const titleHtml = counter ? 
                `<div class="${envName}-title">${displayName} ${counter}${title ? ': ' + title : ''}</div>` :
                `<div class="${envName}-title">${displayName}${title ? ': ' + title : ''}</div>`;

            element.innerHTML = titleHtml + element.innerHTML;

            // 証明の場合はQEDマークを追加
            if (envName === 'proof') {
                element.innerHTML += '<span class="qed">□</span>';
            }
        });
    }

    numberEquations() {
        // 数式番号の自動付与
        const equations = document.querySelectorAll('.equation');
        equations.forEach(equation => {
            this.equationCounter++;
            const eqNumber = document.createElement('span');
            eqNumber.className = 'equation-number';
            eqNumber.textContent = `(${this.equationCounter})`;
            equation.appendChild(eqNumber);
        });
    }

    setupMathTooltips() {
        // 数式記号の説明ツールチップ
        const mathSymbols = {
            '\\mathbb{R}': '実数全体の集合',
            '\\mathbb{C}': '複素数全体の集合',
            '\\mathbb{N}': '自然数全体の集合',
            '\\mathbb{Z}': '整数全体の集合',
            '\\mathbb{Q}': '有理数全体の集合',
            '\\infty': '無限大',
            '\\sum': '総和',
            '\\prod': '総積',
            '\\int': '積分',
            '\\partial': '偏微分',
            '\\nabla': 'ナブラ演算子（勾配）',
            '\\Delta': 'ラプラシアン',
            '\\alpha': 'アルファ',
            '\\beta': 'ベータ',
            '\\gamma': 'ガンマ',
            '\\delta': 'デルタ',
            '\\epsilon': 'イプシロン',
            '\\theta': 'シータ',
            '\\lambda': 'ラムダ',
            '\\mu': 'ミュー',
            '\\sigma': 'シグマ',
            '\\omega': 'オメガ'
        };

        // ツールチップの実装は省略（実際の実装では詳細な処理が必要）
    }
}
```

## 🗣️ Claude Code協働方針

### このフェーズでClaude Codeに期待すること

1. **学術コミュニケーションの最適化**
   - 研究の新規性・有用性・影響力の明確な伝達
   - 研究方法の再現可能性、結果の妄当性の明示
   - 先行研究との差分、独自性の効果的なアピール
   - 学術コミュニティへの貢献、将来的な発展の提示

2. **研究的厚密さの保証**
   - 研究仮説、方法論、結果、考察の論理的一貫性
   - 統計的有意性、効果量、信頼区間の適切な表示
   - 研究限界、バイアス、今後の課題の誠実な記載
   - 査読者の疑問を先回りした詳細な説明

3. **学術標準への適合**
   - 引用・参考文献の学術標準（APA・MLA・IEEE等）への準拠
   - 数式・化学式・統計表示の正確性・美しさ
   - 研究倫理・データガバナンスへの配慮
   - 国際学会・査読付きジャーナルの品質水準維持

### 積極的に相談したいポイント

- [ ] 「研究の科学的有用性・新規性が明確に伝わるか？」
- [ ] 「査読者・学術コミュニティが納得できる内容か？」
- [ ] 「研究方法・結果・考察の論理的一貫性は十分か？」
- [ ] 「国際学会・查読付きジャーナルの水準に達しているか？」
- [ ] 「研究倫理・データガバナンスに十分配慮しているか？」

## 🔧 品質保証チェック

### 学術品質確認

**フォーマット準拠**:
- [ ] 引用・参考文献が学術標準に準拠している
- [ ] 数式・化学式が正確に表示されている
- [ ] 図表番号・キャプションが適切に管理されている
- [ ] 学術用語・記号が正確に使用されている

**研究内容の整合性**:
- [ ] データの出典・信頼性が明確
- [ ] 統計分析の手法・結果が適切
- [ ] 研究倫理に配慮した内容構成
- [ ] 再現可能性が確保されている

### 発表効果確認

**学術コミュニケーション**:
- [ ] 研究目的・仮説が明確に提示
- [ ] 方法論・分析手法が適切に説明
- [ ] 結果・考察が論理的に構成
- [ ] 限界・今後の課題が適切に言及

**聴衆への配慮**:
- [ ] 専門用語の適切な解説
- [ ] 視覚的な理解を促進する図表
- [ ] 質疑応答に対応可能な詳細度
- [ ] 時間配分が発表形式に適合

## 📁 ファイル構成

### Academic版成果物

```
academic-presentation/
├── index.html                   # メインプレゼンテーション
├── assets/
│   ├── academic/
│   │   ├── academic-theme.css
│   │   ├── citation-styles.css
│   │   └── math-environments.css
│   ├── data/
│   │   ├── research-data.json
│   │   ├── statistical-results.json
│   │   └── bibliography.bib
│   ├── scripts/
│   │   ├── citation-manager.js
│   │   ├── academic-charts.js
│   │   ├── math-environments.js
│   │   └── statistical-display.js
│   └── figures/
│       ├── charts/
│       ├── diagrams/
│       └── photos/
├── references/
│   ├── bibliography.html       # 参考文献リスト
│   ├── citations.json          # 引用データ
│   └── sources/                # 原典資料
├── supplementary/
│   ├── appendix.html           # 補遺
│   ├── raw-data.csv           # 生データ
│   ├── analysis-code.R        # 分析コード
│   └── methodology.pdf        # 詳細な方法論
├── exports/
│   ├── presentation.pdf       # PDF版
│   ├── handout.pdf           # 配布資料
│   ├── poster.pdf            # ポスター版
│   └── manuscript.docx       # 原稿版
└── docs/
    ├── research-protocol.md
    ├── ethics-approval.pdf
    └── data-management-plan.md
```

## ✅ HTML生成完了チェックリスト

### Claude Codeとの協働確認
- [ ] 学術標準要件の理解と実装確認完了
- [ ] 引用・参考文献管理機能確認完了
- [ ] 数式・定理環境表示確認完了
- [ ] 統計データ可視化機能確認完了

### 学術品質適合確認
- [ ] 学会・論文投稿基準への準拠確認
- [ ] 研究倫理・データ整合性確認
- [ ] 査読・評価基準への適合確認
- [ ] 国際標準フォーマット準拠確認

### 技術的動作確認
- [ ] 数式レンダリング動作確認完了
- [ ] 引用リンク機能確認完了
- [ ] 図表番号自動生成確認完了
- [ ] エクスポート機能動作確認完了

## 🚀 次フェーズへの申し送り

### Phase 6（品質確認）への重要事項
- **完成プレゼンテーション**: [学術版HTML一式]
- **引用・参考文献**: [Citation.js統合・書誌情報管理]
- **数式・定理環境**: [LaTeX数式・定理番号管理]
- **研究データ**: [統計分析・可視化機能統合]

### 学術特化引き継ぎ事項
- **学術標準**: [フォーマット準拠状況・査読対応]
- **データ品質**: [統計分析・研究倫理対応状況]
- **技術仕様**: [数式レンダリング・引用管理システム]
- **品質保証**: [学術コミュニティ標準への適合状況]

---

**📝 Academic版のコンセプト**:
「学術的厳密さと研究コミュニケーションの効果性を両立した、査読・評価に耐える高品質プレゼンテーション」
研究者が安心して学会発表・論文執筆に活用でき、学術コミュニティの標準を満たす品質を確保します。

**🤖 Claude Codeへの指示**:
このAcademic版では、学術発表としての厳密性と正確性を最優先してください。引用・参考文献の管理、数式・統計データの正確な表示、研究倫理への配慮を徹底し、学術コミュニティで信頼される品質を確保してください。