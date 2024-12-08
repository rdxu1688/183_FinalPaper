# UMAP

##### Group 3: Richard Xu, Eugene Kong, Jonathan Lam

## Interpretations of UMAP

Thus, interpreting the outputted graphs from UMAP is vital in order to get accurate results. Below is a typical workflow post clustering as for annotation and verification in the context of single-cell RNA sequencing(scRNA-seq). [^SC_interpretation]

![My local image](workflow1.jpeg "My Image")

In the perspective of scRNA-seq data, your goal is to quantify the different cell types using marker genes or gene functions. Typically, the data enters in as a "gene-by-cell" matrix, in which UMAP conducts dimensionality reduction. If certain cell types are known, or a reference is on hand, automatic annotation can be conducted to mark these particular clusters. Then, dependent on the cluster's trend as compared to data (i.e combination of marker genes, pathway analysis, etc) the data can further be annotated to mark any unlabeled clusters or intermediate regions. [^SC_interpretation] As such, the core idea of this is the content of each cluster, we're not necessarily looking at individual data points, we're looking at clusters at a whole.

## Example: scRNA-seq Context

Thus, let us look at an example of a UMAP clustering graph, the following is taken from the Clarke. et al. paper. [^SC_interpretation]

![My local image](example.jpg "My Image")

The following UMAP was created post batch correction using harmony, from three different datasets(three different experiments respectively). The plot isn't too hard to interpret-- starting off, the X and Y axis represent arbitrary distances to seperate the clusters based one "how related they are", this being dependent on the clustering technique and experimental parameters as mentioned earlier. [^UMAP_doc] Visually, we can see three distinct clusters consisting of the different cell types. The main point to consider is the content of your clusters in relation to distances between clusters, as ones that are closer together are likely to be more related, this again being in terms of the such arbitrary distance given by the UMAP. From here you can cross reference this to your data, let us take the upper left cluster with T cells and NK cells for example. The creation of NK cells involves CD127+, a common innate lymphoid progenitor, notably, this is just slightly downstream of another common lymphoid progenitor which makes T cells amongst other types. [^NK_cells] 

### Tips and Common Misconceptions

As such, there are some common misconceptions to be considered:

1. Hyperparameters and thresholds are important
**True**, as previously mentioned, you must test different thresholds that you input to your UMAP to see how your data is affected through different values. Does it lead to more clusters getting blended together? Can you effectively label your clusters? [^Misconceptions]

2. Cluster sizes matter
**False**, the number of datapoints within your cluster doesn't necessarily correlate to anything. With changing hyperparameters and clustering techniques, one individual datapoint in your UMAP plot could just as easily be associated with another cluster. [^Misconceptions]

3. Cluster Distance always matters
**False**, while the above example me![example](https://github.com/user-attachments/assets/346c1443-a68a-4e63-9e87-a90b00968e99)
![workflow1](https://github.com/user-attachments/assets/a0d6bca3-1d9b-4bb5-b5cc-65f986678807)
![test1](https://github.com/user-attachments/assets/3e6a150f-00bb-4c0c-badd-e2562ea52373)
<img width="922" alt="scRNA-seq_example" src="https://github.com/user-attachments/assets/1b26bd22-0acb-40ff-aabd-d43db1d11652">
![Proteomics_umap](https://github.com/user-attachments/assets/b809889d-7d51-49df-828a-f04c2069e44e)
![pop_gen_ex](https://github.com/user-attachments/assets/b3f0351c-bdac-4fdc-a4e4-9060b198e372)
ntioned different cell types and how they potentially may be related, the distance between clusters could just as easily be unrelated. In essence, you must check the background of your data and annotations to see if you can draw conclusions from these clusters. [^Misconceptions] However, for example if you have a lot of datapoints(and in turn a lot of clusters), the clusters can just as easily start blending together and thus makes it impossible for you to associate one cluster versus another in terms of distance. Really, if anything the content of your clusters is of most importance when looking at any graphs. 

## Applications

The premise of UMAP is that, if you have data from any context and you want to identify groups, UMAP is applicable. **As for biological contexts,** here are some different applications of UMAP.

1. scRNA-seq

As mentioned rigorously, UMAP is commonly used in scRNA-seq data interpretation. Their goal is to characterize some sort of gene expression in relation to some sort of factor. To elaborate, by plotting out the different cell types, analysis can be conducted to find out if any cell-type groups of interest are being affected by your experimental conditions. For example, scRNA-seq involves different library preperation techniques before sequencing. These plots aimed to characterize how the different methods affected clustering and their cell type expression.[^scRNA-seq_example]

![My local image](scRNA-seq_example.jpg "My Image") 

2. Proteomics

Another scenario involves the context of proteins and proteomics, their goal is to characterize difference in the structures of these proteins either by mutations or variances within the genome. For example, below, a UMAP plot was generated for 1484 single-gene deletion strains based on their similarity of transcriptional effects. In this scenario distance actually matters, figure a show characterizes the clusters by how closely they are together. [^proteomic_ex]

![My local image](Proteomics_umap.jpg "My Image") 

3. Population Genetics

Population genetics is another prime example of UMAP's visualization power and characterization. The goal here is to characterize the different genomes behind populations be it identifying any major risk factors(i.e ones that lead to higher rate of cancer), or simple SNPs(single nucleotide polymophisms) that are relatively harmless and lead to different encodings of their associated protein structures. An example can be seen below, where UMAP was used to cluster data from the Genome Aggreation Database, characterizing ancestral diversity. Their goal was to showcase the relationships between the populations on a contential and subcontential level. [^population_gen_ex]

![My local image](pop_gen_ex.jpg "My Image") 

### References

[^SC_interpretation]: Clarke, Z.A., Andrews, T.S., Atif, J. et al. Tutorial: guidelines for annotating single-cell transcriptomic maps using automated and manual methods. Nat Protoc 16, 2749–2764 (2021). https://doi.org/10.1038/s41596-021-00534-0

[^Misconceptions]: Coenen, Andy, and Adam Pearce. “Understanding Umap.” PAIR Page Redirection, pair-code.github.io/understanding-umap/.

[^scRNA-seq_example] Mary Piper, Meeta Mistry. “Single-Cell RNA-Seq: Integration.” Introduction to Single-Cell RNA-Seq, 21 Nov. 2020, hbctraining.github.io/scRNA-seq_online/lessons/06_integration.html. 

[^UMAP_doc] “Basic UMAP Parameters.” Basic UMAP Parameters - Umap 0.5 Documentation, umap-learn.readthedocs.io/en/latest/parameters.html. Accessed 7 Dec. 2024. 

[^NK_cells]Wikipedia contributors. "Natural killer cell." Wikipedia, The Free Encyclopedia. Wikipedia, The Free Encyclopedia, 16 Oct. 2024. Web. 8 Dec. 2024.

[^proteomic_ex] Dorrity, M.W., Saunders, L.M., Queitsch, C. et al. Dimensionality reduction by UMAP to visualize physical and genetic interactions. Nat Commun 11, 1537 (2020). https://doi.org/10.1038/s41467-020-15351-4

[^population_gen_ex] Diaz-Papkovich, A., Anderson-Trocmé, L. & Gravel, S. A review of UMAP in population genetics. J Hum Genet 66, 85–91 (2021). https://doi.org/10.1038/s10038-020-00851-4
