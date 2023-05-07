# LLM_DD_Challenge
Dashboard for LLM Drug Discovery Challenge.

# ルール
※ 状況の変化に応じて随時更新。質問は随時 @souyakuchan へ。

## 総則
- 所定の創薬標的に対し、大規模言語モデル (LLM) を利用して **必ず LLM 自身が化合物の提案もしくは選別をするステップを含めたワークフローで** 10 個の活性化合物候補を提案すること。１参加者の応募は１セットまで。(提出期間中の上書きは可)

- 提出〆切は ~~2023/04/30~~ 2023/05/31 24:00:00 (JST)
  - [参加登録フォーム](https://forms.gle/n9wDuje1QjNKAN968)

- 提出物　(※ 具体的な提出方法はまた別途参加者に告知する)
  - LLM との対話内容の Markdown出力 (※ 対話形式では無い場合、処理一式を記載したもの) → GitHub･Gist などにアップロード
  - 計算処理を LLM の外で実行した場合、そのコード → GitHub･Gist などにアップロード
  - 提案化合物 10 個 → SMILES 形式で提出

- 評価方法: 提案化合物についての参加者同士の相互評価と審査員による評価、LLM 活用度や定量指標等を組み合わせる (後述)

## 標的
[CACHE #4](https://cache-challenge.org/challenges/Finding-ligands-targeting-the-TKB-domain-of-CBLB) に乗っかる形で、CBL-B タンパク質の TKB ドメインを標的とする。

![image](https://user-images.githubusercontent.com/33997698/228606335-5be8fbbf-d982-4202-b7f2-7e55ce864eb5.png)

- 既知の結合化合物として [約 900 個](https://cache-challenge.org/sites/default/files/challenge/CBLB_inhibitors_vsF.sdf) の特許化合物の情報が与えられている。
  - それら既知化合物との構造類似性がなるべく低く高活性なものを目指して新規活性化合物候補を提案すること。
  - 類似性は例えば Morgan fingerprint での Tanimoto 係数などで評価。

- 既知のタンパク質-リガンド複合体構造あり。[8GCY.PDB](https://www.rcsb.org/structure/8GCY)
  - 同じ結合部位を狙うこと。

- 市販化合物ライブラリを用いる場合、[Enamine Hit Locator Library](https://enamine.net/compound-libraries/diversity-libraries/hit-locator-library-200) を推奨。※ アッセイ実施するかどうかは未確定だが、在庫的に国内での入手性が高い化合物ライブラリであるため。
  - CACHE 提供の [ライブラリ](http://cache.docking.org/) もあるが、入手性はやや落ちる。

## 細則
- まずは [参加登録](https://forms.gle/n9wDuje1QjNKAN968) をすること。各参加者には参加報酬 (ファイトマネー) として￥10,000 ずつ支給する。 ※ 上限 30 名、先着順
  - GPT-4 API アクセス権の順番が来ていない人には、当イベント開催期間中は私から API アクセス権を提供する。
- 参加報酬を受け取ったプレイヤーの義務:
  - 提出〆切までに提出物一式を提出すること
  - 参加者全員分の提出化合物の評価を評価〆切までに各自実施すること (専用ウェブサイトを用意する)

- 作業ルール:
  - 任意の LLM を使用可、どこかに必ず「LLM に化合物の提案もしくは選別をさせる」ステップを入れること
    - 参加者が単に自分の力で LLM の外で処理した結果を LLM にただ復唱させるだけでは LLM を用いる意味が薄いので、「LLM に考えさせる」ことをなるべく目指すこと
  - LLM に外部知識の入れ知恵や tuning、embedding/retrieval してよい
  - LLM にできない任意の計算処理を LLM の外で実行してよいが、コードを LLM に生成させる等、LLM を活かせているほど加点するかもしれない (詳細はまだこれから検討)
    - OSS ライブラリの利用やバグ取り編集は可
    - ドッキングを行う場合、PDBファイルの準備や座標指定は手でやってよい
  - 情勢の変化が早いため、状況に応じ必要な場合ルール変更や追加を行う可能性があるが受け入れること (〆切の変更等も含む)
  - 採点: 参加者間相互評価と審査員評価の得点を基本点として、既知化合物との類似性指標や「LLM 活用度」を加味する
    - 構造式を多角的に評価して頂く
    - 本イベントでは提案化合物の実際の活性の評価のためのアッセイ実験は必ずしも実施しない
    - ~~審査員はこれから有償にて募集する~~ ５名の審査員を確保した

- 評価項目
  - 化学的な安定性、反応性 (Chemical stability or Reactivity)
  - 合成容易性 (Synthetic accessibility)
  - 合成展開可能性 (Synthetic amenability to diverse derivatizations)
  - 忌避構造 (Structural alerts)
  - ヒット(活性あり)期待度 (Potential for bioactivity)

- 審査員 (join 順)
  - @rkakamilan (medchem/compchem)
  - @taxyach (medchem)
  - @HattoriLab (structural biologist)
  - @AgroDesign_ (chemist/structural biologist)
  - @isip_tkg (compchem)

- 情報共有促進
  - 創薬における LLM 活用に関して得られた知見の共有を推奨する。[Discussion](https://github.com/souyakuchan/LLM_DD_Challenge/discussions) で共有･議論を。
  - 各人の最終提出化合物は提出〆切前には公開しないこと。
  - Upvote 獲得数の多い参加者も授賞対象とする。

## 賞
- 得点で順位を決め、賞金を授与。
  - 🥇￥80,000
  - 🥈￥50,000
  - 🥉￥30,000
- ソーシャル創薬賞: 本イベント開催中に創薬での LLM 活用に関する知見を [Discussion](https://github.com/souyakuchan/LLM_DD_Challenge/discussions) で共有し、upvote 獲得数の多かった３名に授与。
  - 🏅￥20,000 × ３名

- [アグロデザイン･スタジオ](https://www.agrodesign.co.jp/) 賞
  - 🥇 好きなタンパク質の構造解析
  - 🏅 上位３組 (希望者) に焼肉

- [iSiP](https://corp.i-sip.jp/) 賞
  - 🏅上位３組 (希望者) に焼鳥 (ミシュランビブグルマン選出店)
