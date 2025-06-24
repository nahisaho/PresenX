---
layout: default
title: "Phase 5: HTML生成（Educational版）"
---

# CLAUDE.md - Phase 5: HTML生成（Educational版）

## 🎯 フェーズ概要

**フェーズ名**: HTML生成（教育・研修プレゼンテーション版）
**目的**: 効果的な学習体験を提供する教育・研修に最適化されたHTMLプレゼンテーションを構築する
**想定時間**: 40-70分
**成果物**: 教育特化プレゼンテーション + 学習支援機能
**対象者**: 
- 教育プレゼンテーション（学校授業・大学講義・オンライン教育・e-learning）
- 企業研修・社員教育・新人研修・スキルアップ研修
- 講演・セミナー・ワークショップ・説明会
- 教材作成者・インストラクショナルデザイナー・研修講師

## 🎓 Educational版の特徴

### 📚 教育・研修プレゼンテーションに特化

**適用場面**:
- **学校教育**: 小中高校授業、大学講義、専門学校、職業訓練校
- **企業研修**: 新人研修、管理職研修、技術研修、コンプライアンス研修
- **公開教育**: セミナー、講演会、ワークショップ、説明会
- **オンライン教育**: e-learning、ウェビナー、MOOCs、リモート研修

**教育要件対応**:
- **学習目標設定**: 明確な学習成果・到達目標の提示
- **段階的学習**: スモールステップ・適応学習・個別対応
- **理解度確認**: クイズ・演習・チェックポイント・振り返り
- **インタラクティブ性**: 参加型学習・グループワーク・ディスカッション促進
- **アクセシビリティ**: 多様な学習者・障害者対応・ユニバーサルデザイン

### 🎨 学習体験設計機能

**学習科学ベース**:
- **認知負荷理論**: 情報の段階的提示・過負荷防止・適切なペーシング
- **マルチメディア学習**: 視覚・聴覚・体感覚の統合的活用
- **アクティブラーニング**: 能動的参加・問題解決・協働学習
- **フィードバック**: 即座の正答確認・建設的評価・改善提案

**学習支援ツール**:
- **プログレストラッキング**: 学習進捗の可視化・達成度表示
- **知識マップ**: 概念間の関係性・前提知識・発展学習
- **学習ノート**: 重要ポイント・メモ機能・復習用まとめ
- **多言語対応**: 国際学習者・外国語教育・翻訳支援

## 🏗️ 教育特化HTML生成アーキテクチャ

### Step 1: 学習設計フレームワーク

#### インストラクショナルデザイン設定

