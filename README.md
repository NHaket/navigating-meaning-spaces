# Navigating Meaning Spaces

This repository contains all code, analysis notebooks, and supplementary materials supporting the empirical studies presented in the thesis investigating word meaning through a positively eclectic approach combining theoretical frameworks with computational and experimental methods.

**Note**: All participant data (questionnaire responses) are available on the Open Science Framework.

## Repository Structure
```
.
├── Chapter 6/
│   ├── Questionnaire/
│   ├── Word Embeddings/
│   ├── Explanation metrics.doc/
│   └── Description of Contents.txt
├── Chapter 7/
│   └── notebooks/
├── Chapter 8/
│   └── Analysis_Chapter_8.ipynb
└── README.md
```

## Overview

This research employs a 'bottom-up' empirical approach at two levels:

- **Chapter 6**: Word-level semantics using BERT embeddings and questionnaires
- **Chapter 7**: Utterance-level interpretation using discourse-based questionnaires  
- **Chapter 8**: Integration of theoretical frameworks with empirical findings

---

## Chapter 6: Words - Vectors, Questionnaires, and Metrics

This chapter employs 'bottom-up' empirical methods to investigate word-level semantics, combining computational distributional analysis (BERT word embeddings) with qualitative data collection (questionnaires).

### Questionnaire Study Design (`Chapter 6/Questionnaire/`)

**Participants**: n=273 via Prolific

**Target Words**: *weight, planet, theory, friend, freedom, truth, water, computer, education, energy*

**Question Types**:
- **DefQ**: Definitions in participants' own words
- **ExQ**: Examples of what counts as instances of the word
- **CharQ**: Characteristic features defining the word
- **AssocQ**: Associated words and concepts
- **CtxQ**: Contexts where the word is most frequently encountered

**Data**: Complete response data (24 participants per word × 5 question types) available on OSF.

**Purpose**: These questionnaires capture speakers' conscious conceptualizations, extensional boundaries, and folk theories about word meanings, providing qualitative depth to complement computational breadth.

### Word Embeddings (`Chapter 6/Word Embeddings/`)

**Method**: Contextualised BERT embeddings (bert-large-uncased, 768 dimensions) generated from the Spoken British National Corpus 2014 (BNC14: 11.5M tokens, 1,251 conversations). Each target word token received a unique embedding based on a 40-word context window, then was reduced to 2D via PCA and clustered using Gaussian Mixture Models with Silhouette Score optimization.

**Target Words** (n=35 across seven semantic taxonomic categories):

1. **World-Oriented Abstract**: *weight, pressure, electricity, temperature, energy*
2. **World-Oriented Concrete**: *water, planet, cancer, protein, tiger*
3. **Mind-Oriented Abstract Theory-bound**: *theory, system, data, concept, information*
4. **Mind-Oriented Abstract Value-bound**: *truth, freedom, responsibility, knowledge, duty*
5. **Mind-Oriented Abstract Practice-bound**: *family, marriage, education, economy, exam*
6. **Mind-Oriented Concrete Social**: *student, friend, engineer, wife, child*
7. **Mind-Oriented Concrete Material**: *computer, cable, wheel, hat, camera*

#### Subdirectories

**`experiments/`** - Core experimental data
- `wordlist.yaml` - Complete list of 35 target words with taxonomic classifications
- `summary_table.csv` - Aggregated metrics for all words (SelfSim, MEV, Intra-Similarity, Inter-Similarity)
- `context_groups/` - 35 plain text files containing clustered contexts for each word

**`imgs/`** - Visualization outputs
- Individual word directories (e.g., `computer/`, `freedom/`) - PCA plots, cluster dendrograms, embedding visualizations
- `consensus_clustering_full_part[1-3].png` - Complete consensus clustering across all 35 words
- `metricsimage.png` - Summary visualization of BERT metrics
- `word_silhouette.png` - Silhouette analysis for cluster validation

**`notebooks/`** - Jupyter analysis notebooks
- `bnc_conceptual_engineering.ipynb` - Primary analysis extracting BERT embeddings, performing GMM clustering, calculating metrics
- `Figures_Chapter_6.ipynb` - Generates all figures for Chapter 6

