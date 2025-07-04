---
layout: default
title: "Phase 2: コンセプト設計"
---

# CLAUDE.md - Phase 2: コンセプト設計

## 🎯 フェーズ概要

**フェーズ名**: コンセプト設計
**目的**: Phase 1の要件をもとに、生成AIによるストーリーライン作成とペルソナ分析による最適化を行う
**想定時間**: 20-40分
**成果物**: storyline.md, audience-personas.md, storyline-analysis.md

## 📐 設計要件

### コンセプト設計の基本方針

**Phase 1からの引き継ぎ情報**:
- **聴衆分析結果**: [キーパーソンとその関心事]
- **成功の定義**: [Phase 1で定義された成功指標]
- **制約条件**: [時間・内容・技術的制約]

### ストーリーライン設計

**基本構造**:
- **導入**: [聴衆の関心を引く開始方法]
- **展開**: [論理的な構成と流れ]
- **結論**: [行動を促すクロージング]
- **時間配分**: [各セクションの時間割り当て]

### メッセージ設計

**核心メッセージ**:
- **ワンライナー**: [15秒で伝えたい核心]
- **キーメッセージ**: [3つの重要ポイント]
- **支持論拠**: [各メッセージを支える根拠]

## 🏗️ Phase 2の3段階プロセス

### 🎬 Step 1: 生成AIによるストーリーライン作成

**Phase 1の要件情報をもとに、Claude Codeに包括的なストーリーラインを生成依頼**

#### 生成AIへの依頼内容

```markdown
Phase 1で定義した要件をもとに、以下の要素を含む詳細なストーリーラインを作成してください：

**必須出力要素:**
1. 📋 **講演タイトル**: インパクトのある魅力的なタイトル
2. 📑 **各ページのスライドタイトル**: 各スライドの見出し
3. 📝 **各ページのサブタイトル**: スライドの補足説明
4. 📊 **各ページのスライド内容**: 具体的な内容・データ・図表
5. 🎤 **各ページのトークスクリプト**: 話す内容の詳細原稿
6. ⏱️ **各ページの講演時間**: 各スライドでの想定話時間

**構成要件:**
- 総講演時間: [Phase 1で定義した時間]
- 聴衆: [Phase 1で分析した聴衆]
- 目的: [Phase 1で設定した目的]
- 制約: [Phase 1で整理した制約条件]
```

#### 期待される生成AIの出力フォーマット

```markdown
# プレゼンテーション・ストーリーライン

## 🎯 講演タイトル
[魅力的で聴衆の関心を引くタイトル]

## 📊 ストーリーライン構成

### スライド1: [スライドタイトル]
**サブタイトル**: [補足説明]
**講演時間**: X分

**スライド内容**:
- [具体的な内容・ポイント]
- [データや図表の指示]
- [視覚的要素の提案]

**トークスクリプト**:
```
[実際に話す内容の詳細原稿]
[聴衆への問いかけや例示を含む]
```

### スライド2: [スライドタイトル]
[以下同様に繰り返し...]

## ⏱️ 時間配分サマリー
- 導入: X分 (スライド1-Y)
- 本論: Z分 (スライドA-B)  
- 結論: W分 (スライドC-D)
- 質疑応答: V分
- **合計: [総時間]分**
```

### 🎭 Step 2: ペルソナ分析による最適化

**生成されたストーリーラインをペルソナ視点で詳細分析・最適化**

#### ペルソナ分析の観点

```markdown
作成いただいたストーリーラインを以下のペルソナ分析で最適化してください：

**主要ペルソナ設定**:
[Phase 1で定義した主要聴衆の詳細ペルソナ]

**分析項目**:
1. 🧠 **認知負荷分析**: 情報量は適切か？複雑すぎないか？
2. 💭 **関心度分析**: 各スライドは聴衆の関心を維持できるか？
3. 🎯 **説得力分析**: 論理構成は聴衆を納得させられるか？
4. ⚡ **エンゲージメント分析**: 飽きさせない工夫があるか？
5. 🔄 **行動変容分析**: 期待する行動変化につながるか？

**最適化要求**:
- 聴衆が理解しやすい構成への調整
- より関心を引く表現方法の提案
- 説得力を高める論理展開の改善
- エンゲージメントを維持する仕掛けの追加
```

#### ペルソナ分析の出力フォーマット

```markdown
# ペルソナ分析レポート

## 🎭 ターゲットペルソナ
**名前**: [ペルソナ名]
**属性**: [役職・専門分野・経験年数]
**関心事**: [主要な関心・懸念事項]
**知識レベル**: [専門知識の程度]

## 📊 ストーリーライン分析結果

### スライド別ペルソナ適合度分析
| スライド | 関心度 | 理解難易度 | 説得力 | 改善提案 |
|:---:|:---:|:---:|:---:|:---:|
| 1 | ⭐⭐⭐⭐⭐ | 易 | 高 | - |
| 2 | ⭐⭐⭐ | 中 | 中 | 具体例追加 |
| ... | ... | ... | ... | ... |

## 🔧 最適化提案
1. **構成の調整**: [具体的な改善案]
2. **表現の改善**: [よりペルソナに響く表現]
3. **追加要素**: [エンゲージメント向上策]
4. **削除要素**: [不要な情報の整理]
```