**educational-framework.css**:
```css
/* 教育用カラーパレット */
:root {
    /* Learning Colors */
    --learning-primary: #2E7D33;        /* グリーン（成長・学習） */
    --learning-secondary: #1976D2;      /* ブルー（知識・信頼） */
    --learning-accent: #FF9800;         /* オレンジ（注意・強調） */
    
    /* Feedback Colors */
    --correct-green: #4CAF50;
    --incorrect-red: #F44336;
    --warning-yellow: #FFC107;
    --info-blue: #2196F3;
    
    /* Accessibility Colors */
    --high-contrast-bg: #FFFFFF;
    --high-contrast-text: #000000;
    --low-vision-yellow: #FFFF00;
    --dyslexia-beige: #FAF0E6;
    
    /* Typography */
    --font-primary: 'Noto Sans', 'Arial', sans-serif;
    --font-display: 'Roboto', 'Helvetica', sans-serif;
    --font-mono: 'Courier New', monospace;
}

/* スライド全体の余白設定 */
.reveal .slides {
    width: 80%;
    margin: 10%;
}

/* 学習目標スタイル */
.learning-objectives {
    background: linear-gradient(135deg, var(--learning-primary) 0%, var(--learning-secondary) 100%);
    color: white;
    padding: 30px;
    border-radius: 12px;
    margin: 20px 0;
    box-shadow: 0 4px 15px rgba(46, 125, 51, 0.3);
}

.learning-objectives h2 {
    font-size: 1.8em;
    margin-bottom: 20px;
    text-align: center;
    font-weight: bold;
}

.objectives-list {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 15px;
    margin-top: 20px;
}

.objective-item {
    background: rgba(255, 255, 255, 0.1);
    padding: 15px;
    border-radius: 8px;
    border-left: 4px solid var(--learning-accent);
}

.objective-item::before {
    content: "🎯 ";
    font-size: 1.2em;
    margin-right: 8px;
}

/* プログレスバー */
.learning-progress {
    width: 100%;
    height: 25px;
    background: #E0E0E0;
    border-radius: 12px;
    overflow: hidden;
    margin: 20px 0;
    box-shadow: inset 0 2px 4px rgba(0,0,0,0.1);
}

.progress-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--learning-primary) 0%, var(--learning-secondary) 100%);
    border-radius: 12px;
    transition: width 0.8s ease-in-out;
    position: relative;
}

.progress-text {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: white;
    font-weight: bold;
    font-size: 0.9em;
}

/* インタラクティブクイズ */
.quiz-container {
    background: var(--high-contrast-bg);
    border: 2px solid var(--learning-secondary);
    border-radius: 10px;
    padding: 25px;
    margin: 30px 0;
    box-shadow: 0 4px 12px rgba(25, 118, 210, 0.15);
}

.quiz-question {
    font-size: 1.3em;
    font-weight: bold;
    color: var(--learning-primary);
    margin-bottom: 20px;
    line-height: 1.4;
}

.quiz-options {
    display: flex;
    flex-direction: column;
    gap: 12px;
    margin: 20px 0;
}

.quiz-option {
    background: #F5F5F5;
    border: 2px solid transparent;
    border-radius: 8px;
    padding: 15px 20px;
    cursor: pointer;
    transition: all 0.3s ease;
    font-size: 1.1em;
}

.quiz-option:hover {
    background: #E3F2FD;
    border-color: var(--learning-secondary);
    transform: translateX(5px);
}

.quiz-option.selected {
    background: var(--learning-secondary);
    color: white;
    border-color: var(--learning-primary);
}

.quiz-option.correct {
    background: var(--correct-green);
    color: white;
    border-color: #2E7D33;
}

.quiz-option.incorrect {
    background: var(--incorrect-red);
    color: white;
    border-color: #C62828;
}

.quiz-feedback {
    margin-top: 15px;
    padding: 15px;
    border-radius: 8px;
    font-weight: bold;
    display: none;
}

.quiz-feedback.correct {
    background: #E8F5E8;
    color: var(--correct-green);
    border: 1px solid var(--correct-green);
}

.quiz-feedback.incorrect {
    background: #FFEBEE;
    color: var(--incorrect-red);
    border: 1px solid var(--incorrect-red);
}

/* 学習ノート */
.learning-notes {
    background: var(--dyslexia-beige);
    border-left: 5px solid var(--learning-accent);
    padding: 20px;
    margin: 25px 0;
    border-radius: 0 8px 8px 0;
    box-shadow: 0 2px 8px rgba(255, 152, 0, 0.2);
}

.learning-notes h3 {
    color: var(--learning-primary);
    margin-bottom: 15px;
    font-size: 1.3em;
}

.learning-notes::before {
    content: "📝 重要ポイント";
    display: block;
    font-weight: bold;
    color: var(--learning-accent);
    margin-bottom: 10px;
    font-size: 1.1em;
}

/* アクセシビリティ対応 */
.high-contrast {
    background: var(--high-contrast-bg) !important;
    color: var(--high-contrast-text) !important;
}

.large-text {
    font-size: 1.5em !important;
    line-height: 1.8 !important;
}

.dyslexia-friendly {
    font-family: 'OpenDyslexic', 'Arial', sans-serif !important;
    letter-spacing: 0.1em !important;
    word-spacing: 0.2em !important;
}

/* レスポンシブ対応 */
@media (max-width: 768px) {
    .learning-objectives {
        padding: 20px;
    }
    
    .objectives-list {
        grid-template-columns: 1fr;
    }
    
    .quiz-container {
        padding: 15px;
    }
    
    .quiz-question {
        font-size: 1.1em;
    }
}
```

### Step 2: インタラクティブ学習機能

#### 学習管理システム統合

