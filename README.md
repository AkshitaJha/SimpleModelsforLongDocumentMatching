# Dataset for Long-Form Document Matching/Semantic Text Matching

This repository contains the data resources for the papers "[Transformer-based Models for Long-Form Document Matching: Challenges and Empirical Analysis](https://aclanthology.org/2023.findings-eacl.178/)" and "[Supervised Contrastive Learning for Interpretable Long-Form Document Matching](https://dl.acm.org/doi/full/10.1145/3542822)".

## Dataset

We create benchmark long document datasets (by pre-processing ACL Anthology 2014 papers and Wikipedia articles) for the task of long-form document matching/semantic text matching.

- **AAN (ACL Anthology Network Campus)**: The [AAN corpus](https://aan.how/download/#aanNetworkCorpus) (Radev et al., 2013) consists of 23,766 papers written by 18,862 authors in 373 venues related to NLP and forms a citation network. Each paper is represented by a node with directed edges connecting a paper (the parent node) to all its cited papers (children nodes). Papers that have been cited by the parent paper are treated as similar samples (Jiang et al., 2019). For every similar sample, an irrelevant paper is randomly chosen to create a balanced dataset. Sets of similar papers are given the same labels. To prevent leakage of information and make the task more difficult, the references and the abstract sections are removed. Papers without any content are also removed. We then randomly sample 15,000 research paper pairs for our experiment.

- **WIKI (Wikipedia)**: We use the [Wikipedia dump](https://dumps.wikimedia.org/enwiki/latest/enwiki-latestpages-articles.xml.bz2), and adopt a similar methodology proposed by Jiang et al. (Jiang et al., 2019) to process this data. From the Wikipedia dump containing 6 million articles, we randomly sampled 250,000 articles along with the articles present in their outlinks. We create a dataset of similar Wikipedia articles by assuming that similar articles have similar outgoing links. The Jaccard similarity between the outgoing links of the source and the target articles is calculated. If the Jaccard similarity > 0.5, the documents are assumed to be similar, otherwise they are considered dissimilar. Only articles with two or more similar articles are selected. We then randomly sample 15,000 research paper pairs for our experiment.


## Citation

Please cite the below papers, if you use the dataset or the proposed methodology:

```
@inproceedings{jha-etal-2023-transformer,
    title = "Transformer-based Models for Long-Form Document Matching: Challenges and Empirical Analysis",
    author = "Jha, Akshita  and
      Samavedhi, Adithya  and
      Rakesh, Vineeth  and
      Chandrashekar, Jaideep  and
      Reddy, Chandan",
    editor = "Vlachos, Andreas  and
      Augenstein, Isabelle",
    booktitle = "Findings of the Association for Computational Linguistics: EACL 2023",
    month = may,
    year = "2023",
    address = "Dubrovnik, Croatia",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2023.findings-eacl.178",
    doi = "10.18653/v1/2023.findings-eacl.178",
    pages = "2345--2355",
    abstract = "Recent advances in the area of long document matching have primarily focused on using transformer-based models for long document encoding and matching. There are two primary challenges associated with these models. Firstly, the performance gain provided by transformer-based models comes at a steep cost {--} both in terms of the required training time and the resource (memory and energy) consumption. The second major limitation is their inability to handle more than a pre-defined input token length at a time. In this work, we empirically demonstrate the effectiveness of simple neural models (such as feed-forward networks, and CNNs) and simple embeddings (like GloVe, and Paragraph Vector) over transformer-based models on the task of document matching. We show that simple models outperform the more complex BERT-based models while taking significantly less training time, energy, and memory. The simple models are also more robust to variations in document length and text perturbations.",
}

@article{10.1145/3542822,
  author = {Jha, Akshita and Rakesh, Vineeth and Chandrashekar, Jaideep and Samavedhi, Adithya and Reddy, Chandan K.},
  title = {Supervised Contrastive Learning for Interpretable Long-Form Document Matching},
  year = {2023},
  issue_date = {February 2023},
  publisher = {Association for Computing Machinery},
  address = {New York, NY, USA},
  volume = {17},
  number = {2},
  issn = {1556-4681},
  url = {https://doi.org/10.1145/3542822},
  doi = {10.1145/3542822},
  abstract = {Recent advancements in deep learning techniques have transformed the area of semantic text matching (STM). However, most state-of-the-art models are designed to operate with short documents such as tweets, user reviews, comments, and so on. These models have fundamental limitations when applied to long-form documents such as scientific papers, legal documents, and patents. When handling such long documents, there are three primary challenges: (i) the presence of different contexts for the same word throughout the document, (ii) small sections of contextually similar text between two documents, but dissimilar text in the remaining parts (this defies the basic understanding of “similarity”), and (iii) the coarse nature of a single global similarity measure which fails to capture the heterogeneity of the document content. In this article, we describe CoLDE: Contrastive Long Document Encoder—a transformer-based framework that addresses these challenges and allows for interpretable comparisons of long documents. CoLDE uses unique positional embeddings and a multi-headed chunkwise attention layer in conjunction with a supervised contrastive learning framework to capture similarity at three different levels: (i) high-level similarity scores between a pair of documents, (ii) similarity scores between different sections within and across documents, and (iii) similarity scores between different chunks in the same document and across other documents. These fine-grained similarity scores aid in better interpretability. We evaluate CoLDE on three long document datasets namely, ACL Anthology publications, Wikipedia articles, and USPTO patents. Besides outperforming the state-of-the-art methods on the document matching task, CoLDE is also robust to changes in document length and text perturbations and provides interpretable results. The code for the proposed model is publicly available at .},
  journal = {ACM Trans. Knowl. Discov. Data},
  month = {feb},
  articleno = {27},
  numpages = {17},
  keywords = {long documents, transformer, embeddings, BERT, interpretability, contrastive learning, Semantic text matching, attention}
  }
```








