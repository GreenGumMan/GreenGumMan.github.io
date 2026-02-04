---
layout: posts
title:  "數字根的公式推導與程式實現"
date:   2025-12-20 16:07:45 +0800
---
# 前言
要考APCS了，我在練習[APCS125題](https://ayooooou.github.io/apcs_read_system/)時發現了一個酷題目，他問的是數字根(Digital root)的概念。
# 基本定義
> 數根是將一正整數的各個位數相加（即橫向相加），若加完後的值大於10的話，則將該值進行橫向相加直到其值小於10為止，或是，將一數字重複做數字和，直到其值小於10為止，則所得的值為該數的數根。 一 [維基百科](https://zh.wikipedia.org/zh-tw/%E6%95%B8%E6%A0%B9)
# 