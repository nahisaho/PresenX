# CLAUDE.mdとプロンプト例の整合性修正計画

## 🎯 修正戦略の基本方針

### 📋 統一基準の決定
**どちらを正として統一するか：**
- **CLAUDE.mdファイルを正とする** ← 実装に直結する詳細な指示があるため
- 06-implementation-methodology.mdを CLAUDE.mdに合わせて修正
- 成果物名・プロンプト内容・手順をCLAUDE.mdベースで統一

### 🔄 修正アプローチ
1. **段階的修正**: フェーズごとに順次修正（Phase 1 → 7）
2. **後方互換性**: 既存の参照を壊さない形で修正
3. **文書間リンク**: 修正後の整合性確認

---

## 📊 詳細修正計画

### 🔴 Phase 1 (要件定義) - 優先度: 中

#### 現状の問題
- workflow/phase1-requirements-CLAUDE.md: プロンプト例なし
- 06-implementation-methodology.md: 詳細なプロンプト例あり

#### 修正計画
**Step 1.1: CLAUDE.mdにプロンプト例を追加**
```markdown
## 📝 推奨プロンプト例

### 基本的な要件定義プロンプト
[methodology文書から移植]

### 用途別プロンプト例
- 営業会議向け
- 学会発表向け  
- 技術カンファレンス向け
```

**Step 1.2: methodology文書の参照修正**
- プロンプト例セクションに「詳細はphase1-requirements-CLAUDE.mdを参照」を追加

**所要時間**: 30分
**影響範囲**: 限定的

---

### 🔴 Phase 2 (コンセプト設計) - 優先度: 最高

#### 現状の問題（重大）
**成果物名の完全不一致:**
| CLAUDE.md | methodology文書 |
|:---:|:---:|
| storyboard.md | storyline.md |
| persona-analysis.md | audience-personas.md |
| optimized-storyboard.md | storyline-analysis.md |
| （なし） | storytelling-improvements.md |

#### 修正計画
**Step 2.1: 成果物名の統一（CLAUDE.mdを正とする）**

*Option A: CLAUDE.mdの成果物名を採用*
```diff
06-implementation-methodology.md修正:
- storyline.md → storyboard.md
- audience-personas.md → persona-analysis.md  
- storyline-analysis.md → optimized-storyboard.md
- storytelling-improvements.md → （optimized-storyboard.mdに統合）
```

*Option B: methodology文書の成果物名を採用*
```diff
CLAUDE.mdファイル修正:
- storyboard.md → storyline.md
- persona-analysis.md → audience-personas.md
- optimized-storyboard.md → storyline-analysis.md
+ storytelling-improvements.md の追加
```

**推奨: Option A（CLAUDE.mdの名称を採用）**
- 理由: より簡潔で分かりやすい
- 技術的整合性が高い

**Step 2.2: プロンプト内容の統一**
- methodology文書のプロンプト例をCLAUDE.mdの指示と整合させる
- 出力フォーマットの統一

**Step 2.3: 手順の整合性確認**
- 3段階プロセス（ストーリーライン作成→ペルソナ分析→最適化）の統一
- Git操作手順の統一

**所要時間**: 90分
**影響範囲**: 大（Phase 3との連携に影響）

---

### 🔴 Phase 3 (コンテキスト作成) - 優先度: 最高

#### 現状の問題（重大）
**成果物名の不一致:**
| CLAUDE.md | methodology文書 |
|:---:|:---:|
| presentation.md | presentation-context.md |
| speaker-notes.md | （記載なし） |

#### 修正計画
**Step 3.1: 成果物名の統一**

*推奨: methodology文書の名称を採用*
```diff
CLAUDE.mdファイル修正:
- presentation.md → presentation-context.md
+ speaker-notes.mdの位置づけ明確化
```

**理由**: 
- `presentation-context.md`の方が内容を明確に表現
- Phase 4, 5での参照に影響が少ない

**Step 3.2: 4要素フォーマットの統一**
```markdown
統一フォーマット:
1. スライドタイトル（パワーフレーズ）
2. スライドサブタイトル  
3. スライドの中身（箇条書き）
4. スライドのトークスクリプト
```

**Step 3.3: Phase 2との連携確認**
- Phase 2の成果物（storyboard.md等）を正しく参照
- 引き継ぎ情報の整合性確認

**所要時間**: 60分
**影響範囲**: 大（Phase 4, 5に影響）

---

### 🟡 Phase 4 (ビジュアル開発) - 優先度: 中

#### 現状の問題
- methodology文書で成果物名が不明確
- 図表・グラフの具体的指示の差異

#### 修正計画
**Step 4.1: 成果物の明確化**
```markdown
Phase 4成果物:
- enhanced-presentation-context.md（ビジュアル要素追加版）
- visual-assets/（図表ファイル格納）
  - mermaid-diagrams/
  - chartjs-configs/
  - mathj-equations/
```