**educational-interactions.js**:
```javascript
// 教育用インタラクションシステム
class EducationalPresentation {
    constructor() {
        this.currentSlide = 0;
        this.totalSlides = 0;
        this.learningProgress = 0;
        this.quizResults = {};
        this.learningNotes = [];
        this.timeSpentOnSlides = {};
        this.startTime = Date.now();
        this.init();
    }

    init() {
        this.setupProgressTracking();
        this.setupQuizSystem();
        this.setupLearningNotes();
        this.setupAccessibilityFeatures();
        this.setupKeyboardNavigation();
    }

    // 学習進捗管理
    setupProgressTracking() {
        this.totalSlides = document.querySelectorAll('.slides section').length;
        this.updateProgress();
        
        // スライド変更時の進捗更新
        Reveal.addEventListener('slidechanged', (event) => {
            this.currentSlide = event.indexh;
            this.trackTimeOnSlide();
            this.updateProgress();
            this.showSlideObjectives();
        });
    }

    updateProgress() {
        const progressPercentage = ((this.currentSlide + 1) / this.totalSlides) * 100;
        this.learningProgress = progressPercentage;
        
        const progressBar = document.querySelector('.progress-fill');
        const progressText = document.querySelector('.progress-text');
        
        if (progressBar) {
            progressBar.style.width = `${progressPercentage}%`;
        }
        
        if (progressText) {
            progressText.textContent = `${Math.round(progressPercentage)}% 完了 (${this.currentSlide + 1}/${this.totalSlides})`;
        }

        // 達成感演出
        if (progressPercentage === 100) {
            this.celebrateCompletion();
        }
    }

    trackTimeOnSlide() {
        const slideId = `slide-${this.currentSlide}`;
        if (!this.timeSpentOnSlides[slideId]) {
            this.timeSpentOnSlides[slideId] = 0;
        }
        
        if (this.currentSlideStartTime) {
            const timeSpent = Date.now() - this.currentSlideStartTime;
            this.timeSpentOnSlides[slideId] += timeSpent;
        }
        
        this.currentSlideStartTime = Date.now();
    }

    // クイズシステム
    setupQuizSystem() {
        const quizContainers = document.querySelectorAll('.quiz-container');
        
        quizContainers.forEach((container, index) => {
            this.initializeQuiz(container, index);
        });
    }

    initializeQuiz(container, quizId) {
        const options = container.querySelectorAll('.quiz-option');
        const feedback = container.querySelector('.quiz-feedback');
        let selectedOption = null;
        let answered = false;

        options.forEach((option, optionIndex) => {
            option.addEventListener('click', () => {
                if (answered) return;

                // 前の選択をクリア
                options.forEach(opt => opt.classList.remove('selected'));
                
                // 新しい選択を設定
                option.classList.add('selected');
                selectedOption = optionIndex;
                
                // 2秒後に答えを表示
                setTimeout(() => {
                    this.showQuizAnswer(container, quizId, selectedOption);
                    answered = true;
                }, 1000);
            });
        });
    }

    showQuizAnswer(container, quizId, selectedOption) {
        const options = container.querySelectorAll('.quiz-option');
        const feedback = container.querySelector('.quiz-feedback');
        const correctAnswer = parseInt(container.dataset.correct || '0');

        // 正解・不正解の表示
        options.forEach((option, index) => {
            if (index === correctAnswer) {
                option.classList.add('correct');
            } else if (index === selectedOption && index !== correctAnswer) {
                option.classList.add('incorrect');
            }
        });

        // フィードバック表示
        const isCorrect = selectedOption === correctAnswer;
        feedback.style.display = 'block';
        feedback.className = `quiz-feedback ${isCorrect ? 'correct' : 'incorrect'}`;
        
        if (isCorrect) {
            feedback.innerHTML = '✅ 正解です！よく理解されています。';
        } else {
            const explanation = container.dataset.explanation || '正解を確認して理解を深めましょう。';
            feedback.innerHTML = `❌ 不正解です。${explanation}`;
        }

        // 結果を記録
        this.quizResults[quizId] = {
            selected: selectedOption,
            correct: correctAnswer,
            isCorrect: isCorrect,
            timestamp: new Date().toISOString()
        };

        // 学習分析更新
        this.updateLearningAnalytics();
    }

    // 学習ノート機能
    setupLearningNotes() {
        // ノート追加ボタン
        const addNoteButton = document.createElement('button');
        addNoteButton.textContent = '📝 ノート追加';
        addNoteButton.className = 'add-note-btn';
        addNoteButton.style.cssText = `
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 1000;
            background: var(--learning-accent);
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 25px;
            cursor: pointer;
            font-weight: bold;
            box-shadow: 0 4px 12px rgba(255, 152, 0, 0.3);
        `;
        
        addNoteButton.addEventListener('click', () => {
            this.showNoteDialog();
        });
        
        document.body.appendChild(addNoteButton);
    }

    showNoteDialog() {
        const noteText = prompt('学習ノートを入力してください:');
        if (noteText && noteText.trim()) {
            const note = {
                text: noteText.trim(),
                slide: this.currentSlide,
                timestamp: new Date().toISOString(),
                slideTitle: this.getCurrentSlideTitle()
            };
            
            this.learningNotes.push(note);
            this.showNoteConfirmation();
            this.saveLearningData();
        }
    }

    getCurrentSlideTitle() {
        const currentSlideElement = document.querySelectorAll('.slides section')[this.currentSlide];
        const titleElement = currentSlideElement?.querySelector('h1, h2, h3');
        return titleElement?.textContent || `スライド ${this.currentSlide + 1}`;
    }

    showNoteConfirmation() {
        const notification = document.createElement('div');
        notification.textContent = '✅ ノートが保存されました';
        notification.style.cssText = `
            position: fixed;
            top: 20px;
            right: 20px;
            background: var(--correct-green);
            color: white;
            padding: 12px 24px;
            border-radius: 8px;
            z-index: 1001;
            font-weight: bold;
            box-shadow: 0 4px 12px rgba(76, 175, 80, 0.3);
        `;
        
        document.body.appendChild(notification);
        
        setTimeout(() => {
            notification.remove();
        }, 3000);
    }

    // アクセシビリティ機能
    setupAccessibilityFeatures() {
        const accessibilityPanel = document.createElement('div');
        accessibilityPanel.className = 'accessibility-panel';
        accessibilityPanel.innerHTML = `
            <div class="accessibility-controls">
                <h3>アクセシビリティ設定</h3>
                <button id="toggle-high-contrast">ハイコントラスト</button>
                <button id="toggle-large-text">大きな文字</button>
                <button id="toggle-dyslexia">ディスレクシア対応</button>
                <button id="toggle-audio">音声読み上げ</button>
            </div>
        `;
        
        accessibilityPanel.style.cssText = `
            position: fixed;
            top: 20px;
            left: 20px;
            background: white;
            border: 2px solid var(--learning-secondary);
            border-radius: 10px;
            padding: 15px;
            z-index: 1000;
            box-shadow: 0 4px 12px rgba(25, 118, 210, 0.2);
            display: none;
        `;
        
        document.body.appendChild(accessibilityPanel);
        
        // アクセシビリティトグルボタン
        const toggleButton = document.createElement('button');
        toggleButton.textContent = '♿ アクセシビリティ';
        toggleButton.className = 'accessibility-toggle';
        toggleButton.style.cssText = `
            position: fixed;
            top: 20px;
            left: 20px;
            background: var(--learning-secondary);
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 20px;
            cursor: pointer;
            z-index: 1001;
            font-weight: bold;
        `;
        
        toggleButton.addEventListener('click', () => {
            accessibilityPanel.style.display = 
                accessibilityPanel.style.display === 'none' ? 'block' : 'none';
        });
        
        document.body.appendChild(toggleButton);
        
        // アクセシビリティ機能の実装
        this.setupAccessibilityControls();
    }

    setupAccessibilityControls() {
        document.getElementById('toggle-high-contrast')?.addEventListener('click', () => {
            document.body.classList.toggle('high-contrast');
        });
        
        document.getElementById('toggle-large-text')?.addEventListener('click', () => {
            document.body.classList.toggle('large-text');
        });
        
        document.getElementById('toggle-dyslexia')?.addEventListener('click', () => {
            document.body.classList.toggle('dyslexia-friendly');
        });
        
        document.getElementById('toggle-audio')?.addEventListener('click', () => {
            this.toggleTextToSpeech();
        });
    }

    // キーボードナビゲーション
    setupKeyboardNavigation() {
        document.addEventListener('keydown', (event) => {
            switch(event.key) {
                case 'h':
                    this.showHelp();
                    break;
                case 'n':
                    if (event.ctrlKey) {
                        event.preventDefault();
                        this.showNoteDialog();
                    }
                    break;
                case 'p':
                    if (event.ctrlKey) {
                        event.preventDefault();
                        this.showLearningProgress();
                    }
                    break;
            }
        });
    }

    // 学習完了祝福
    celebrateCompletion() {
        const celebration = document.createElement('div');
        celebration.innerHTML = `
            <div class="completion-celebration">
                <h2>🎉 学習完了おめでとうございます！</h2>
                <p>素晴らしい学習姿勢でした。</p>
                <div class="completion-stats">
                    <p>📊 クイズ正答率: ${this.calculateQuizAccuracy()}%</p>
                    <p>⏱️ 学習時間: ${this.formatLearningTime()}</p>
                    <p>📝 ノート数: ${this.learningNotes.length}</p>
                </div>
                <button onclick="this.parentElement.parentElement.remove()">閉じる</button>
            </div>
        `;
        
        celebration.style.cssText = `
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 2000;
        `;
        
        celebration.querySelector('.completion-celebration').style.cssText = `
            background: white;
            padding: 40px;
            border-radius: 15px;
            text-align: center;
            max-width: 500px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
        `;
        
        document.body.appendChild(celebration);
    }

    calculateQuizAccuracy() {
        const totalQuizzes = Object.keys(this.quizResults).length;
        if (totalQuizzes === 0) return 0;
        
        const correctAnswers = Object.values(this.quizResults)
            .filter(result => result.isCorrect).length;
        
        return Math.round((correctAnswers / totalQuizzes) * 100);
    }

    formatLearningTime() {
        const totalTime = Date.now() - this.startTime;
        const minutes = Math.floor(totalTime / 60000);
        const seconds = Math.floor((totalTime % 60000) / 1000);
        return `${minutes}分${seconds}秒`;
    }

    // データ保存・分析
    saveLearningData() {
        const learningData = {
            progress: this.learningProgress,
            quizResults: this.quizResults,
            notes: this.learningNotes,
            timeSpentOnSlides: this.timeSpentOnSlides,
            totalTime: Date.now() - this.startTime,
            completedAt: new Date().toISOString()
        };
        
        localStorage.setItem('prezenx-learning-data', JSON.stringify(learningData));
    }

    updateLearningAnalytics() {
        // 学習分析データの更新（将来的にLMS連携等で活用）
        const analytics = {
            engagement: this.calculateEngagement(),
            comprehension: this.calculateComprehension(),
            completion: this.learningProgress
        };
        
        console.log('Learning Analytics:', analytics);
    }

    calculateEngagement() {
        // エンゲージメント指標の計算
        const avgTimePerSlide = Object.values(this.timeSpentOnSlides)
            .reduce((sum, time) => sum + time, 0) / this.totalSlides;
        return Math.min(100, avgTimePerSlide / 30000 * 100); // 30秒を100%として
    }

    calculateComprehension() {
        // 理解度指標の計算
        return this.calculateQuizAccuracy();
    }
}

// 初期化
document.addEventListener('DOMContentLoaded', () => {
    new EducationalPresentation();
});
```

