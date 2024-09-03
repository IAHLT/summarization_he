# Text Summarization in Hebrew


האיגוד הישראלי לטכנולוגיות שפת אנוש
الرابطة الإسرائيلية لتكنولوجيا اللغة البشرية

The Israeli Association of Human Language Technologies
https://www.iahlt.org

## Project Scope

The goal of this project is to create a high-quality, human-annotated dataset
for text summarization in Hebrew, with a focus on ensuring inter-annotator
agreement (IAA) to maintain consistency and quality.

## Guidelines Summary

The summarization guidelines at IAHLT follow a three-step approach:

1. **Familiarization**: Thoroughly read the article to understand its main
themes and details.
2. **Identification**: Identify the central point or main message of the
article.
3. **Drafting**: Write a concise and coherent summary that captures the essence
of the article.

The guidelines emphasize objectivity, clear language, and preservation of the
original context. Special rules are in place for different types of articles,
such as opinion pieces and list-based articles.

The main guidelines are included in `guidelines.pdf`.
We summarized the documents using two distinct approaches, indicated as "gold" and "silver" in the `source` field (see below):

#### Gold
This approach follows the standard summarization process outlined in the `guidelines.pdf` file.

#### Silver
For this approach, we first used a generative large language model to create the summary, including 
supporting sentences from the text for each summary sentence. An annotator then reviewed and corrected 
the summary according to the instructions in the `silver_guidelines.pdf` file.


## Contents

The release includes the following files:

- summarization-7-heb.jsonl.zip: article summaries
- summarization-7-heb-iaa.tsv: interannotator agreement scores
- guidelines.pdf: The general guidelines used for summarization
- silver_guidelines.pdf: The guidelines used for silver.

This release contains 5368 summaries of 5076 unique articles.
Gold/Silver summary distribution:

| Type | Summaries |
| :---   | ---: |
| Only gold | 2082 | 
| Only silver | 2944 | 
| Silver + Gold | 50 | 

The articles come from the following sources:

| Source | Summaries |
| :---   | ---: |
| Bagatz | 68 |
| Israel Hayom | 2182 |
| Knesset | 396 |
| Weizmann | 945 |
| Wikipedia | 1777 |

## Format

### Summary data

The data is provided in JSON Lines (JSONL) format, with each line representing a record that contains the following
fields:

- `text_raw`: The full text of the original article in Hebrew
- `metadata` Various article metadata fields: `source`,
  `url`, `doc_id`, `type`, `annotator`, and optionally 
  `ai_summary` (only available when the `type` is silver, and it contains 
   the summary that was originally generated by the large language model). Some of the
   documents also have the `title` and `genre` fields.
- `summary`: The human-annotated summary of the article in Hebrew
- `user`: The handle of the annotator

## Inter-annotator agreement

Inter-annotator agreement is calculated using [BERTScore] with [AlephBERT]; see
the references for detailed information. Multiply-summarized articles have all
summaries compared pairwise, and precision, recall, and F1 scores are reported
in TSV format with the following columns:

- `user_id1`: the first annotator of the pair
- `user_id2`: the second annotator of the pair
- `doc_id`: the id of the summarized document
- `precision`: the precision output by BERTScore
- `recall`: the precision output by BERTScore
- `F1`: the precision output by BERTScore

<br/>

[BERTScore]: https://arxiv.org/abs/1904.09675 <br/>
[AlephBERT]: https://arxiv.org/abs/2104.04052  <br/>

## Acknowledgements

We would like to thank all the people who contributed to this corpus:

Alon Mannor <br/>
Amir Zeldes <br/>
Ariela Ben-Dov <br/>
Emmanuelle Kowner <br/>
Gil Godinger <br/>
Israel Landau<br/>
Leaya Porter<br/>
Kfir Bar<br/>
Maayan Orner<br/>
Nick Howell<br/>
Noam Ordan<br/>
Omer Strass<br/>
Rut Rosner<br/>
Rotem Ecker<br/>
Shahar Adar<br/>
Shira Wigderson<br/>
Tamar Levi<br/>
Yifat Ben Moshe<br/>

