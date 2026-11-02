# 画像・ビジュアル全面再制作指示（Codex / Astra）
対象: 成増歯科室キムラ / https://kinnovationx-star.github.io/kimura-dental-site/
参考: https://open-rise.jp/
作業ブランチ: `redesign/premium-visual-overhaul-2026`

## 必須要件：既存画像の紹介・差し替え案だけで終わらせない
**サイトの見た目を構成する画像を新規に制作/許諾済み素材から再調達し、PC・SPの画像ファイルを実際に作成して、コード内の画像参照を差し替える。**
- デザイン案・プロンプト案・候補画像URLを並べるだけでは完了としない。
- 実際に画像生成/編集を行える環境なら制作する。機能がない場合は画像生成可能なツールと連携するか、画像生成用プロンプト・必要素材・未制作箇所を正直に一覧化し、完成扱いにしない。
- 写真の置換が優先だが、実在の医院・スタッフ・設備・アクセス・症例・治療実績を捏造しない。元画像の真正性が確認できない場合は再撮影・提供待ちを明示する。
- 元画像の保存・ロールバック方法を確保し、既存公開用mainは変更しない。
- ロゴは原則維持。無断で別のロゴに作り替えない。

## コードから確認できた現状（画像の画質/被写体は未検証）
`index.html` に `<img>` が **43 箇所**、`src` に指定された画像は **29 種類（ロゴ含む）**。この数字はHTML内のimg要素のみ。CSS background-image、動画ポスター、他ページ、JS動的画像も追加調査する。

| 区分 | 現行ファイル候補 | 対応方針 |
|---|---|---|
| 維持・正式素材 | `logo.png` | 医院ロゴ。原則変更せず、色・余白・形式の最適化のみ。 |
| FV・人物イメージ | `fv_person.jpg`, `family.jpg`, `seniors.jpg`, `senior_w.jpg`, `smile0.jpg`, `smile_close.jpg`, `woman_smile2.jpg`, `smile_woman.jpg` | 写真の役割を再定義し、同じ人物・同じ顔・似た構図の乱用を避けたオリジナル素材に刷新。人物は実在のスタッフとして扱わない。 |
| 治療イメージ | `implant.jpg`, `implant_model.jpg`, `implant_3d.jpg`, `whitening.jpg`, `ortho.jpg`, `ortho2.jpg`, `ortho_case.jpg`, `snoring.jpg`, `sleep2.jpg`, `denture.jpg` | 専門領域に即したビジュアルを個別制作。症例や実績のように見える画像は実データ/許諾がない限り使用しない。 |
| 医療・ケア | `hygienist.jpg`, `hygienist2.jpg`, `exam.jpg`, `ct.jpg`, `dentist2.jpg`, `brush_bamboo.jpg` | 診療行為・医療機器の正確さを優先。特定医院の設備/医師として見えるものは実写確認済み素材を使用。その他は一般的なイメージであることを明確にする。 |
| 実際の施設・アクセス | `station.jpg`, `platform.jpg`, `corridor_warm.jpg`, `reception.jpg` | 実際の道順や院内の写真は原則実写のみ。既存素材の権利と真正性を検証し、必要に応じて再撮影を依頼。生成画像で現地案内を偽装しない。 |

現行 src 一覧（確認用。内容の一致・権利は画像を目視で確認して判断）:
- `img/logo.png`
- `img/implant.jpg`
- `img/snoring.jpg`
- `img/whitening.jpg`
- `img/seniors.jpg`
- `img/ortho.jpg`
- `img/fv_person.jpg`
- `img/platform.jpg`
- `img/family.jpg`
- `img/ct.jpg`
- `img/station.jpg`
- `img/corridor_warm.jpg`
- `img/reception.jpg`
- `img/hygienist.jpg`
- `img/exam.jpg`
- `img/sleep2.jpg`
- `img/denture.jpg`
- `img/hygienist2.jpg`
- `img/smile_close.jpg`
- `img/implant_model.jpg`
- `img/smile0.jpg`
- `img/woman_smile2.jpg`
- `img/smile_woman.jpg`
- `img/ortho_case.jpg`
- `img/ortho2.jpg`
- `img/senior_w.jpg`
- `img/dentist2.jpg`
- `img/brush_bamboo.jpg`
- `img/implant_3d.jpg`