### Step 3: 学習評価・フィードバック機能

#### 学習成果測定

**learning-assessment.js**:
```javascript
// 学習評価システム
class LearningAssessment {
    constructor() {
        this.assessmentData = {
            preTest: null,
            postTest: null,
            formativeAssessments: [],
            selfReflections: []
        };
        this.init();
    }

    init() {
        this.setupFormativeAssessment();
        this.setupSelfReflection();
        this.setupLearningObjectiveTracking();
    }

    // 形成的評価（途中確認）
    setupFormativeAssessment() {
        const checkpoints = document.querySelectorAll('.learning-checkpoint');
        
        checkpoints.forEach((checkpoint, index) => {
            this.createCheckpoint(checkpoint, index);
        });
    }

    createCheckpoint(element, checkpointId) {
        const questions = JSON.parse(element.dataset.questions || '[]');
        
        const checkpointHTML = `
            <div class="checkpoint-container">
                <h3>🎯 理解度チェック ${checkpointId + 1}</h3>
                <div class="checkpoint-questions">
                    ${questions.map((q, i) => `
                        <div class="checkpoint-question">
                            <p><strong>Q${i + 1}:</strong> ${q.question}</p>
                            <div class="understanding-scale">
                                <label><input type="radio" name="q${checkpointId}_${i}" value="1">全く理解できない</label>
                                <label><input type="radio" name="q${checkpointId}_${i}" value="2">少し理解できる</label>
                                <label><input type="radio" name="q${checkpointId}_${i}" value="3">理解できる</label>
                                <label><input type="radio" name="q${checkpointId}_${i}" value="4">よく理解できる</label>
                                <label><input type="radio" name="q${checkpointId}_${i}" value="5">完全に理解できる</label>
                            </div>
                        </div>
                    `).join('')}
                </div>
                <button class="submit-checkpoint" onclick="this.submitCheckpoint(${checkpointId})">
                    理解度を記録
                </button>
                <div class="checkpoint-feedback" style="display: none;"></div>
            </div>
        `;
        
        element.innerHTML = checkpointHTML;
    }

    submitCheckpoint(checkpointId) {
        const container = document.querySelectorAll('.checkpoint-container')[checkpointId];
        const responses = {};
        
        // 回答収集
        container.querySelectorAll('input[type="radio"]:checked').forEach(input => {
            const questionId = input.name;
            responses[questionId] = parseInt(input.value);
        });
        
        // フィードバック生成
        const feedback = this.generateCheckpointFeedback(responses);
        const feedbackElement = container.querySelector('.checkpoint-feedback');
        
        feedbackElement.innerHTML = feedback;
        feedbackElement.style.display = 'block';
        
        // データ保存
        this.assessmentData.formativeAssessments.push({
            checkpointId,
            responses,
            timestamp: new Date().toISOString()
        });
    }

    generateCheckpointFeedback(responses) {
        const scores = Object.values(responses);
        const averageScore = scores.reduce((sum, score) => sum + score, 0) / scores.length;
        
        let feedback = '<h4>📊 理解度フィードバック</h4>';
        
        if (averageScore >= 4) {
            feedback += '<p style="color: var(--correct-green);">✅ 素晴らしい理解度です！次のセクションに進みましょう。</p>';
        } else if (averageScore >= 3) {
            feedback += '<p style="color: var(--learning-secondary);">👍 良い理解度です。不明な点があれば復習しましょう。</p>';
        } else {
            feedback += '<p style="color: var(--warning-yellow);">⚠️ 理解度が不足している可能性があります。前のセクションを復習することをお勧めします。</p>';
        }
        
        // 個別アドバイス
        feedback += '<div class="individual-advice">';
        scores.forEach((score, index) => {
            if (score <= 2) {
                feedback += `<p>💡 質問${index + 1}: 追加の説明資料や例を確認してみてください。</p>`;
            }
        });
        feedback += '</div>';
        
        return feedback;
    }

    // 自己省察機能
    setupSelfReflection() {
        const reflectionPrompts = [
            "今日学んだ最も重要なことは何ですか？",
            "どの部分が最も理解しにくかったですか？",
            "学習内容を実際にどのように活用できそうですか？",
            "次に学びたいことは何ですか？"
        ];
        
        const reflectionButton = document.createElement('button');
        reflectionButton.textContent = '🤔 振り返り';
        reflectionButton.className = 'reflection-toggle';
        reflectionButton.style.cssText = `
            position: fixed;
            bottom: 80px;
            right: 20px;
            background: var(--learning-primary);
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 25px;
            cursor: pointer;
            font-weight: bold;
            z-index: 1000;
            box-shadow: 0 4px 12px rgba(46, 125, 51, 0.3);
        `;
        
        reflectionButton.addEventListener('click', () => {
            this.showReflectionDialog(reflectionPrompts);
        });
        
        document.body.appendChild(reflectionButton);
    }

    showReflectionDialog(prompts) {
        const dialog = document.createElement('div');
        dialog.innerHTML = `
            <div class="reflection-dialog">
                <h3>🤔 学習の振り返り</h3>
                <form id="reflection-form">
                    ${prompts.map((prompt, index) => `
                        <div class="reflection-prompt">
                            <label for="reflection-${index}">${prompt}</label>
                            <textarea id="reflection-${index}" name="reflection-${index}" 
                                     rows="3" placeholder="自由に記入してください..."></textarea>
                        </div>
                    `).join('')}
                    <div class="reflection-buttons">
                        <button type="submit">保存</button>
                        <button type="button" onclick="this.closest('.reflection-overlay').remove()">キャンセル</button>
                    </div>
                </form>
            </div>
        `;
        
        dialog.className = 'reflection-overlay';
        dialog.style.cssText = `
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 2000;
        `;
        
        dialog.querySelector('.reflection-dialog').style.cssText = `
            background: white;
            padding: 30px;
            border-radius: 15px;
            max-width: 600px;
            max-height: 80vh;
            overflow-y: auto;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
        `;
        
        dialog.querySelector('#reflection-form').addEventListener('submit', (e) => {
            e.preventDefault();
            this.saveReflection(new FormData(e.target));
            dialog.remove();
        });
        
        document.body.appendChild(dialog);
    }

    saveReflection(formData) {
        const reflection = {
            responses: Object.fromEntries(formData),
            timestamp: new Date().toISOString(),
            slideIndex: window.currentSlide || 0
        };
        
        this.assessmentData.selfReflections.push(reflection);
        localStorage.setItem('prezenx-assessment-data', JSON.stringify(this.assessmentData));
        
        // 確認メッセージ
        this.showSaveConfirmation('振り返りが保存されました！継続的な学習に役立ちます。');
    }

    showSaveConfirmation(message) {
        const notification = document.createElement('div');
        notification.textContent = message;
        notification.style.cssText = `
            position: fixed;
            top: 20px;
            right: 20px;
            background: var(--learning-primary);
            color: white;
            padding: 15px 25px;
            border-radius: 8px;
            z-index: 1001;
            font-weight: bold;
            box-shadow: 0 4px 12px rgba(46, 125, 51, 0.3);
            animation: slideInRight 0.5s ease;
        `;
        
        document.body.appendChild(notification);
        
        setTimeout(() => {
            notification.style.animation = 'slideOutRight 0.5s ease';
            setTimeout(() => notification.remove(), 500);
        }, 4000);
    }
}

// CSS アニメーション
const style = document.createElement('style');
style.textContent = `
    @keyframes slideInRight {
        from { transform: translateX(100%); }
        to { transform: translateX(0); }
    }
    
    @keyframes slideOutRight {
        from { transform: translateX(0); }
        to { transform: translateX(100%); }
    }
