---
title: "Introduction to computational methods to quantify tumor heterogeneity"

author: "Jane Merlevede"
date: "October 7, 2019"
layout: post
---


<section class="main-content">
<blockquote>
<p>Author: Jane Merlevede</p>
</blockquote>
<div id="statistical-methods-for-deconvolution" class="section level2">
<h2>Statistical methods for deconvolution</h2>
<p>The widely used methods in matrix factorization are Principal Component Analysis (PCA), Non Negative Matrix Factorization (NMF) and Independent Component Analysis (ICA). Let us give some key aspects on these methods for solving the optimization problem min <span class="math inline">\(||D-T*A||^2\)</span>.</p>
<div id="principal-component-analysis-pca" class="section level3">
<h3>Principal Component Analysis (PCA)</h3>
<p>PCA (Pearson, K, 1901) solves a Singular Value Decomposition: <span class="math inline">\(D=UWVT\)</span> where <span class="math inline">\(W\)</span> is a rectangular diagonal matrix of positive numbers, <span class="math inline">\(U\)</span> and <span class="math inline">\(V\)</span> are squared orthogonal matrices. The constraints here are on the structure of the matrices used in the factorization, which will result in orthogonal components. PCA aims at detecting the correlation between variables and then reduces the dimensionality. By finding components that explain most of the variation in the data, PCA can be limited in the presence of high technical artifacts.</p>
</div>
<div id="non-negative-matrix-factorization-nmf" class="section level3">
<h3>Non Negative Matrix Factorization (NMF)</h3>
<p>In NMF (Paatero, P et al, 1994), the constraints are that the elements of both T and A matrices must be non-negative. It is considered as a natural approximation in different cases as it represents the non-negative nature of most omics data.</p>
</div>
<div id="independent-component-analysis-ica" class="section level3">
<h3>Independent Component Analysis (ICA)</h3>
<p>The constraint in ICA (Herault and Jutten, 1982), also called Blind Source Separation, is statistical independence between columns of A. The multivariate signal is decomposed into components, with non-Gaussian distributions, that are as independent as possible. The resulting components should minimize statistical dependence, in the aim of identifying distinct biological processes. The constraints of statistical independence is equivalent to maximizing non-gaussianity of data point projections onto the components. The idea is to use higher-order moments for matrix approximation, while considering all Gaussian signals as noise (Comon, P, 1994).</p>
<blockquote>
<p>Several studies have compared these methods in the context of this problematic (Zinovyev, A et al, 2013 and Cantini, L et al, 2019).</p>
</blockquote>
</div>
</div>
<div id="how-to-use-omic-data-for-deconvolution" class="section level2">
<h2>How to use omic-data for deconvolution?</h2>
<p>For the main data types on which deconvolution can be applied, let us mention some of the tools that can be used.</p>
<div id="methylation-levels" class="section level3">
<h3>Methylation levels</h3>
<p>The three methods used in the <strong>Health data challenge (1st edition)</strong> were based on NMF (RefFreeEWAS: Houseman, EA et al, 2014 - EDEc: Onuchic, V et al, 2016 - MeDeCom: Lutsik, P et al, P, 2017). Reference-Free Adjustment for Cell-Type composition (ReFACTor) (Rahmani, E et al, 2016) is an unsupervised method for the correction of cell-type heterogeneity based on PCA. There are also other methods, like the one proposed by Liang, C et al, (bioRxiv) 2019 where the authors used a hybrid method of stability selection and elastic net. The advantage of methylation data in this type of problem is that it is one of the most reproducible among molecular experiments, which allows easier integration of different datasets.</p>
</div>
<div id="gene-expression" class="section level3">
<h3>Gene expression</h3>
<p>Most of the recent tools proposed to identify immune and stromal cell populations are supervised methods like CIBERSORT (Newman, A et al, 2015) or MCPCounter (Becht, E et al, 2016). They are not matrix factorization methods. The use of unsupervised tools for the identification of cell populations in gene expression seems quite limited until now. Few NMF-based methods have been developed (Brunet, J-P et al, 2004, Repsilber, D et al, 2010, Moffitt, R et al 2015, Gaujoux R, Seoighe C, 2012 (semi-supervised approach), Liu, Y et al, 2017). There are also few tools based on ICA: BIODICA (Kairov, U et al, 2017), DeconICA (<a href="https://github.com/UrszulaCzerwinska/DeconICA" class="uri">https://github.com/UrszulaCzerwinska/DeconICA</a>).</p>
</div>
<div id="mutational-signatures" class="section level3">
<h3>Mutational signatures</h3>
<p>Most of the methods developed so far for mutational signature extraction are based on NMF as described in this review (Baez-Ortega A, 2019). The most well-known method, which rely on NMF, was published in Alexandrov, L et al, 2013 and was reused in several publications, including Alexandrov, L et al, 2018.</p>
</div>
</div>
</section>
