# Portuguese Hate Speech Expanded Dataset (TuPyE)
TuPyE, an enhanced iteration of TuPy, encompasses a compilation of 43,668 meticulously annotated documents specifically 
selected for the purpose of hate speech detection within diverse social network contexts. 
This augmented dataset integrates supplementary annotations and amalgamates with datasets sourced from 
[Fortuna et al. (2019)](https://aclanthology.org/W19-3510/), 
[Leite et al. (2020)](https://arxiv.org/abs/2010.04543), 
and [Vargas et al. (2022)](https://arxiv.org/abs/2103.14972),
complemented by an infusion of 10,000 original documents from the [TuPy-Dataset](https://huggingface.co/datasets/Silly-Machine/TuPy-Dataset).

In light of the constrained availability of annotated data in Portuguese pertaining to the English language, 
TuPyE is committed to the expansion and enhancement of existing datasets. 
This augmentation serves to facilitate the development of advanced hate speech detection models through the utilization of machine learning (ML) 
and natural language processing (NLP) techniques.
This repository is organized as follows:

```sh
root.
    ├── binary     : binary dataset (including training and testing split)
    ├── multilabel : multilabel dataset (including training and testing split)
    └── README.md  : documentation and card metadata
```
We highly recommend reading the associated research paper [TuPy-E: detecting hate speech in Brazilian Portuguese social media with a novel dataset and comprehensive analysis of models](https://arxiv.org/abs/2312.17704) to gain 
comprehensive insights into the advancements integrated into this extended dataset.

## Security measures
To safeguard user identity and uphold the integrity of this dataset, all user mentions have been anonymized as "@user," and any references to external websites have been omitted

## Annotation and voting process

In the pursuit of advancing the field of automatic hate speech detection in Portuguese, our team undertook the meticulous task of creating a comprehensive database. 
This endeavor involved the integration of labeled document sets from seminal studies in the domain, specifically those conducted by Fortuna et al. (2019), 
Leite et al. (2020), and Vargas et al. (2022). To ensure the highest degree of consistency and compatibility within our dataset, 
we adhered to stringent guidelines for text integration, detailed as follows:

1. **Fortuna et al. (2019)**: This study presented a dataset of 5,670 tweets, each annotated by three independent evaluators to ascertain the presence or absence of hate speech. In our integration process, we adopted a simple majority-voting mechanism to classify each document, ensuring a consistent approach to hate speech identification across the dataset.

2. **Leite et al. (2020)**: The dataset from this research encompassed 21,000 tweets, annotated by 129 volunteers. Each tweet was reviewed by three different assessors. The study identified six categories of toxic speech, namely: (i) homophobia, (ii) racism, (iii) xenophobia, (iv) offensive language, (v) obscene language, and (vi) misogyny. In aligning with our operational definition of hate speech, we chose to exclude texts that solely fell under the categories of offensive and/or obscene language. Consistent with our methodology, a straightforward majority-voting process was utilized for the classification of these texts.

3. **Vargas et al**. (2022): This research involved a compilation of 7,000 comments sourced from Instagram, each labeled by a trio of annotators. These data had already been subjected to a simple majority-voting classification, thereby obviating the need for us to apply additional text classification protocols.

Through the application of these rigorous integration guidelines, we have succeeded in establishing a robust, unified database that stands as a valuable resource for the development and refinement of automatic hate speech detection systems in the Portuguese language.

## Data structure
A data point comprises the tweet text (a string) along with thirteen categories, each category is assigned a value of 0 when there is an 
absence of aggressive or hateful content and a value of 1 when such content is present. These values represent the consensus of 
annotators regarding the presence of aggressive, hate, ageism, aporophobia, body shame, capacitism, lgbtphobia, political, racism, 
religious intolerance, misogyny, xenophobia, and others. An illustration from the multilabel TuPyE dataset is depicted below:

```python
{
source:"twitter",
text: "e tem pobre de direita imbecil que ainda defendia a manutenção da política de preços atrelada ao dólar link",
researcher:"leite et al", year:2020,
aggressive: 1, hate: 1, ageism: 0, aporophobia: 1, body shame: 0, capacitism: 0, lgbtphobia: 0, political: 1, racism : 0,
religious intolerance : 0, misogyny : 0, xenophobia : 0, other : 0
}
```

# Dataset content

The table 1 delineates the quantity of documents annotated in TuPyE, systematically categorized by the respective researchers.

#### Table 1 - TuPyE composition

| Label                | Count  |Source   |
|----------------------|--------|---------|
| Leite et al.         | 21,000 |Twitter  |
| TuPy                 | 10,000 |Twitter  |
| Vargas et al.        |  7,000 |Instagram|
| Fortuna et al.       |  5,668 |Twitter  |

Table 2 provides a detailed breakdown of the dataset, delineating the volume of data based on the occurrence of aggressive speech and the manifestation of hate speech within the documents

#### Table 2 - Count of non-aggressive and aggressive documents

| Label                | Count  |
|----------------------|--------|
| Non-aggressive       | 31121  |
| Aggressive - Not hate| 3180   |
| Aggressive - Hate    | 9367   |
| Total                | 43668  |

Table 3 provides a detailed analysis of the dataset, delineating the data volume in relation to the occurrence of distinct categories of hate speech.

#### Table 3 - Hate categories count

| Label                    | Count |
|--------------------------|-------|
| Ageism                   | 57    |
| Aporophobia              | 66    |
| Body shame               | 285   |
| Capacitism               | 99    |
| LGBTphobia               | 805   |
| Political                | 1149  |
| Racism                   | 290   |
| Religious intolerance    | 108   |
| Misogyny                 | 1675  |
| Xenophobia               | 357   |
| Other                    | 4476  |
| Total                    | 9367  |


# Acknowledge
The TuPy-E project is the result of the development of Felipe Oliveira's thesis and the work of several collaborators. This project is financed by the Federal University of Rio de Janeiro ([UFRJ](https://ufrj.br/)) and the Alberto Luiz Coimbra Institute for Postgraduate Studies and Research in Engineering ([COPPE](https://coppe.ufrj.br/)).

# References 
[1] P. Fortuna, J. Rocha Da Silva, J. Soler-Company, L. Wanner, and S. Nunes, “A Hierarchically-Labeled Portuguese Hate Speech Dataset,” 2019. [Online]. Available: https://github.com/t-davidson/hate-s

[2] J. A. Leite, D. F. Silva, K. Bontcheva, and C. Scarton, “Toxic Language Detection in Social Media for Brazilian Portuguese: New Dataset and Multilingual Analysis,” Oct. 2020, [Online]. Available: http://arxiv.org/abs/2010.04543

[3] F. Vargas, I. Carvalho, F. Góes, T. A. S. Pardo, and F. Benevenuto, “HateBR: A Large Expert Annotated Corpus of Brazilian Instagram Comments for Offensive Language and Hate Speech Detection,” 2022. [Online]. Available: https://aclanthology.org/2022.lrec-1.777/
