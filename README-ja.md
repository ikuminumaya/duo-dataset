# DUO: Dialogue dataset with User subjective and Objective evaluations

DUO データセットは，SIGDIAL 2025 採択論文 [*How Stylistic Similarity Shapes Preferences in Dialogue Dataset with User and Third Party Evaluations*](https://aclanthology.org/2025.sigdial-1.15/) で導入された対話データセットです。

本データセットには，EmpatheticDialogues (ED) \[[Rashkin+'19](https://aclanthology.org/P19-1534/)\] および Wizard of Wikipedia (WoW) \[[Dinan+'19](https://arxiv.org/abs/1811.01241)\] に基づき，MTurk 上で収集されたオープンドメイン対話が含まれます。

各対話には，話者本人による主観評価と，第三者のアノテーターによる客観評価が付与されています。

日本語データは，Yahoo!クラウドソーシングを通じて収集されたもので，会誌『自然言語処理』32巻4号に掲載された論文「[スタイル類似の知覚主体が対話評価に与える影響](https://www.jstage.jst.go.jp/article/jnlp/32/4/32_1241/_article/-char/ja)」で詳述されており，DUO データセットの日本語拡張となっています。

ジャーナル版では，英語対話に新たな客観評価を追加しているため，本リポジトリで公開している一部スコアは SIGDIAL 2025 論文で報告した値と異なります。

## 統計情報

**基本統計量**

|                              | 英語                 |                     | 日本語               |                   |
|------------------------------|:----------------------:|:-------------------:|:----------------------:|:-----------------:|
|                              | **ED**                 | **WoW**             | **ED**                 | **WoW**           |
| 対話数          | 157                    | 157                 | 68                     | 73                |
| 客観評価のついた対話数 | 70 | 71 | 45 | 45 |
| 参加者の数       | 34                     | 34                  | 52                     | 52                |
| 発話数         | 3,148                  | 3,302               | 1,360                  | 1,533             |
| 単語数             | 44,640                 | 63,157              | 23,046                 | 35,524            |
| 感情の数    | 30                     | -                   | 28                     | -                 |
| トピックの数      | -                      | 133                 | -                      | 73                |
| 対話の長さ(最小-最大)     | 20-23                  | 20-23               | 20                     | 21                |
| 対話の長さの平均 | 20.05        | 21.03               | 20                     | 21                |
| 発話あたりの文字数(min-max)    | 1-76                   | 1-146               | 1-84                   | 2-76              |
| 発話あたりの文字数の平均     | 14.18                  | 19.13               | 16.95                  | 23.17             |
| 語彙数                   | 3,819                  | 6,439               | 2,707                  | 3,669             |
| タイプ・トークン数             | 0.086                  | 0.10                | 0.117                  | 0.103             |
| Herdan’s C                   | 0.77                   | 0.79                | 0.787                  | 0.783             |


**主観評価（平均 ± 標準偏差）**

|                      | 英語                 |                     | 日本語               |                   |
|----------------------|:----------------------:|:-------------------:|:----------------------:|:-----------------:|
|                      | **ED**                 | **WoW**             | **ED**                 | **WoW**           |
| 好ましさ           | 3.47 ± 1.31            | 3.96 ± 1.11         | 3.53 ± 1.00            | 3.82 ± 1.06       |
| 一貫性          | 4.40 ± 0.80            | 4.57 ± 0.68         | 4.13 ± 0.83            | 3.93 ± 1.13       |
| スタイル類似度 | 3.32 ± 1.31            | 3.86 ± 1.06         | 3.47 ± 0.95            | 3.59 ± 1.09       |
| 共感度              | 3.87 ± 1.19            | –                   | 3.74 ± 0.99            | –                 |
| 魅力度         | –                      | 3.87 ± 1.18         | –                      | 3.62 ± 1.08       |


**客観評価（平均 ± 標準偏差）**

|                      | 英語                 |                     | 日本語               |                   |
|----------------------|:----------------------:|:-------------------:|:----------------------:|:-----------------:|
|                      | **ED**                 | **WoW**             | **ED**                 | **WoW**           |
| 好ましさ           | 3.55 ± 0.75            | 3.55 ± 0.72         | 3.63 ± 0.68            | 3.73 ± 0.55       |
| 一貫性          | 4.60 ± 0.38            | 4.54 ± 0.54         | 3.82 ± 0.45            | 3.96 ± 0.52       |
| スタイル類似度 | 3.50 ± 0.54            | 3.41 ± 0.70         | 3.25 ± 0.77            | 3.52 ± 0.66       |
| 共感度              | 4.14 ± 0.55            | –                   | 3.53 ± 0.63            | –                 |
| 魅力度         | –                      | 3.80 ± 0.73         | –                      | 3.67 ± 0.55       |

## データ形式

| キー                                             | 型               | 説明                                                                                   |
|--------------------------------------------------|------------------|----------------------------------------------------------------------------------------|
| `dialogue_id`                                    | string           | 対話 ID                                                                     |
| `setting`                                        | string           | データセットの設定（`"ed"` = EmpatheticDialogues, `"wow"` = Wizard of Wikipedia）     |
| `model`                                          | string           | 対話システムとして用いたモデル名                                                       |
| `prompt`                                         | string           | スタイル制御プロンプト（`"aligned"` / `"neutral"` / `"not_aligned"`）                 |
| `emotion`                                        | string           | ユーザが選択した感情ラベル                                                              |
| `episode`                                        | string           | 感情に対応するユーザの短いエピソード                                               |
| `objective_evaluation.preference`                | float            | 第三者のアノテーターによる “好ましさ” の平均スコア                                     |
| `objective_evaluation.stylistic_similarity`      | float            | 第三者のアノテーターによる “スタイル類似度” の平均スコア                          |
| `objective_evaluation.consistency`               | float            | 第三者のアノテーターによる “一貫性” の平均スコア                                   |
| `objective_evaluation.empathy`                   | float            | 第三者のアノテーターによる “共感度” の平均スコア                                       |
| `objective_evaluation.engagingness`              | float            | 第三者のアノテーターによる “魅力度” の平均スコア                                  |
| `objective_evaluation.preference_scores`         | list of float    | 3 名のアノテーターそれぞれの “好ましさ” スコア                                       |
| `objective_evaluation.stylistic_similarity_scores` | list of float  | 3 名のアノテーターそれぞれの “スタイル類似度” スコア                             |
| `objective_evaluation.consistency_scores`        | list of float    | 3 名のアノテーターそれぞれの “一貫性” スコア                                      |
| `objective_evaluation.empathy_scores`            | list of float    | 3 名のアノテーターそれぞれの “共感度” スコア                                          |
| `objective_evaluation.engagingness_scores`       | list of float    | 3 名のアノテーターそれぞれの “魅力度” スコア                                     |
| `subjective_evaluation.preference`               | float            | ユーザ本人による “好ましさ” スコア                                                   |
| `subjective_evaluation.stylistic_similarity`     | float            | ユーザ本人による “スタイル類似度” スコア                                         |
| `subjective_evaluation.consistency`              | float            | ユーザ本人による “一貫性” スコア                                                  |
| `subjective_evaluation.empathy`                  | float            | ユーザ本人による “共感度” スコア                                                      |
| `subjective_evaluation.engagingness`             | float            | ユーザ本人による “魅力度” スコア                                                 |
| `dialogue`                                       | list of dict     | 各対話に含まれる発話のリスト                                                           |
| `dialogue[].message_id`                          | int              | 発話 ID                                                                            |
| `dialogue[].user_id`                             | string           | 話者が人間である場合のユーザ ID                                                        |
| `dialogue[].system_id`                           | string           | 話者がシステムである場合のシステム ID                                                  |
| `dialogue[].speaker`                             | string           | 話者の役割（`"Human"` または `"Bot"`）                                                 |
| `dialogue[].message`                             | string           | 発話内容                                                                               |
```
{
  "dialogue_id": "0000",
  "setting": "ed",
  "model": "gpt-4o",
  "prompt": "neutral",
  "emotion": "Excited",
  "episode": "I'm moving out west, I'm excited about it.",
  "objective_evaluation": {
    "preference": 3.67,
    "stylistic_similarity": 3.67,
    "consistency": 4.33,
    "empathy": 4.0,
    "preference_scores": [
      3.0,
      4.0,
      4.0
    ],
    "stylistic_similarity_scores": [
      4.0,
      3.0,
      4.0
    ],
    "consistency_scores": [
      4.0,
      5.0,
      4.0
    ],
    "empathy_scores": [
      3.0,
      5.0,
      4.0
    ]
  },
  "subjective_evaluation": {
    "preference": 1.0,
    "stylistic_similarity": 4.0,
    "consistency": 5.0,
    "empathy": 4.0
  },
  "dialogue": [
    {
      "message_id": 0,
      "user_id": "0000",
      "speaker": "Human",
      "message": "I'm going to be making a big move in 2 weeks."
    },
    {
      "message_id": 1,
      "system_id": "0000",
      "speaker": "Bot",
      "message": "That's exciting! How are you feeling about it?"
    },
    .....   
  ]
}
```

収集されたデータ中に話者に関連した人物名が含まれている場合は，すべて <name> によって匿名化されています。

>[!CAUTION]
>本データセットを利用する際は，以下の点にご注意ください。
>
>* 本データセットから個人を特定しようとしないでください。
>* 本データセットには，文化的・思想的にセンシティブな内容が含まれている可能性があります。

## 引用
```
@inproceedings{numaya2025stylesim,
    title = "How Stylistic Similarity Shapes Preferences in Dialogue Dataset with User and Third Party Evaluations",
    author = "Ikumi, Numaya  and
      Shoji, Moriya  and
      Shiki, Sato  and
      Reina, Akama  and
      Jun, Suzuki",
    booktitle = "In Proceedings of the 26th Annual Meeting of the Special Interest Group on Discourse and Dialogue",
    month = "Aug",
    year = "2025",
    publisher = "Association for Computational Linguistics",
}

@article{numaya2025,
  title={スタイル類似の知覚主体が対話評価に与える影響},
  author={沼屋 征海 and 守屋 彰二 and 佐藤 志貴  and 赤間 怜奈 and 鈴木 潤},
  journal={自然言語処理},
  volume={32},
  number={4},
  pages={1241-1271},
  year={2025},
  doi={10.5715/jnlp.32.1241}
}
```

## ライセンス
本コーパスは，対話設定ごとに以下のライセンスのもとで提供されます：
* EmpatheticDialogues 設定： [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)  
* Wizard of Wikipedia 設定： [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0)  

対話設定ごとに異なるライセンスが適用される点にご注意ください。