### ✅ Step 3: 人間による最終チェック

**最適化されたストーリーラインの人間による品質確認**

#### 人間チェックの観点

```markdown
## 🔍 人間による最終チェックリスト

### ✅ 全体構成の確認
- [ ] 論理的な流れに違和感はないか
- [ ] 時間配分は現実的か（練習時間込み）
- [ ] 聴衆のレベルに適しているか
- [ ] 目的達成につながる構成か

### ✅ 内容の妥当性確認  
- [ ] 事実関係に誤りはないか
- [ ] 最新の情報が反映されているか
- [ ] 機密情報・法的問題はないか
- [ ] 企業方針・価値観と整合するか

### ✅ 実用性の確認
- [ ] 実際に話せる内容か
- [ ] 準備可能な資料・データか
- [ ] 技術的に実現可能な図表か
- [ ] 予想される質問への準備ができるか

### ✅ リスク要因の確認
- [ ] 誤解を招く表現はないか
- [ ] 批判を受けやすい内容はないか
- [ ] 代替案・フォロー策は用意されているか
- [ ] 失敗した場合の影響は許容範囲か
```

## 🎨 ビジュアルコンセプト

### デザイン方針

**視覚的なトーン設定**:
- **色調**: [プロフェッショナル/フレンドリー/エネルギッシュ]
- **レイアウト**: [シンプル/情報豊富/ビジュアル重視]
- **フォント**: [読みやすさ重視/インパクト重視/ブランド統一]

### 図表戦略

**使用予定の視覚要素**:
- [ ] **Mermaid図表**: [フローチャート/組織図/シーケンス図]
- [ ] **Chart.js**: [棒グラフ/円グラフ/折れ線グラフ]
- [ ] **数式**: [MathJax数学式/mhchem化学式]
- [ ] **表組み**: [比較表/データ表/スペック表]

## 🗣️ Claude Code協働方針

### Phase 2における協働の流れ

#### 1️⃣ ストーリーライン生成フェーズ
**Claude Codeに期待する役割:**
- Phase 1要件の深い理解と解釈
- 聴衆に最適化された論理構成の提案
- 具体的で実用的なトークスクリプトの作成
- 現実的な時間配分の設計

**人間が提供する情報:**
- Phase 1で整理した要件書の詳細
- 聴衆についての補足情報・背景
- 業界特有の慣習・文化的背景
- 利用可能なデータ・リソースの範囲

#### 2️⃣ ペルソナ分析フェーズ
**Claude Codeに期待する役割:**
- 客観的なペルソナ視点での分析
- 認知科学・心理学に基づく改善提案
- エンゲージメント向上のための具体的施策
- 説得力を高める論理構造の最適化

**人間が提供する情報:**
- 聴衆の個人的特性・過去の反応
- 組織内の力関係・意思決定プロセス
- 業界トレンド・競合他社の動向
- 成功・失敗事例の具体的体験

#### 3️⃣ 最終チェックフェーズ
**人間が重点的に確認する領域:**
- 事実関係の正確性
- 機密情報・コンプライアンス
- 実現可能性・リソース制約
- リスク評価・代替シナリオ

### 効果的な協働のコツ

**📝 質問の仕方:**
```
❌ 悪い例: 「この構成どう思う？」
✅ 良い例: 「この構成で、技術に詳しくない役員が理解できるか、特に財務的影響の部分について客観的に評価してください。」
```

**🔄 反復改善:**
```
1回目: 基本的なストーリーライン生成
2回目: ペルソナ分析による最適化
3回目: 人間チェック後の微調整
```

**⚡ 効率化のポイント:**
- Phase 1の情報を整理して一度に提供
- 具体的な改善要求を明示
- 制約条件を事前に明確化

## 📊 実践例: ストーリーライン生成の流れ

### 実際の協働セッション例

#### 1️⃣ 初回ストーリーライン生成

**人間からClaude Codeへの依頼:**
```markdown
Claude Codeさん、新商品XYZ市場投入のプレゼンテーション（営業会議、15分＋質疑5分）のストーリーラインを作成してください。

**Phase 1からの情報:**
- 聴衆: 営業部長、マーケティング部長、財務部長、CEO（4名）
- 目的: 新商品XYZ市場投入予算1000万円の承認獲得
- 制約: 製造コスト詳細、技術特許情報は言及禁止
- 必須情報: 市場規模、競合比較、投資回収期間

以下の6要素を含む詳細なストーリーラインをお願いします：
1. 講演タイトル
2. 各ページのスライドタイトル  
3. 各ページのサブタイトル
4. 各ページのスライド内容
5. 各ページのトークスクリプト
6. 各ページの講演時間
```

