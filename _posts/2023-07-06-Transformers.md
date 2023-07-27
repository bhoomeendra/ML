---
title: Transformers (Attention is all you need)
author: Bhoomeendra 
date: 2023-07-27
category: Jekyll
layout: post
comments: true
---

In this blog, I will take the approach of understanding what goes in and out of each part of transformer. I will try to explain the transformer in a way that we can understand how the vectors are generated at each layer.

We first start with a dataset which consists of sentences in a language. We will call this language as source language. We will also have a target language. The target language is the language in which we want to translate the source language. The dataset will have pairs of sentences in source and target language.

The first problem is tokenization how do we convert sentences into tokens this is where tokenization algorithems come into picture. We will use BPE (Byte Pair Encoding) algorithm for tokenization. The BPE algorithm is a simple algorithm which is based on the frequency of the words in the dataset. The algorithm is as follows:

1. Initialize the vocabulary with all the characters in the dataset.
2. Find the most frequent pair of characters in the dataset.
3. Merge the most frequent pair of characters into a single character.
4. Repeat step 2 and 3 until the vocabulary size reaches the desired size.

We now have a list of tokens that are used to tokenize the sentences in the dataset. We will use the tokens to convert the sentences into vectors with the help of an embedding layer every token will be mapped to a vector based on its token id. Now we add position encoding with this because transformer in it self is position invariant so we need to add position encoding to the tokens. The position encoding is a vector that is added to the embedding vector. The position encoding is a vector that is generated based on the position of the token in the sentence. The position encoding is generated using the following formula:

$$ PE_{(pos, 2i)} = sin(pos/10000^{2i/d_{model}}) $$
$$ PE_{(pos, 2i+1)} = cos(pos/10000^{2i/d_{model}}) $$

where $pos$ is the position of the token in the sentence, $i$ is the index of the dimension of the embedding vector and $d_{model}$ is the dimension of the embedding vector. The position encoding is added to the embedding vector to get the final embedding vector.

The embedding vector is passed through an encoder. The encoder is a stack of $N$ identical layers. Each layer has two sub-layers. The first sub-layer is a multi-head self-attention layer and the second sub-layer is a feed-forward network.

We have embedding combined with position encoding as $$X_{nxd}$$ where n is the number of words and d is the dimension of the embedding vector. Now in self-attention block, we have 3 learnable matrices which are $$W_{q}$$, $$W_{k}$$ and $$W_{v}$$ which are of the dimension $$ d x 64 $$ and used to generate query, key and value vectors. We get $$ Q = XW_{q} $$ $$ K = XW_{k} $$ $$ V = XW_{v} $$ hence we get $$ Q_{nx64} $$, $$ K_{nx64} $$ and $$ V_{nx64} $$.

Now we calculate the attention weights by using $$ Q $$ and $$ K $$ as follows $$ A = softmax(\frac{QK^{T}}{\sqrt{d}}) $$ where $$ A_{nxn} $$ is the attention matrix (The softmax is along the rows of the attention matrix). Now we calculate the output of the self-attention block as follows $$ O = AV $$ where $$ O_{nx64} $$ is the output of the self-attention block.

Now we will have this output for multiple attention heads. We will have 8 attention heads. We will have 8 $$ Q $$, $$ K $$ and $$ V $$ matrices. We will concatenate the output of all the attention heads to get the final output this will be $$ O_{nx8x64} $$. Now this is multiplied with a learnable matrix $$ W_{o} $$ of dimension $$ 8x64 x d $$ to get the final output of the self-attention block as $$ O_{nxd} $$. Now we add a residual connection to the output of the self-attention block as follows $$ O_{nxd} = O_{nxd} + X_{nxd} $$. Now we pass this output through a layer normalization layer to get the final output of the self-attention block as follows $$ O_{nxd} = LN(O_{nxd}) $$.

After this we pass the output of the self-attention block through a feed-forward network. The feed-forward network is a simple network with two linear layers with a ReLU activation function in between. $$FF(x) = max(0,xW_1+b_1)W_2 + b_2 $$ The output of the feed-forward network is added to the output of the self-attention block as follows $$ O_{nxd} = O_{nxd} + FF(O_{nxd}) $$ where $$ FF $$ is the feed-forward network. Now we pass this output through a layer normalization layer to get the final output of the encoder block as follows $$ O_{nxd} = LN(O_{nxd}) $$.

We have 6 such encoder blocks.  

