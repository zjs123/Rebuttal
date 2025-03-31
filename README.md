# Tables for ICML submission 8244 rebuttal
__Table 1 Comparison of Kara, SaProt, and ProtSST on ProteinGYM benchmark (Zero-shot)__
| Models          | Coefficient  | NDCG  | Top-recall |
|-----------------|--------|-------|------------|
| SaProt          | 0.458  | 0.768 | 0.233      |
| ProtSST         | 0.504  | 0.777 | 0.239      |
| EMS2            | 0.414  | 0.747 | 0.217      |
| Kara (ProtBert) | 0.351  | 0.747 | 0.208      |
| Kara (ESM2-33t)     | 0.446  | 0.761 | 0.235      |

__Table 2 Comparison of Kara, SaProt, and ProtSST on inductive setting__
|  Tasks      | ProtSST | SaProt | Kara   |
|--------|---------|--------|--------|
| Binding affinity prediction (lower is better)  | 0.639   | 0.656  | 0.501  |
| Semantic Similarity Inference (BP) | 0.25    | 0.22   | 0.41   |
| Semantic Similarity Inference (CC) | 0.27    | 0.23   | 0.41   |

__Table 3 Comparison of Kara and ESM2-33t on short-term contact task__
|   Models     | P@L | P@L/2 | P@L/5  |
|--------|---------|--------|--------|
| ESM2-33t | 0.44 | 0.44 | 0.50 |
| Kara (ProtBert) | 0.45 | 0.55 | 0.65|

__Table 4 Effectiveness of the retriever__
| Variants                                       | Contact (short, P@L) | Stability | Homology |
|------------------------------------------------|---------|-----------|----------|
| Kara                                           | 0.45    | 0.83      | 0.32     |
| Both Fine-tune and inference without retriever | 0.42    | 0.80      | 0.30     |
| Fine-tune without retriever                    | 0.41    | 0.82      | 0.28     |
| Inference without retriever                    | 0.42    | 0.81      | 0.28     |

__Table 5 Comparison of different models after pre-training and after task fine-tuning__
| Models                                        | After Pre-training                    | After Task Fine-tuning    |
|-----------------------------------------------|---------------------------------------|----------------------------|
| OntoProtein                                   | Precision: 0.712<br>Similarity: 0.901 | Precision: 0.621<br>Similarity: 0.632  |
| KeAP                                          | Precision: 0.705<br>Similarity: 0.918 | Precision: 0.645<br>Similarity: 0.677 |
| Kara                                          | Precision: 0.738<br>Similarity: 0.934           | Precision: 0.725<br>Similarity: 0.968 |
| Kara (without Structure-based Regularization) | Precision: 0.722<br>Similarity: 0.906             | Precision: 0.624<br>Similarity: 0.749  |
| Kara (without Contextualized Virtual Tokens)  | Precision: 0.713<br>Similarity: 0.902             | Precision: 0.676<br>Similarity: 0.816  |

__Table 6 Comparison of training and inference time cost of different models__
|                                                | train time (ProteinKG 25) | inference time (ProteinKG 25) | train time (ProteinKG 65) | inference time (ProteinKG 65) |
|------------------------------------------------|---------------------------|-------------------------------|---------------------------|-------------------------------|
| Kara                                           | 2.3 s/it                  | 0.04 s/item                   | 2.5 s/it                  | 0.05 s/item                   |
| Kara without relation-GO combinations strategy | 34.2 s/it                 | 2.63 s/item                   | 79.4 s/it                 | 4.17 s/item                   |
| knowledge-free baseline (ProtBert)             | 1.5 s/it                  | 0.02 s/item                   | 1.6 s/it                  | 0.02 s/item                   |

__Table 7 Performance of Kara under varying levels of noise (The contact results refer to short-term prediction with P@L/2 metric)__
|                           | 20% noise                                  | 40% noise                                  | 60% noise                                  | 80% noise                                   | No noise                                    |
|---------------------------|--------------------------------------------|--------------------------------------------|--------------------------------------------|---------------------------------------------|---------------------------------------------|
| Inject during fine-tuning | contact: 0.553<br>Homology:0.323<br>Stability: 0.828 | contact: 0.546<br>Homology:0.323<br>Stability: 0.827 | contact: 0.543<br>Homology:0.320<br>Stability: 0.817 | contact: 0.541<br>Homology: 0.320<br>Stability: 0.812 | contact: 0.553<br>Homology: 0.323<br>Stability: 0.830 |
| Inject during inference   | contact: 0.553<br>Homology:0.323<br>Affinity:0.503 | contact: 0.553<br>Homology:0.321<br>Affinity:0.502 | contact: 0.548<br>Homology:0.318<br>Affinity:0.504 | contact: 0.548<br>Homology:0.317<br>Affinity: 0.507 | contact: 0.553<br>Homology:0.323<br>Affinity:0.501  |

__Table 8 Performance of Kara with different retrieval threshold__
|            Tasks            | threshold=0.9 | threshold=0.8 | threshold=0.7 | threshold=0.6 | threshold=0.5  |
|------------------------|---------------|---------------|---------------|---------------|----------------|
| Contact (short, P@L/2) | 0.553         | 0.553         | 0.553         | 0.550         | 0.545          |
| Homology               | 0.323         | 0.323         | 0.320         | 0.317         | 0.314          |
| Affinity               | 0.498         | 0.501         | 0.507         | 0.510         | 0.511          |


__Table 9 Performance of Kara with different knowledge graphs__
|   Models     | contact (short, P@L/5) | Affinity | homology  |
|--------|---------|--------|--------|
| ProteinKG25 | 0.65 | 0.50 | 0.32 |
| ProteinKG65 | 0.67 | 0.48 | 0.31|

__Table 10 Performance of different models for proteins within knowledge graph__
|                 Models                 | Contact (short, P@L/5) | Homology | Contact (long, P@L/5) |
|----------------------------------------------|-----------------|----------|----------------|
| Kara (With virtual tokens without retrieval) | 0.698           | 0.481    | 0.582          |
| Kara                                         | 0.692           | 0.485    | 0.583          |
| KeAP                                         | 0.648           | 0.457    | 0.566          |
| OntoProtein                                  | 0.619           | 0.441    | 0.562          |