## アートディレクション
テーマ: Quiet Confidence / 上質な自然光 × 清潔な静けさ × 医療への信頼。
参考サイトの空気感を観察し、構図・余白・タイポ・アニメーションに一貫性を持たせる。参考サイトの写真・ロゴ・テキスト・コードはコピーしない。
- 白/ニュートラルグレー/温かみのあるオフホワイト/深いネイビーを軸に、必要な青を抑制して洗練させる。
- クリニック紹介でよくある「白衣モデルの整列」「歯の3Dアイコンだらけ」「全員が正面を向いて不自然に笑う」テンプレート感を避ける。
- 各画像の構図に目的を持たせる。文字配置側に安全余白を取り、端末別にトリミングを設計。
- 高級感は被写体よりも光・質感・色温度・アングル・編集一貫性で表現する。
- 医療の現実性を優先し、不自然な歯並び/指/器具/解剖/診療手順を厳しく点検。

## 画像生成/選定の制作メニュー
1. **ファーストビュー:** PC 1920×1080を基準とし、必要なら別構図のSP縦版も制作。ヒーロー文字の邪魔をせず、見る人が安心できる自然な人物/抽象的な上質空間。実際の医院として偽装しない。
2. **医院の理念・安心感:** 年齢や性別に偏りすぎない自然な日常の表情・生活風景、品のある実写調。患者個人の実写実績として扱わない。
3. **ホワイトニング:** 清潔感のある自然な笑顔/治療の一般イメージ。強調しすぎた白い歯、ビフォーアフター風の捏造は禁止。
4. **インプラント:** 治療内容を誤解させない医療監修可能な模型・抽象的なイメージ。架空の手術・症例を実例と称さない。
5. **矯正:** マウスピース/矯正の一般イメージ。特定製品と誤認させるロゴや構造は監修を要する。
6. **いびき治療:** 穏やかな睡眠環境の一般イメージ。治療効果を保証する表現にしない。
7. **予防歯科・ケア:** オーラルケア/歯ブラシ/衛生の上質な一般写真。スタッフや医院の実景ではないことを管理。
8. **医院/スタッフ/設備/駅アクセス:** 認証済みの院内・スタッフ・設備・経路の本物の写真を調達。必要なら撮影指示書とカットリストを作成。
9. **コラム:** 記事テーマに合わせて独立した写真・図を制作。患者症例や他院実写を混在させない。

## 制作時の共通画像生成プロンプトの核
**English art direction (adapt subject per section):**
"Premium editorial healthcare photography for a refined Japanese dental clinic website, elegant contemporary Japanese aesthetic, calm trustworthy atmosphere, authentic subtle emotions, natural skin and realistic dental anatomy, soft directional daylight, restrained navy and warm ivory color palette, architectural negative space for typography, cinematic but understated depth, tactile realism, sophisticated art direction, high-resolution photographic quality, no text, no watermarks, no visual clutter, no exaggerated smiles, no uncanny AI aesthetics, no fake clinic identity, no misrepresented before-after results."
- セクションごとに subject / camera angle / framing / lighting / PC/SP crop / text safe area を具体的に指示。
- AI生成画像は実際の医院・医師・設備・駅・症例の証拠画像にしない。必要な箇所には写真の監修や実素材の提供を求める。
- 出力した画像は欠陥確認（手指・歯・器具・顔・不自然な影・文字化け）、権利確認を通過したものだけ採用。

## 実装・納品基準
- すべての現行画像使用箇所を走査し、場所→旧画像→新画像→状態→出典/権利→alt→PC/SPクロップの台帳を作成。
- 新画像をリポジトリへ保存（例: `img/redesign/`）。元素材のライセンス/許諾と生成履歴を管理。不要なオリジナル画像を公開リポジトリに入れない。
- 画像生成時はWebP/AVIFも用意し、適切なフォールバック、`srcset` / `sizes`、width/height、FV優先読み込み、下層lazy、適切なaltを実装。
- 可能な限り画像を単独ファイルで管理し、文字/CTAはHTMLとしてアクセシブルに重ねる。
- PC/SPの比較スクリーンショットを撮影し、トリミング、読みやすさ、画像解像度、余白・配色を検証。
- 新画像が用意できない重要箇所は完成扱いにせず、`needs-real-photo` または `needs-image-generation` と記載。
- 既存の各画像に対する**差し替え反映結果の一覧**と、実装したファイル一覧を提出する。最後に画像参照切れ・404が0件であることを確認する。

## 作業順序
現行全ページ画像監査 → 画像構成案/ショットリスト → 画像生成・撮影素材の整理 → 画像最適化 → 実際のコード差し替え → PC/SP実機検証 → Before/Afterと未完成箇所の報告。