**Step 4.2: Mermaid/Chart.js指示の統一**
- CLAUDE.mdの詳細指示をmethodology文書に反映

**所要時間**: 45分
**影響範囲**: 中

---

### 🔴 Phase 5 (HTML生成) - 優先度: 最高

#### 現状の問題（重大）
- 5つの専用版（General/Technical/Business/Academic/Educational）の説明不足
- 用途別特化アプローチの不整合

#### 修正計画
**Step 5.1: 用途別特化の詳細説明追加**
```markdown
methodology文書に追加:

## 🎯 Phase 5: 用途別HTML生成

### 5つの専用版から選択
| 版 | 対象ユーザー | 特化機能 |
|:---:|:---:|:---:|
| General | 汎用利用者 | シンプルなreveal.js |
| Technical | 技術者 | PWA、Web Components |
| Business | ビジネス | KPI、ROI分析 |
| Academic | 研究者 | Citation.js、LaTeX |
| Educational | 教育者 | インタラクティブ機能 |
```

**Step 5.2: プロンプト例の用途別特化**
- 各専用版に対応したプロンプト例を追加
- CLAUDE.mdファイル切り替え手順の明記

**Step 5.3: 成果物の統一**
```markdown
共通成果物:
- presentation.html（メインファイル）
- assets/（リソースファイル）
```

**所要時間**: 75分
**影響範囲**: 大（利用者の選択に直結）

---

### 🟡 Phase 6-7 - 優先度: 低

#### 修正計画
**Step 6.1: 詳細度の統一**
- CLAUDE.mdの詳細な手順をmethodology文書に反映
- 品質確認チェックリストの統一

**Step 7.1: デプロイ手順の詳細化**
- GitHub Pages設定の詳細をmethodology文書に追加

**所要時間**: 30分（各フェーズ）
**影響範囲**: 限定的

---

## 📋 修正実行計画

### 🚀 実行順序（優先度順）

#### Phase 1: 緊急修正（重大な矛盾解消）
1. **Phase 2成果物名統一** (30分)
2. **Phase 3成果物名統一** (20分)  
3. **Phase 5用途別特化説明** (45分)
4. **全体整合性確認** (15分)

**小計: 110分（約2時間）**

#### Phase 2: 詳細修正（内容の充実）
1. **Phase 1プロンプト例統一** (30分)
2. **Phase 2プロンプト内容統一** (60分)
3. **Phase 3フォーマット統一** (40分)
4. **Phase 4成果物明確化** (45分)
5. **Phase 5プロンプト例拡充** (30分)

**小計: 205分（約3.5時間）**

#### Phase 3: 仕上げ修正（品質向上）
1. **Phase 6-7詳細化** (60分)
2. **文書間リンク整備** (30分)
3. **最終検証** (30分)

**小計: 120分（約2時間）**

### 📊 総所要時間: 約7.5時間

---

## ⚠️ リスク管理

### 🚨 修正時の注意点
1. **既存参照の破綻防止**
   - ファイル名変更時は古い名前での言及も同時修正
   - README.mdや他の文書の参照も確認

2. **Git履歴の保全**
   - ファイル名変更はgit mvを使用
   - コミットメッセージで変更理由を明記

3. **段階的検証**
   - 各フェーズ修正後に動作確認
   - 他フェーズへの影響をチェック

### 🔄 修正後の検証項目
1. **ファイル名参照の一貫性**
2. **プロンプト例の実行可能性**  
3. **成果物の連携性**
4. **GitHub Actionsの動作確認**

---

## 🎯 成功基準

### ✅ 修正完了の判断基準
1. **成果物名の完全統一**: 全フェーズで同一ファイル名
2. **プロンプト例の実行可能性**: CLAUDE.mdの指示で実行可能
3. **手順の一貫性**: methodology ↔ CLAUDE.mdで齟齬なし
4. **文書品質の向上**: より実用的で理解しやすい

### 📈 期待される効果
1. **開発効率の向上**: 混乱なく作業を進行可能
2. **品質の安定化**: 一貫したワークフローで高品質維持  
3. **学習コストの削減**: 統一された文書体系で習得しやすい
4. **メンテナンス性の向上**: 文書間の整合性維持が容易

---

## 🚀 次のアクション

### 即座に実行すべき項目
1. **Phase 2成果物名の統一決定**: storyboard vs storylineどちらにするか
2. **Phase 3成果物名の確定**: presentation-context.mdで統一
3. **Phase 5説明の追加**: 5つの専用版の説明をmethodology文書に追加

この計画に基づいて修正を開始しますか？あるいは特定のフェーズから優先的に着手しますか？