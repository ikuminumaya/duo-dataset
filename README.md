# DUO: Dialogue dataset with User subjective and Objective evaluations

The DUO dataset is introduced in our SIGDIAL 2025 paper, [*How Stylistic Similarity Shapes Preferences in Dialogue Dataset with User and Third Party Evaluations*](https://aclanthology.org/2025.sigdial-1.15/)
.

This dataset contains dialogues collected on MTurk under open-domain dialogue settings, including EmpatheticDialogues (ED) \[[Rashkin+'19](https://aclanthology.org/P19-1534/)\] and Wizard of Wikipedia (WoW) \[[Dinan+'19](https://arxiv.org/abs/1811.01241)\].

Each dialogue is annotated with subjective evaluations from the user themselves and objective evaluations from third-party annotators.

The Japanese data, collected via Yahoo! Crowdsourcing, are described in an article in the Journal of Natural Language Processing (Vol. 32, No. 4) (Japan), [*Dialogue Evaluation Is Affected by How Raters Perceive Stylistic Similarity*](https://www.jstage.jst.go.jp/article/jnlp/32/4/32_1241/_article/-char/ja), and constitute a Japanese extension of the DUO dataset.

In the journal version, we added objective evaluations to English dialogues , so some of the scores reported here differ from those in the SIGDIAL 2025 paper.

## Statistics
**Basic Statistics**
|                      | English                 |                     | Japanese               |                   |
|----------------------|:--------------------:|:-------------------:|:--------------------:|:-------------------:|
|                      | **ED**               | **WoW**             | **ED**               | **WoW**             |
|Number of dialogues|157|157|68|73|
|Number of dialogues with objective evaluations|70|71|45|45|
|Number of participants|34|34|52|52|
|Number of utterances|3,148|3,302|1,360|1,533|
|Number of tokens|44,640|63,157|23,046|35,524|
|Number of unique emotions|30|-|28|-|
|Number of unique topics|-|133|-|73|
|Dialogue length(min-max)|20-23|20-23|20|21|
|Avg. Number of utterances per dialogue|20.05|21.03|20|21|
|Utterance length(min-max)|1-76|1-146|1-84|2-76|
|Avg. of utterance length|14.18|19.13|16.95|23.17|
|Vocabulary|3,819|6,439|2,707|3,669|
|Type-token ratio|0.086|0.10|0.117|0.103|
|Herdan’s C|0.77|0.79|0.787|0.783|


**Subjective evaluations (mean ± SD)**

|                      | English                 |                     | Japanese               |                   |
|----------------------|:--------------------:|:-------------------:|:--------------------:|:-------------------:|
|                      | **ED**               | **WoW**             | **ED**               | **WoW**             |
| Preference   | 3.47 ± 1.31    | 3.96 ± 1.11     | 3.53 ± 1.00    | 3.82 ± 1.06     |
| Consistency   | 4.40 ± 0.80    | 4.57 ± 0.68     | 4.13 ± 0.83    | 3.93 ± 1.13     |
| Stylistic similarity   | 3.32 ± 1.31    | 3.86 ± 1.06     | 3.47 ± 0.95    | 3.59 ± 1.09     |
| Empathy    | 3.87 ± 1.19    | –               |3.74 ± 0.99    | –               |
| Engagingness  | –              | 3.87 ± 1.18     | –              | 3.62 ± 1.08     |



**Objective evaluations (mean ± SD)**

|                      | English                 |                     | Japanese               |                   |
|----------------------|:--------------------:|:-------------------:|:--------------------:|:-------------------:|
|                      | **ED**               | **WoW**             | **ED**               | **WoW**             |
| Preference   | 3.55 ± 0.75    | 3.55 ± 0.72     |3.63 ± 0.68    | 3.73 ± 0.55     |
| Consistency   | 4.60 ± 0.38    | 4.54 ± 0.54     | 3.82 ± 0.45    | 3.96 ± 0.52     |
| Stylistic similarity   | 3.50 ± 0.54    | 3.41 ± 0.70     | 3.25 ± 0.77    | 3.52 ± 0.66     |
| Empathy    | 4.14 ± 0.55    | –               | 3.53 ± 0.63    | –               |
| Engagingness  | –              | 3.80 ± 0.73     | –              | 3.67 ± 0.55     |

## Data Format
| Key                                             | Type             | Description                                                                          |
|-------------------------------------------------|------------------|--------------------------------------------------------------------------------------|
| `dialogue_id`                                     | string           | Unique identifier for the dialogue                                                   |
| `setting`                                       | string           | Dataset setting (`"ed"` for EmpatheticDialogues, `"wow"` for Wizard of Wikipedia) |
| `model`                                         | string           | Name of the model used as the dialogue system                                      |
| `prompt`                                        | string           | Style control prompt (`"aligned"` / `"neutral"` / `"not_aligned"`)                            |
| `emotion`                                       | string           | Emotion label selected by the user                                                   |
| `episode`                                       | string           | User’s short personal episode related to the emotion                                  |
| `objective_evaluation.preference`               | float   | Mean “Preference” score from third party annotators                                   |
| `objective_evaluation.stylistic_similarity`     | float   | Mean “Stylistic similarity” score from third party annotators                        |
| `objective_evaluation.consistency`              | float   | Mean “Consistency” score from third party annotators                                  |
| `objective_evaluation.empathy`                  | float   | Mean “Empathy” score from third party annotators                                      |
| `objective_evaluation.engagingness`                  | float   | Mean “Engagingness” score from third party annotators                                      |
| `objective_evaluation.preference_scores`        | list of float    | Individual “Preference” scores from each of the three annotators                     |
| `objective_evaluation.stylistic_similarity_scores` | list of float  | Individual “Stylistic similarity” scores from each of the three annotators           |
| `objective_evaluation.consistency_scores`       | list of float     | Individual “Consistency” scores from each of the three annotators                    |
| `objective_evaluation.empathy_scores`           | list of float     | Individual “Empathy” scores from each of the three annotators                        |
| `objective_evaluation.engagingness_scores`           | list of float     | Individual “engagingness” scores from each of the three annotators                        |
| `subjective_evaluation.preference`              | float              | “Preference” scores from the user                                                       |
| `subjective_evaluation.stylistic_similarity`    | float              | “Stylistic similarity” scores from the user                                             |
| `subjective_evaluation.consistency`             | float              | “Consistency” scores from the user                                                      |
| `subjective_evaluation.empathy`                 | float              | “Empathy” scores from the user                                                          |
| `subjective_evaluation.engagingness`                 | float              | “Engagingness” scores from the user                                                          |
| `dialogue`                                      | list of dict  | List of utterances in the dialogue                                                   |
| `dialogue[].message_id`                         | int              | Identifier for each utterance                                                        |
| `dialogue[].user_id`                            | string           | User ID when the speaker is the human                                                 |
| `dialogue[].system_id`                          | string           | System ID when the speaker is the bot                                                 |
| `dialogue[].speaker`                            | string           | Role of the speaker (`"Human"` or `"Bot"`)                                           |
| `dialogue[].message`                            | string           | Content of the utterance                                                             |
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
Any real names contained in the collected data are anonymized and replaced with `<name>`.

> [!CAUTION]
>Please be aware of the following points when using this dataset.
>
>* Do not attempt to identify individuals from the data in this dataset.
>* The dataset may contain culturally or ideologically sensitive content.


## Citation
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

@article{沼屋2025,
  title={スタイル類似の知覚主体が対話評価に与える影響},
  author={沼屋 征海 and 守屋 彰二 and 佐藤 志貴  and 赤間 怜奈 and 鈴木 潤},
  journal={自然言語処理},
  volume={32},
  number={4},
  pages={},
  year={2025},
  doi={}
}

```

## LICENSE
This corpus is provided under the following licenses depending on the dialogue setting:
* EmpatheticDialogues setting: [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)  
* Wizard of Wikipedia setting: [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0)  

This corpus is made available under different licenses for each dialogue setting.

