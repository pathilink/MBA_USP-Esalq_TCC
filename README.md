# Exploring women's financial inclusion: classification of women's profiles and related variables

Repository of final project for the USP/Esalq MBA in Data Science & Analytics – 2024.  

![Status Badge](https://img.shields.io/static/v1?label=STATUS&message=COMPLETE&color=008000)

## 📖 Description

This project investigates **women's financial inclusion** as a crucial indicator of economic empowerment.  
The study used data from the **World Bank (Global Findex 2021)** to classify profiles of Brazilian women in relation to access to financial services, identifying patterns of inclusion, dependence on government assistance, and use of digital technologies.

## 🎯 Objectives

- Analyze socioeconomic and financial variables related to women's inclusion.
- Identify **profiles (clusters)** of financially included and excluded women.
- Provide **practical insights** for the formulation of public policies and market strategies aimed at female audiences.

## 🗂️ Data

- Source: **World Bank – Global Findex 2021**
- Granularity: **individual (Brazilian women)**  
- Sample: **475 observations** and **71 variables** initially  
- Treatments applied:
    - Exclusion of irrelevant variables or those with >60% null values
    - Imputation of missing data with averages or control values (-1)
    - Normalization and reduction of the final set to 67 variables  

## 🔎 Methodology
1. **Exploratory Data Analysis (EDA)**

    As can be seen in the figure below, which shows the distribution of variables by age, most of the women interviewed had a high school or college education. 
    In all age groups up to 84 years old, a large proportion of women remained in the labor market, decreasing as they got older. 
    However, 62% had not received a salary in the last 12 months. 
    Only 11% did not have any type of bank account.

    ![eda graphs](img/eda_graphs.png)  

    Analyzing only the distribution of socioeconomic variables, just over 51% of the women interviewed have a high school education and another significant portion (32%) have a college degree or higher. 
    Educational level did not appear to be a determining factor for financial inclusion, as 89% of them have some type of bank account (traditional or mobile), although only 75% of them are somehow present in the labor market.

    ![distribution](img/distribuicoes.png)

2. **Clustering**  
   - **Hierarchical (dendrogram)** to identify number of groups  
   - **K-Means** validated by metrics **Silhouette**, **Davies-Bouldin** and **Calinski-Harabasz**  

    I chose to explore the data by applying the hierarchical clustering scheme, which iteratively merges clusters based on a dissimilarity metric (such as Euclidean distance) until all clusters form a single cluster. The result allowed me to identify three main clusters.

    ![dendrogam](img/dendograma_ptbr_line.png)

    In order to test the result, the non-hierarchical k-means scheme was applied. In this scheme, the data started in a single cluster, and the algorithm iteratively divided them into smaller clusters until a stopping criterion was reached. The number of clusters was verified using the elbow curve, which allowed us to choose a number of clusters such that adding another cluster would not provide a better model of the data, and also through validation metrics.

    ![elbow curve](img/elbow_curve.png)

    Among the internal validation metrics is the Silhouette coefficient, which measures the suitability of each data point to the cluster to which it has been assigned. The higher and further away the coefficient is from zero, the better. Another metric is the Davies-Bouldin index, which is based on the idea that good clusters are those that have low variation within the cluster and high separation between clusters—the closer the value is to zero, the better.  The combination of cohesion and separation is the Calinski-Harabasz index, a measure of the similarity of an object to its own cluster (cohesion) compared to other clusters (separation). Here, cohesion is estimated based on the distances of the data points in a cluster to the cluster centroid, and separation is based on the distance of the cluster centroids to the global centroid—the higher the value, the better.

    | Number of clusters | Silhouette | Davies-Bouldin | Calinski-Harabasz |
    |:-:|:-:|:-:|:-:|
    | 2 | 0.2499 | 1.3755 | 127.3031 |
    | **3** | **0.1948** | **1.8959** | **115.6588** |
    | 4 | 0.1775 | 2.0672 |  98.4795 |
    
    

3. **Validation and Interpretation of Clusters**  
   - Seleção das variáveis mais significativas (idade, escolaridade, renda, uso de contas digitais, recebimento de salário etc.)  
   - [imagem "4"] – Principais variáveis diferenciadoras  

## 📊 Results

Foram identificados **três clusters principais**:

- **Cluster 2 – Maior inclusão**  
  Mulheres mais jovens, com ensino superior, no mercado de trabalho, maior acesso a serviços bancários e digitais.  

- **Cluster 1 – Inclusão intermediária**  
  Mulheres de meia-idade, com conta em banco tradicional, mas dependentes de transferências governamentais.  

- **Cluster 0 – Menor inclusão**  
  Mulheres mais velhas, com baixa utilização de serviços financeiros, poucas contas bancárias e sem acesso digital.  

[imagem "5"] – Distribuição dos clusters  

## 📌 Conclusões

- A inclusão financeira é determinante para o **empoderamento feminino** e está ligada a fatores como renda, escolaridade e acesso digital.  
- Políticas públicas e estratégias de mercado devem considerar os diferentes perfis identificados, priorizando os grupos menos incluídos.  
- A análise sugere **quatro dimensões principais de mensuração**:  
  1. Informações demográficas e de renda  
  2. Recebimento de salário  
  3. Uso de meios digitais/cartões  
  4. Propriedade de conta bancária  

## 🛠️ Technologies used

<img alt="Python" src="https://img.shields.io/badge/-Python-blue?style=flat&logo=python&logoColor=yellow" />  ![Badge](https://img.shields.io/badge/Colab-Google-%F9AB00?style=flat&logo=Google-Colab&color=blue)

## 👩🏻‍💻 Author

[![Linkedin Badge](https://img.shields.io/badge/-Patrícia-blue?style=flat&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/pathilink/)](https://www.linkedin.com/in/pathilink/)

## 🔓 License

[![License: MIT](https://img.shields.io/badge/License-MIT-750014.svg)](https://opensource.org/licenses/MIT)