`;
document.head.appendChild(style);

// 初期化
document.addEventListener('DOMContentLoaded', () => {
    new LearningAssessment();
});
```

## 🗣️ Claude Code協働方針

### このフェーズでClaude Codeに期待すること

1. **教育効果の最大化**
   - 学習科学に基づいた効果的な情報提示・構造化
   - 学習者の認知負荷を適切に管理する段階的コンテンツ配置
   - 多様な学習スタイル（視覚・聴覚・運動感覚）への対応
   - アクティブラーニングを促進するインタラクティブ要素の配置

2. **教育的配慮の実装**
   - 年齢・習熟度・文化的背景を考慮した適切な表現・例示
   - 学習目標と評価基準の明確な整合性確保
   - 誤解を防ぐ正確で分かりやすい説明・図解
   - 建設的なフィードバックと励ましのメッセージ設計

3. **アクセシビリティ・インクルーシブ教育への対応**
   - 障害者・学習困難者に配慮したユニバーサルデザイン
   - 多言語・多文化学習者への配慮
   - デジタルデバイド・技術格差への対応
   - 多様な学習環境（オンライン・オフライン・ハイブリッド）での利用可能性

### 積極的に相談したいポイント

- [ ] 「学習者の理解促進に最も効果的な構成・流れになっているか？」
- [ ] 「年齢・習熟度に適した難易度・表現レベルか？」
- [ ] 「インタラクティブ要素が学習効果を高めているか？」
- [ ] 「アクセシビリティ・インクルーシブ教育の要件を満たしているか？」
- [ ] 「教育現場・研修現場で実用的に活用できるか？」

