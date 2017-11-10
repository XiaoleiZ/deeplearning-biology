# deeplearning-biology

This is a list of implementations of deep learning methods to biology, originally published on [Follow the Data](https://followthedata.wordpress.com/). There is a slant towards genomics because that's the subfield that I follow most closely.

Please, contribute to this growing list, especially in categories that I haven't covered well! Also, do add your contributions to [GitXiv](http://gitxiv.com/) as well if you can.

You might also want to refer to the [awesome deepbio](https://github.com/gokceneraslan/awesome-deepbio) list.

## Table of contents
* [Reviews](#reviews)
* [Chemoinformatics and drug discovery](#chemo)
* [Proteomics](#proteomics)
* [Generic 'omics tools](#omics)
* [Genomics](#genomics)
  - [Gene expression](#genomics_expression)
  - [Predicting enhancers and regulatory elements](#genomics_enhancers)
  - [Methylation](#genomics_methylation)
  - [Single-cell applications](#genomics_single-cell)
  - [Non-coding RNA](#genomics_non-coding)
  - [Population genetics](#genomics_pop)
* [Neuroscience](#neuro)

## Reviews <a name="reviews"></a>

These are not implementations as such, but contain useful pointers.

**An introduction to deep learning on biological sequence data: examples and solutions** [[Bioinformatics](https://academic.oup.com/bioinformatics/article/33/22/3685/4092933)] 

**Opportunities And Obstacles For Deep Learning In Biology And Medicine** [[bioRxiv preprint](http://biorxiv.org/content/early/2017/05/28/142760)]

This impressive collaborative review was written completely in the open on [Github](https://github.com/greenelab/deep-review). It is focused on discussing how deep learning may be able to transform patient classification and treatment as well as fundamental biological research in the future, and what the main obstacles are that could prevent it from happening. A lot of interesting points are brought up here. Together with the review listed below, which has a more technical slant, you will get a good overview of how deep learning is used and can be used in biology and medicine.

**Deep learning for computational biology** [[open access paper](http://msb.embopress.org/content/12/7/878)]

This is a very nice review of deep learning applications in biology. It primarily deals with convolutional networks and explains well why and how they are used for sequence (and image) classification.

**Deep learning for health informatics** [[open access paper](http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7801947)]

An overview of several types of deep nets and their applications in translational bioinformatics, medical imaging, "pervasive sensing", medical data and public health.

## Chemoinformatics and drug discovery <a name="chemo"></a>

**Neural graph fingerprints** [[github](https://github.com/HIPS/neural-fingerprint)][[gitxiv](http://gitxiv.com/posts/DFtFytneou3SXLuSM/convolutional-networks-on-graphs-for-learning-molecular)]

A convolutional net that can learn features which are useful for predicting properties of novel molecules; “molecular fingerprints”. The net works on a graph where atoms are nodes and bonds are edges. Developed by the group of Ryan Adams, who co-hosts the very good [Talking Machines](http://www.thetalkingmachines.com/) podcast.

**Deep-learning models for Drug Discovery and Quantum Chemistry** [[github](https://github.com/deepchem/deepchem)][[Python library](http://deepchem.io/)][[preprint](https://arxiv.org/abs/1611.03199)]

This is a "... [P]ython library that aims to make the use of machine-learning in drug discovery straightforward and convenient" which checks a lot of boxes when it comes to advanced is deep learning: one-shot learning, graph convolutional networks, learning from less data, and LSTM embeddings. According to the GitHub site, "DeepChem aims to provide a high quality open-source toolchain that democratizes the use of deep-learning in drug discovery, materials science, and quantum chemistry."

## Generic 'omics tools <a name="omics"></a>

**Continuous Distributed Representation of Biological Sequences for Deep Genomics and Deep Proteomics**[[github](https://github.com/ehsanasgari/Deep-Proteomics)][[paper](http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0141287)]

The GitHub summary reads: "We introduce a new representation for biological sequences. Named bio-vectors (BioVec) to refer to biological sequences in general with protein-vectors (ProtVec) for proteins (amino-acid sequences) and gene-vectors (GeneVec) for gene sequences, this representation can be widely used in applications of deep learning in proteomics and genomics. Biovectors are basically n-gram character skip-gram wordvectors for biological sequences (DNA, RNA, and Protein). In this work, we have explored biophysical and biochemical meaning of this space. In addition, in variety of bioinformatics tasks we have shown the strength of such a sequence representation."

## Proteomics <a name="proteomics"></a>

**Pcons2 – Improved Contact Predictions Using the Recognition of Protein Like Contact Patterns** [[web interface](http://c2.pcons.net/)]

Here, a “deep random forest” with five layers is used to improve predictions of which residues (amino acids) in a protein are physically interacting which each other. This is useful for predicting the overall structure of the protein (a very hard problem.)

## Genomics <a name="genomics"></a>

This category is divided into several subfields.

### Gene expression <a name='genomics_expression'></a>

In modeling gene expression, the inputs are typically numerical values (integers or floats) estimating how much RNA is produced from a DNA template in a particular cell type or condition.

**ADAGE – Analysis using Denoising Autoencoders of Gene Expression** [[github](https://github.com/greenelab/adage)][[gitxiv](http://gitxiv.com/posts/M9Dnc8HbKvNgsSp5D/adage-analysis-using-denoising-autoencoders-of-gene)]

This is a Theano implementation of stacked denoising autoencoders for extracting relevant patterns from large sets of gene expression data, a kind of feature construction approach if you will. I have played around with this package quite a bit myself. The authors initially published a [conference paper](http://www.worldscientific.com/doi/abs/10.1142/9789814644730_0014) applying the model to a compendium of breast cancer (microarray) gene expression data, and more recently posted a paper on [bioRxiv](http://biorxiv.org/content/early/2015/11/05/030650) where they apply it to all available expression data (microarray and RNA-seq) on the pathogen Pseudomonas aeruginosa. (I understand that this manuscript will soon be published in a journal.)

**Learning structure in gene expression data using deep architectures** [[paper](http://biorxiv.org/content/early/2015/11/16/031906)]

This is also about using stacked denoising autoencoders for gene expression data, but there is no available implementation (as far as I could tell). Included here for the sake of completeness (or something.)

**Gene expression inference with deep learning** [[github](https://github.com/uci-cbcl/D-GEX)][[paper](http://biorxiv.org/content/early/2015/12/15/034421)]

This deals with a specific prediction task, namely to predict the expression of specified target genes from a panel of about 1,000 pre-selected “landmark genes”. As the authors explain, gene expression levels are often highly correlated and it may be a cost-effective strategy in some cases to use such panels and then computationally infer the expression of other genes. Based on Pylearn2/Theano.

**Learning a hierarchical representation of the yeast transcriptomic machinery using an autoencoder model** [[paper](http://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-015-0852-1)]

The authors use stacked autoencoders to learn biological features in yeast from thousands of microarrays. They analyze the hidden layer representations and show that these encode biological information in a hierarchical way, so that for instance transcription factors are represented in the first hidden layer.

### Predicting enhancers and regulatory regions <a name='genomics_enhancers'></a>

Here the inputs are typically “raw” DNA sequence, and convolutional networks (or layers) are often used to learn regularities within the sequence. Hat tip to [Melissa Gymrek](http://melissagymrek.com/science/2015/12/01/unlocking-noncoding-variation.html) for pointing out some of these.

**DanQ: a hybrid convolutional and recurrent deep neural network for quantifying the function of DNA sequences** [[github](https://github.com/uci-cbcl/DanQ)][[gitxiv](http://gitxiv.com/posts/aqrWwLoyg75jqNAYX/danq-a-hybrid-convolutional-and-recurrent-deep-neural)]

Made for predicting the function of non-protein coding DNA sequence. Uses a convolution layer to capture regulatory motifs (i e single DNA snippets that control the expression of genes, for instance), and a recurrent layer (of the LSTM type) to try to discover a “grammar” for how these single motifs work together. Based on Keras/Theano.

**Basset – learning the regulatory code of the accessible genome with deep convolutional neural networks** [[github](https://github.com/davek44/Basset)][[gitxiv](http://gitxiv.com/posts/fhET6G7gnBrGS8S9u/basset-learning-the-regulatory-code-of-the-accessible-genome)]

Based on Torch, this package focuses on predicting the accessibility (or “openness”) of the chromatin – the physical packaging of the genetic information (DNA+associated proteins). This can exist in more condensed or relaxed states in different cell types, which is partly influenced by the DNA sequence (not completely, because then it would not differ from cell to cell.)

**DeepSEA – Predicting effects of noncoding variants with deep learning–based sequence model** [[web server](http://deepsea.princeton.edu/job/analysis/create/)][[paper](http://www.nature.com/nmeth/journal/v12/n10/full/nmeth.3547.html)]

Like the packages above, this one also models chromatin accessibility as well as the binding of certain proteins (transcription factors) to DNA and the presence of so-called histone marks that are associated with changes in accessibility. This piece of software seems to focus a bit more explicitly than the others on predicting how single-nucleotide mutations affect the chromatin structure. Published in a high-profile journal (Nature Methods).

**DeepBind – Predicting the sequence specificities of DNA- and RNA-binding proteins by deep learning** [[code](http://tools.genes.toronto.edu/deepbind/)][[paper](http://www.nature.com/nbt/journal/v33/n8/full/nbt.3300.html)]

This is from the group of Brendan Frey in Toronto, and the authors are also involved in the company Deep Genomics. DeepBind focuses on predicting the binding specificities of DNA-binding or RNA-binding proteins, based on experiments such as ChIP-seq, ChIP-chip, RIP-seq,  protein-binding microarrays, and HT-SELEX. Published in a high-profile journal (Nature Biotechnology.)

**DeeperBind - Enhancing Prediction of Sequence Specificities of DNA Binding Proteins** [[preprint](https://arxiv.org/pdf/1611.05777.pdf)]

This is an attempt to improve on DeepBind by adding a recurrent sequence learning module (LSTM) after the convolutional layer(s). In this way, the authors propose to capture a positional dimension that is lost in the pooling step in the original DeepBind design. They claim that benchmarking shows that this architecture leads to superior performance compared to previous work.

**DeepMotif - Visualizing Genomic Sequence Classifications** [[paper](https://arxiv.org/abs/1605.01133)]

This is also about learning and predicting binding specificities of proteins to certain DNA patterns or "motifs". However, this paper makes use of a combination of convolutional layers and [highway networks](https://arxiv.org/pdf/1505.00387v2.pdf), with more layers than the DeepBind network. The authors also show how a learned classifier can generate typical DNA motifs by input optimization; applying back-propagation with all the weights held constant in order to find an input pattern that maximally activates the appropriate output node in the network.

**Convolutional Neural Network Architectures for Predicting DNA-Protein Binding** [[code](http://cnn.csail.mit.edu/)][[paper](http://bioinformatics.oxfordjournals.org/content/32/12/i121.full)]

This work describes a systematic exploration of convolutional neural network (CNN) architectures for DNA-protein binding. It concludes that the convolutional kernels are very important for the success of the networks on motif-based tasks. Interestingly, the authors have provided a Dockerized implementation of DeepBind from the Frey lab (see above) and also provide EC2-laucher scripts and code for comparing different GPU enabled models programmed in Caffe.

**PEDLA: predicting enhancers with a deep learning-based algorithmic framework** [[code](https://github.com/wenjiegroup/PEDLA)][[paper](http://biorxiv.org/content/early/2016/01/07/036129)]

This package is for predicting enhancers (stretches of DNA that can enhance the expression of a gene under certain conditions or in a certain kind of cell, often working at a distance from the gene itself) based on heterogeneous data from (e.g.) the ENCODE project, using 1,114 features altogether.

**DEEP: a general computational framework for predicting enhancers** [[paper](http://nar.oxfordjournals.org/content/early/2014/11/05/nar.gku1058.full)][[code](http://cbrc.kaust.edu.sa/deep/)]

An ensemble prediction method for enhancers.

**Genome-Wide Prediction of cis-Regulatory Regions Using Supervised Deep Learning Methods** (and several other papers applying various kinds of deep networks to regulatory region prediction) [[code](https://github.com/yifeng-li/DECRES)] (one [[paper](http://biorxiv.org/content/early/2016/02/28/041616)] out of several)

Wyeth Wasserman’s group have made a kind of [toolkit](https://github.com/yifeng-li/DECRES) (based on the Theano tutorials) for applying different kinds of deep learning architectures to cis-regulatory element (DNA stretches that can modulate the expression of a nearby gene) prediction. They use a specific “feature selection layer” in their nets to restrict the number of features in the models. This is implemented as an additional sparse one-to-one linear layer between the input layer and the first hidden layer of a multi-layer perceptron.

**FIDDLE: An integrative deep learning framework for functional genomic data inference** [[paper](http://biorxiv.org/content/early/2016/10/17/081380)][[code](https://github.com/ueser/FIDDLE)[[Youtube talk](https://www.youtube.com/watch?v=pcLTUsOm5pc&feature=youtu.be&list=PLlMMtlgw6qNjROoMNTBQjAcdx53kV50cS&t=2411)]

The group predicted transcription start site and regulatory regions but claims this solution could be easily generalized and predict other features too. FIDDLE stands for Flexible Integration of Data with Deep LEarning. The idea (nicely explained by the author in the YouTube video above) is to model several genomic signals jointly using convolutional networks. This could be for example DNase-seq, ATAC-seq, ChIP-seq, TSS-seq, maybe RNA-seq signals (as in .wig files with one value per base in the genome).


### Non-coding RNA <a name='genomics_non-coding'></a>

**DeepLNC, a long non-coding RNA prediction tool using deep neural network** [[paper](http://link.springer.com/article/10.1007%2Fs13721-016-0129-2)] [[web server](http://bioserver.iiita.ac.in/deeplnc/)]

Identification of potential long non-coding RNA molecules from DNA sequence, based on k-mer profiles.

### Methylation <a name='genomics_methylation'></a>

**DeepCpG - Predicting DNA methylation in single cells**
[[paper](http://dx.doi.org/10.1186/s13059-017-1189-z)]
[[code](https://github.com/cangermueller/deepcpg)]
[[docs](http://deepcpg.readthedocs.io/en/latest/)]

DeepCpG is a deep neural network for predicting DNA methylation in multiple cells. DeepCpG has a modular architecture, consisting of a recurrent CpG module to account for correlations between CpG sites within and across cells, a convolutional DNA module to extract patterns from a wide DNA sequence window, and a Joint module that integrates the evidence from the CpG and DNA module to predict the methylation state of multiple cells for a target CpG site. DeepCpG yields accurate predictions, enables discovering DNA sequence motifs that are associated with DNA methylation states and cell-to-cell variability, and can be used for analyzing the effect of single-nucleotide mutations on DNA methylation. DeepCpG is implemented in Python and publicly available.

**Predicting DNA Methylation State of CpG Dinucleotide Using Genome Topological Features and Deep Networks** [[paper](http://www.nature.com/articles/srep19598)][[web server](http://dna.cs.usm.edu/deepmethyl/)]

This implementation uses a stacked autoencoder with a supervised layer on top of it to predict whether a certain type of genomic region called “CpG islands” (stretches with an overrepresentation of a sequence pattern where a C nucleotide is followed by a G) is methylated (a chemical modification to DNA that can modify its function, for instance methylation in the vicinity of a gene is often but not always related to the down-regulation or silencing of that gene.) This paper uses a network structure where the hidden layers in the autoencoder part have a much larger number of nodes than the input layer, so it would have been nice to read the authors’ thoughts on what the hidden layers represent.

### Single-cell applications <a name='genomics_single-cell'></a>

**DeepCpG - Predicting DNA methylation in single cells**
[[paper](http://dx.doi.org/10.1186/s13059-017-1189-z)]
[[code](https://github.com/cangermueller/deepcpg)]
[[docs](http://deepcpg.readthedocs.io/en/latest/)]

See above.

**CellCnn – Representation Learning for detection of disease-associated cell subsets**
[[code](https://github.com/eiriniar/CellCnn)][[paper](http://biorxiv.org/content/early/2016/03/31/046508)]

This is a convolutional network (Lasagne/Theano) based approach for “Representation Learning for detection of phenotype-associated cell subsets.” It is interesting because most neural network approaches for high-dimensional molecular measurements (such as those in the gene expression category above) have used autoencoders rather than convolutional nets.

**DeepCyTOF: Automated Cell Classification of Mass Cytometry Data by Deep Learning and Domain Adaptation**[[paper](http://biorxiv.org/content/biorxiv/early/2016/05/31/054411.full.pdf)]

Describes autoencoder approaches (stacked AE and multi-AE) to gating (assigning cells into discrete groups) with mass cytometry (CyTOF).

**Using Neural Networks To Improve Single-Cell RNA-Seq Data Analysis**[[preprint](http://biorxiv.org/content/early/2017/04/23/129759)]

Tests a variety of neural network architectures for obtaining a reduced representation of single-cell gene expression data. Introduces a database of tens of thousands of single-cell profiles which can be queried to infer a cell type or state based on this reduced representation.

**Removal of batch effects using distribution-matching residual networks**[[code](https://github.com/ushaham/BatchEffectRemoval)][[paper](https://academic.oup.com/bioinformatics/article-abstract/doi/10.1093/bioinformatics/btx196/3611270/Removal-of-Batch-Effects-using-Distribution)]

Most high-throughput assays in genomics, proteomics etc. are affected to some extent by systematic technical errors, so-called "batch effects". This paper uses a residual neural network to attenuate batch effects by trying to match the distributions of replicate experiments on e.g. single-cell RNA sequencing or mass cytometry. 

### Population genetics <a name='genomics_pop'></a>

**Deep learning for population genetic inference** [[code](https://sourceforge.net/projects/evonet/)][[paper](http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004845)]

**Diet networks: thin parameters for fat genomics** [[manuscript](http://openreview.net/pdf?id=Sk-oDY9ge)]

This weirdly-named paper addresses the frequently encountered problem in genomics where the number of features is much larger than the number of training examples. Here, it is addressed in the context of SNPs (single-nucleotide polymorphisms, genetic variations between individuals). The authors propose a new network parametrization that reduces the number of free parameters using a multi-task architecture which tries to learn a useful embedding of the input features.

## Neuroscience <a name='neuro'></a>

There are potentially lots of implementations that could go here.

**Deep learning for neuroimaging: a validation study** [[paper](http://journal.frontiersin.org/article/10.3389/fnins.2014.00229/abstract)]

**SPINDLE: SPINtronic deep learning engine for large-scale neuromorphic computing** [[paper](http://dl.acm.org/citation.cfm?id=2627625)]
