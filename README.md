# DUO: Dialogue dataset with User subjective and Objective evaluations

The DUO dataset is introduced in our paper at SIGDIAL 2025, *How Stylistic Similarity Shapes Preferences in Dialogue Dataset with User and Third Party Evaluations.*

This dataset contains dialogues collected on MTurk under open-domain dialogue settings, including EmpatheticDialogues \[[Rashkin+'19](https://aclanthology.org/P19-1534/)\] and Wizard of Wikipedia \[[Dinan+'19](https://arxiv.org/abs/1811.01241)\].

Each dialogue is annotated by subjective evaluations from the user themselves and objective evaluations from third-party annotators.

## Statistics
**Basic Statistics**
||EmpatheticDialogues|Wizard of Wikipedia|
|-|----|----|
|Number of dialogues|157|157|
|Number of dialogues with objective evaluations|50|46|
|Number of participants|34|34|
|Number of utterances|3,148|3,302|
|Number of tokens|44,640|63,157|
|Number of unique emotions|30|-|
|Number of unique topics|-|133|
|Dialogue length(min-max)|20-23|20-23|
|Avg. Number of utterances per dialogue|20.05|21.03|
|Utterance length(min-max)|1-76|1-146|
|Avg. of utterance length|14.18|19.13|
|Vocabulary|3,819|6,439|
|Type-token ratio|0.086|0.10|
|Herdan’s C|0.77|0.79|
|Language|English|English|


**Subjective evaluations (mean ± SD)**

| Label   | EmpatheticDialogues| Wizard of Wikipedia |
|:--------|:---------------|:----------------|
| Preference   | 3.47 ± 1.31    | 3.96 ± 1.11     |
| Consistency   | 4.40 ± 0.80    | 4.57 ± 0.68     |
| Stylistic similarity   | 3.32 ± 1.31    | 3.86 ± 1.06     |
| Empathy    | 3.87 ± 1.19    | –               |
| Engagingness  | –              | 3.87 ± 1.18     |


**Objective evaluations (mean ± SD)**

| Label   | Empathetic Dialogue| Wizard of Wikipedia |
|:--------|:---------------|:----------------|
| Preference   | 3.50 ± 0.79    | 3.56 ± 0.72     |
| Consistency   | 4.55 ± 0.42    | 4.49 ± 0.57     |
| Stylistic similarity   | 3.51 ± 0.54    | 3.18 ± 0.73     |
| Empathy    | 4.10 ± 0.58    | –               |
| Engagingness  | –              | 3.62 ± 0.75     |

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


```

## LICENSE
This corpus is provided under the following licenses depending on the dialogue setting:
* EmpatheticDialogues setting: [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)  
* Wizard of Wikipedia setting: [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0)  

This corpus is made available under different licenses for each dialogue setting.