## 🔧 品質保証チェック

### 教育効果確認

**学習設計**:
- [ ] 学習目標が明確で測定可能
- [ ] 内容が段階的・体系的に構成されている
- [ ] 理解度確認・フィードバック機能が適切に配置
- [ ] 学習者の能動的参加を促す仕組みがある

**教育的配慮**:
- [ ] 年齢・習熟度に適した内容・表現
- [ ] 例示・図解が理解を促進している
- [ ] 誤解・混乱を避ける正確な情報提示
- [ ] 学習者の自信・動機を高める設計

### アクセシビリティ確認

**技術的対応**:
- [ ] スクリーンリーダー対応
- [ ] キーボードナビゲーション完備
- [ ] 色覚・視覚・聴覚障害者への配慮
- [ ] 認知・学習障害者への配慮

**多様性への対応**:
- [ ] 多言語・多文化学習者対応
- [ ] 異なる技術レベル・デバイスでの利用可能性
- [ ] 学習時間・ペースの個別対応
- [ ] 様々な学習環境での適用可能性

### 実用性確認

**教育現場での利用**:
- [ ] 教室・研修室での投影品質
- [ ] 学習管理システム（LMS）との連携可能性
- [ ] 印刷・配布資料としての利用可能性
- [ ] 継続的な利用・更新の容易さ

