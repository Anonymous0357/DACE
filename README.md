# DACE: Debiased Cognition Representation Learning for Knowledge Tracing
Considering some abnormal behaviors (like guessing and plagiarism) lead to the existence of bias data in students' interaction answer records, we propose the DACE model to learn a robust and debiased representation of knowledge states for reliable prediction on the KT task. 

### Briefly introduce the DACE model
![framework](.assets/framework.png)

Given the processed interaction data, the whole framework mainly contains two modules:
1.  Two knowledge state extractors: both of them utilize a sequential contrastive learning network to learn representations of knowledge state but are trained differently to capture distinct aspects of the data. 
2. Training process: The biased knowledge state extractor is trained using a combination of contrastive loss and cross-entropy loss with an early stop mechanism. The unbiased extractor is trained independently by minimizing information bottleneck loss. 

For more details, please read our paper: 《Debiased Cognition Representation Learning for Knowledge Tracing》

### How to train the DACE model
1. Data Preparation: Download and unzip [assist09 data](https://drive.google.com/uc?export=download&id=14wBw8BHf9e328v4dD5EdsRMtR_gCFcdq) in `data` directory, download and unzip [embedding data](https://drive.google.com/uc?export=download&id=16s9jNZZSkxT33Hb7r1OY7PqkJBzhC5DV) in `embeddings` directory.
2. Bias Injection: Change `config.py`, such as `biased types (i.e., plagiarism, guessing), inject proportion: p`
3. Main Files: Run the following command: 
    ```
    python train.py # pretrain sequence model on biased dataset
    python run.py # train on biased dataset and evaluate on clean dataset
    ```

Please note that, this model is also suitable for regular KT prediction, if you want to test the performance on normal KT datasets, just skip the step 2.