#### Metrics Explained

- **SelfSim** (Average Cosine Similarity): How similar all uses of a word are to each other (higher = more consistent usage)
- **MEV** (Maximum Explained Variance): Proportion of variation captured by the first principal component (higher = variation structured along single dominant dimension)
- **Intra-Similarity**: Average similarity within clusters (higher = tighter, more coherent clusters)
- **Inter-Similarity**: Average similarity between clusters (lower = more distinct usage types)

---

## Chapter 7: Mapping Meaning Through Dialogue

This chapter extends empirical investigation to the utterance level, examining how speakers interpret words embedded in naturally occurring dialogue contexts.

### Study Design

**Participants**: Same 273 participants from Chapter 6

**Materials**: For each of the 10 target words, 5 dialogues were selected through cluster-based sampling from the BNC14 corpus (distributed proportionally across BERT-identified clusters to capture the full range of naturally occurring usage patterns).

**Task**: Participants read dialogue excerpts with a target word underlined and answered: *"What do you think is conveyed by [Speaker] in the underlined text?"*

**Coding**: Open-ended responses were coded into four interpretive strategies:
- **PAR** (Paraphrase): Literal restatement of explicit content
- **SIT** (Situational): Interpretation of concrete situational role or real-world function
- **INF** (Inferential): Derivation of implied meanings, background assumptions, or unstated implications
- **EVA** (Evaluative): Identification of speaker's evaluative stance or subjective attitude

**Data**: Complete coded responses (5 dialogues per word, 24 participants per dialogue, PAR/SIT/INF/EVA framework) available on OSF.

**Key Finding**: Context-driven variation within single words substantially exceeds variation between words (interpretive strategies do not vary systematically by lexical item but respond to contextual and pragmatic factors).

### Analysis Notebook (`Chapter 7/notebooks/`)

- `Analysis_Chapter_7.ipynb` - Chi-square tests, effect size calculations (Cramér's V), visualizations

---

## Chapter 8: A Positively Eclectic Approach for Conceptual Engineering

Integrates theoretical frameworks with empirical methods through three complementary strands:

### Strand A: Building Comprehensive Lexical Profiles
Populating PIB Theory (E-, C-, and L-structure) with questionnaire data and BERT embeddings

### Strand B: Predicting Interpretive Strategies  
Testing whether taxonomic categories (orientation, abstractness) predict both:
- Distributional patterns (BERT metrics)
- Comprehension strategies (discourse questionnaires)

### Analysis

`Analysis_Chapter_8.ipynb` performs:
- Statistical tests: ANOVA, Kruskal-Wallis, t-tests, chi-square, linear regression
- Effect size calculations
- Integrated visualizations demonstrating how theoretical and empirical approaches work together

---

## Reproducibility

All notebooks are fully executable and document the complete analytical pipeline from raw data to reported results.

### Technical Requirements

**Software**:
- Python 3.x
- Libraries: pandas, numpy, scipy, matplotlib, seaborn, scikit-learn
- HuggingFace Transformers for BERT embeddings
- Jupyter Notebook or JupyterLab

**Hardware**: 
- Standard consumer laptop sufficient
- BERT embedding extraction: 12-24 hours
- All other analyses: minutes

### Data Access

All participant data (questionnaire responses, coded annotations, and aggregate results) are available on the Open Science Framework at [OSF URL]. This repository contains all code needed to reproduce analyses from those data.

## Ethics and Participant Information

- All studies received ethics approval from the University of Cambridge
- Participants provided informed consent  
- Compensation: £2.50 via Prolific
- Complete ethics documentation available on OSF

## Citation

Researchers using these materials should cite the associated thesis:
```
@phdthesis{haket2026,
  title = {Navigating {{Meaning Spaces}}: {{A Contextualist Approach}} to {{Conceptual Engineering}}},
  author = {Haket, Nina},
  year = 2026,
  address = {Cambridge},
  school = {University of Cambridge}
}
```

## License

This project is licensed under the terms of the MIT licence.

## Acknowledgments

This research was supported by The Cambridge Trust International Scholarship. Special thanks to the 273 participants who contributed their time and insights to this study, and to Ryan Daniels.