## 📁 ファイル構成

### Educational版成果物

```
educational-presentation/
├── index.html                    # メインプレゼンテーション
├── assets/
│   ├── educational/
│   │   ├── learning-framework.css
│   │   ├── interactive-elements.css
│   │   └── accessibility.css
│   ├── interactions/
│   │   ├── educational-system.js
│   │   ├── quiz-engine.js
│   │   ├── progress-tracker.js
│   │   └── assessment-tools.js
│   ├── content/
│   │   ├── learning-objectives.json
│   │   ├── quiz-questions.json
│   │   ├── assessment-rubrics.json
│   │   └── multimedia-resources/
│   └── accessibility/
│       ├── screen-reader.js
│       ├── keyboard-navigation.js
│       └── alternative-formats/
├── learning-data/
│   ├── progress-tracking.json
│   ├── quiz-results.json
│   ├── learning-notes.json
│   └── assessment-data.json
├── resources/
│   ├── instructor-guide.md       # 指導者向けガイド
│   ├── learner-guide.md         # 学習者向けガイド
│   ├── technical-requirements.md
│   └── troubleshooting.md
└── exports/
    ├── presentation.pdf         # 印刷用PDF
    ├── learner-workbook.pdf    # 学習者用ワークブック
    ├── instructor-notes.pdf    # 指導者用ノート
    └── scorm-package.zip       # SCORM対応パッケージ
```

