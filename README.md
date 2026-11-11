# Topic Modeling of MyIcon+ App Reviews: BERTopic vs. Top2Vec with IndoBERT Embeddings

Muhammad Rama Refiando, Fitriyani
Paper: ICIMCIS 2026 (accepted), "Topic Modeling of MyIcon+ App Reviews: Comparing BERTopic and Top2Vec With IndoBERT Embeddings"

Code and supporting files for the paper *"Topic Modeling of MyIcon+ App Reviews: Comparing BERTopic and Top2Vec
with IndoBERT Embeddings"*.

Both algorithms use the same IndoBERT document embeddings (`indolem/indobert-base-uncased`, mean pooling), the same
UMAP/HDBSCAN tuning space, and the same selection rule. The notebook covers preprocessing, embedding, tuning, final
models, evaluation (C_v, NPMI, topic diversity, ten-seed stability, swapped-parameter control), topic comparison
(Jaccard, ARI, NMI), and topic interpretation.

## Contents

| Path | Description |
|---|---|
| `topic_modeling_myiconplus.ipynb` | Full pipeline with the outputs of the reported run (notebook comments in Indonesian). |
| `requirements.txt` | Library versions used for the reported results. |
| `dictionaries/` | Domain, typo, and phrase dictionaries, stopword list (274 words), negation words, final configuration. |
| `results/` | Topic tables, stability and agreement summaries, coded sample of 100 negative outlier reviews, figures. |

The table at the top of the notebook maps each table and figure in the paper to a notebook section.

## Data

The review dataset is not redistributed. Reviews of the MyIcon+ app (Google Play id
`id.co.iconpln.icmn.customer`) from April 3, 2023 to March 15, 2026 can be collected with `google-play-scraper`;
the notebook uses the rating, date, and review text only.

The general slang lexicon is taken from the Colloquial Indonesian Lexicon
(https://github.com/nasalsabila/kamus-alay) and downloaded by the notebook. The dictionaries in `dictionaries/` are
the domain-specific additions; merged with that lexicon they give the 4,385-entry normalization dictionary.

## Reproducibility

- Run the notebook top to bottom on Google Colab with a GPU. Set the data path in the **Konfigurasi** cell.
- UMAP results depend on the numpy and numba versions. Section 1.2 of the notebook installs the pinned versions and
  restarts the runtime once; with newer versions the clustering differs.
- Seeds: 42 for the final models; 42, 7, 123, 2024, 777, 1, 13, 99, 314, and 2026 for the stability analysis.
