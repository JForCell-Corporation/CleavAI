# CleavAI

> **Work in Progress**: This project is under active development.

CleavAI is a computational framework for predicting furin cleavage of peptides and ranking candidates based on a weighted efficiency score that incorporates cleavage likelihood and synthesis cost.

<br/>

## Overview

- CleavAI uses **ProtBERT**, a transformer model from the ProtTrans project, for embedding peptide sequences.
  > Elnaggar et al., ProtTrans: Towards Cracking the Language of Life’s Code Through Self-Supervised Learning
  > bioRxiv 2021.07.12.199554
  > https://doi.org/10.1101/2020.07.12.199554
  
- A multi-layer perceptron is trained on ProtBERT embeddings and **biochemical features** to classify cleavage potential.
  
  | Feature             | Description                 |
  |---------------------|-----------------------------|
  | Molecular weight    | Total peptide mass (Da) |
  | Isoelectric point   | pH of net zero charge |
  | Aromaticity         | Fraction of F, W, Y residues |
  | Instability index   | Empirical estimate of peptide stability from residue pairs |
  | GRAVY               | Average hydropathy |
  | Flexibility         | Mean residue flexibility, relates to cleavage exposure |

<br/>

## Dataset

The dataset was constructed from curated cleavage annotations in the [MEROPS](https://www.ebi.ac.uk/merops/) database (v12.4).
> Neil D Rawlings, Alan J Barrett, Paul D Thomas, Xiaosong Huang, Alex Bateman, Robert D Finn, The MEROPS database of proteolytic enzymes, their substrates and inhibitors in 2017 and a comparison with peptidases in the PANTHER database, Nucleic Acids Research, Volume 46, Issue D1, 4 January 2018, Pages D624–D632, https://doi.org/10.1093/nar/gkx1134

<br/>

## Results

### Model Performance
CleavAI achieves robust classification performance on held-out data:

- **Accuracy**: 94.4%
- **F1 score**: 0.884 (positive class)

![auc](https://github.com/user-attachments/assets/2369e465-e340-4337-bb65-f642f99476f9)

![pr](https://github.com/user-attachments/assets/a9d36c5b-d17b-4502-9898-eacfe6dfddaa)


### Top-Ranked Cleavage Candidates

|peptide|cleavage_prob|
|-------|-------------|
| RVKR |  0.986675  |
| RLKR |  0.985134  |
| RTKR |  0.981022  |
|...|

![rank](https://github.com/user-attachments/assets/d7af6663-ce66-4207-a49a-3bbc2370c3de)


© 2025 JForCell Corporation. All Rights Reserved.