#### 2️⃣ ペルソナ分析依頼

**人間からClaude Codeへの分析依頼:**
```markdown
作成いただいたストーリーラインについて、以下のペルソナで最適化してください：

**主要ペルソナ（CEO）:**
- 属性: 50代男性、起業家出身、直感重視の意思決定
- 関心事: ROI、リスク、競合優位性、会社成長への寄与
- 知識レベル: ビジネス戦略は高い、技術詳細は苦手
- 意思決定パターン: 数字よりもストーリーを重視

この視点で認知負荷、関心度、説得力、エンゲージメント、行動変容の5項目で分析し、最適化案を提示してください。
```

#### 3️⃣ 人間による最終確認

**チェック結果例:**
```markdown
## 最終確認結果

✅ **承認事項:**
- 論理構成: 問題→解決策→効果の流れが明確
- 時間配分: 15分に収まる現実的な構成
- 説得力: 競合比較とROI分析が効果的

⚠️ **要修正事項:**
- スライド3の市場規模: 最新データ（2024年Q3）に更新必要
- スライド7の競合比較: A社の新製品情報を反映
- トークスクリプト: CEO向けにもう少しストーリー性を強化

📝 **追加確認事項:**
- 投資回収期間: 財務部長への事前根回し完了
- 質疑応答: 製造コストについて深掘りされた場合の対応策準備
```

## 📊 成果物と次フェーズへの引き継ぎ

### Phase 2完了時の成果物

1. **storyline.md**: 初期ストーリーライン
2. **audience-personas.md**: ペルソナ分析結果  
3. **storyline-analysis.md**: 最適化済みストーリーライン

### Phase 3への引き継ぎ情報

- 最終確定したストーリーライン構成
- 各スライドの詳細内容指示
- トークスクリプトの方向性
- 必要なデータ・図表の具体的指示
- ペルソナ分析で得られた聴衆インサイト

## ⚠️ 重要な注意事項

### Phase 2で特に注意すべきポイント

#### 🎯 ストーリーライン生成時の注意
- **詳細度の適切性**: あまり詳細すぎるとPhase 3での柔軟性が失われる
- **時間配分の現実性**: 練習時間・質疑応答・予期しない延長を考慮
- **技術的実現性**: Phase 4-5で実装困難な図表・アニメーションを避ける
- **情報の最新性**: 生成AIの知識ベースの制限を人間がカバー

#### 🎭 ペルソナ分析時の注意  
- **過度の最適化避け**: 特定ペルソナに寄せすぎて他聴衆を軽視しない
- **文化的配慮**: 組織文化・業界慣習・地域性を適切に反映
- **リスク評価**: 攻めのメッセージと安全性のバランス
- **代替シナリオ**: 主要ペルソナが不在の場合の対応策

#### 👁️ 人間チェック時の注意
- **客観性の維持**: 個人的好みより聴衆視点を優先
- **完璧主義の回避**: 80%の完成度でPhase 3に進む判断
- **フィードバック記録**: 改善点を次回プロジェクトに活かす
- **時間管理**: Phase 2に時間をかけすぎない（40分以内目標）

## 🎉 Phase 2完了の判断基準

### ✅ 完了チェックリスト

**必須完了事項:**
- [ ] 6要素を含むストーリーラインが完成
- [ ] ペルソナ分析による最適化が実施済み  
- [ ] 人間による最終チェックが完了
- [ ] Phase 3への引き継ぎ情報が整理済み

**品質確認項目:**
- [ ] 論理的な構成になっている
- [ ] 時間制限内に収まる
- [ ] 聴衆のレベルに適している  
- [ ] 目的達成につながる内容

**リスク確認項目:**
- [ ] 事実関係に大きな誤りがない
- [ ] 機密情報・法的問題がない
- [ ] 実現可能な内容である
- [ ] 代替案・フォロー策が検討済み

### 🔄 次フェーズへ

**Phase 2完了時のアクション:**
```bash
# Phase 2の成果物をコミット
git add storyline.md audience-personas.md storyline-analysis.md
git commit -m "Phase 2: コンセプト設計完了

✅ ストーリーライン生成完了（6要素）
✅ ペルソナ分析による最適化完了  
✅ 人間による最終チェック完了

次フェーズ: コンテキスト作成（Markdownコンテンツ作成）

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>"

# Phase 3用のCLAUDE.mdに切り替え
cp workflow/phase3-context-CLAUDE.md ./CLAUDE.md
```

---

> **💡 Phase 2のポイント**: 生成AIの創造性と人間の判断力を組み合わせることで、短時間で高品質なストーリーラインを作成できます。完璧を求めすぎず、Phase 3での詳細化に備えて適切な抽象度を保つことが重要です。