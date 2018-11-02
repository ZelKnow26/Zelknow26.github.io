---
layout: post
title: 快速傅里叶变换
author: ZelKnow26
tagline: ""
date: 2018.10.18 20:16:12
categories: other
tag: other
---

<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>


本文将介绍两种快速傅里叶变换的方法。

# 快速傅里叶变换

## 前言

最近做课程项目，翻了一下FFT的相关文献，并查找了一下相关的资料，在这里简单总结一下快速傅里叶变换，以备后查。

## FFT介绍

快速傅里叶变换（Fast Fourier transform）是一系列快速进行离散傅里叶变换（DFT）的方法的总称。需要强调的是，FFT的运算结果不是DFT的近似，而是精确等于DFT的结果，且运算时间得到比较大的提高。但是一般来说FFT的算法相对复杂，没有DFT直观。

FFT的基本的思想即是将原始的信号重新排列，利用傅里叶变换中系数因子的周期性与对称性将其分成一系列的长度较小的信号，将问题转化成求解长度较小的DFT问题。通过适当的组合，可以减少重复计算，减少计算次数。

本文将介绍Cooley-Tukey算法和Rader算法。这两种算法的适用范围各不相同，Cooley—Tukey算法适用于N为合数时的情况，Rader算法适用于N为质数的情况。下面分别介绍。

## 基2-FFT

首先先介绍当$N=2^k$时的特殊情况。此时的FFT算法称为基2-FFT算法。当序列长度$N$为2的整数倍时，我们可以利用基2—FFT算法将其化简成$N/2$点的傅里叶变换。我们用$N$次单位根$W_N$来表示$e^{-j2\pi /N}$，容易知道，$W_N$有如下性质：

- *周期性*，$W_N$具有周期$N$，即$W_N^{k+N}=W_N^k$
- *对称性*，$W_N^{k+\frac{N}{2}}=-W_N^k$
- 若$m$是$N$的约数，$W_N^{mkn}=W_{\frac{N}{m}}^{kn}$

重写离散傅里叶变换的公式：

$$X_k=\sum_{n=0}^{N-1}x_nW_N^{nk}$$

将右式分成奇偶两个部分：

$$X_k &= \sum_{n=0}^{\frac{N}{2}-1}x_{2n}W_N^{2nk} + \sum_{n=0}^{\frac{N}{2}-1}x_{2n+1}W_N^{(2n+1)k}\\
    &= \sum_{n=0}^{\frac{N}{2}-1}x_{2n}W_N^{2nk} + W^k_N\sum_{n=0}^{\frac{N}{2}-1}x_{2n+1}W_N^{2nk}\\
    &= \sum_{n=0}^{\frac{N}{2}-1}x_{2n}W_{\frac{N}{2}}^{nk} + W^k_N\sum_{n=0}^{\frac{N}{2}-1}x_{2n+1}W_{\frac{N}{2}}^{nk}\\
    &= X_{even}+W^k_NX_{odd}$$








