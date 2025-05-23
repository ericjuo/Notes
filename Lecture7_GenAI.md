# Lecture 7. Protein generative models
課程時間:4小時

## UniProt
-    [RCSB PDB](https://www.rcsb.org/)
-    [Alphafold DB](https://alphafold.ebi.ac.uk/)

## Swissmodel
https://swissmodel.expasy.org/interactive
## Alphafold
-    [Alphafold3](https://alphafoldserver.com/)
-    [Alphafold2](https://colab.research.google.com/github/sokrypton/ColabFold/blob/main/AlphaFold2.ipynb)

## ESMfold
**ESMFold** 是 Meta AI（Facebook AI）開發的一款 **蛋白質結構預測工具**，基於大型語言模型（Large Language Model, LLM）訓練的 **蛋白質語言模型 ESM-2**，可以從 **胺基酸序列直接預測三維結構**。

它是對 AlphaFold 的挑戰者之一，特點是**不依賴序列比對（MSA）**，速度快、資源需求低，非常適合大規模掃描與初步結構預測。

```
docker run --rm --gpus all -v $(pwd)/processed6:/data biochunan/esmfold-image -i /data/denovo_mlca_${i}.fasta -o /data/pdb | tee $(pwd)/processed6/denovo_mlca_${i}.log
```
-    ESMfold
-    ESM3


## RFdiffusion
-    Active site model

## ProteinMPNN
-    ProteinMPNN
-    LigandMPNN
-    SolubleMPNN







### References
1. https://www.rcsb.org/
2. https://www.uniprot.org/
3. https://swissmodel.expasy.org/interactive
4. https://alphafoldserver.com/
5. https://github.com/google-deepmind/alphafold
6. https://github.com/facebookresearch/esm
7. https://github.com/RosettaCommons/RFdiffusion
8. https://github.com/dauparas/ProteinMPNN
9. https://github.com/dauparas/LigandMPNN