## ✅ HTML生成完了チェックリスト

### Claude Codeとの協働確認
- [ ] 教育効果を重視した設計確認完了
- [ ] インタラクティブ学習機能確認完了
- [ ] アクセシビリティ対応確認完了
- [ ] 学習評価・フィードバック機能確認完了

### 教育品質適合確認
- [ ] 学習科学に基づいた設計確認
- [ ] 教育現場での実用性確認
- [ ] 学習者・指導者双方への配慮確認
- [ ] 継続的学習支援機能確認

### 技術的動作確認
- [ ] インタラクティブ要素動作確認完了
- [ ] 学習進捗追跡機能確認完了
- [ ] アクセシビリティ機能確認完了
- [ ] データ保存・分析機能確認完了

## 🚀 次フェーズへの申し送り

### Phase 6（品質確認）への重要事項
- **完成プレゼンテーション**: [教育版HTML一式]
- **学習支援機能**: [進捗追跡・クイズ・ノート・評価システム]
- **アクセシビリティ**: [ユニバーサルデザイン・多様性対応]
- **教育データ**: [学習分析・効果測定データ]

### 教育特化引き継ぎ事項
- **教育効果**: [学習目標達成度・理解促進効果]
- **使いやすさ**: [学習者・指導者双方の操作性]
- **技術要件**: [LMS連携・SCORM対応・データ管理]
- **運用体制**: [継続利用・更新・サポート体制]

---

**📝 Educational版のコンセプト**:
「学習者中心の効果的な教育体験を提供し、多様な学習者が確実に学習目標を達成できる包括的な学習支援システム」
教育の本質である「理解促進」「能力開発」「学習意欲向上」を技術的に支援し、教育現場で実際に活用される実用的な品質を確保します。

**🤖 Claude Codeへの指示**:
このEducational版では、「教育効果」「学習者中心設計」「アクセシビリティ」を最優先してください。学習科学の知見を活用し、多様な学習者が確実に学習目標を達成でき、教育現場で継続的に活用される実用的で効果的な学習環境を構築してください。