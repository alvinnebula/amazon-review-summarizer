# Amazon-review-summarizer
> - **via bart-large-cnn**

![python](https://img.shields.io/badge/Python-3.9.0%2B-blue)
[![model](https://img.shields.io/badge/model%20-%20Amazon%20Review-lightblue)]([https://huggingface.co/mabrouk/amazon-review-summarizer-bart](https://huggingface.co/facebook/bart-large-cnn?text=The+tower+is+324+metres+%281%2C063+ft%29+tall%2C+about+the+same+height+as+an+81-storey+building%2C+and+the+tallest+structure+in+Paris.+Its+base+is+square%2C+measuring+125+metres+%28410+ft%29+on+each+side.+During+its+construction%2C+the+Eiffel+Tower+surpassed+the+Washington+Monument+to+become+the+tallest+man-made+structure+in+the+world%2C+a+title+it+held+for+41+years+until+the+Chrysler+Building+in+New+York+City+was+finished+in+1930.+It+was+the+first+structure+to+reach+a+height+of+300+metres.+Due+to+the+addition+of+a+broadcasting+aerial+at+the+top+of+the+tower+in+1957%2C+it+is+now+taller+than+the+Chrysler+Building+by+5.2+metres+%2817+ft%29.+Excluding+transmitters%2C+the+Eiffel+Tower+is+the+second+tallest+free-standing+structure+in+France+after+the+Millau+Viaduct.))
[![data](https://img.shields.io/badge/Datasets-%20Amazon%20Review%20Corpus-orange)](https://huggingface.co/datasets/amazon_reviews_multi)
[![api](https://img.shields.io/badge/API-%20Amazon%20Review%20Summarizer-yellow)](https://huggingface.co/mabrouk/amazon-review-summarizer-bart)
![license](https://img.shields.io/badge/license-MIT-lightgreen)

**DS5899 Special Topics  - Course Project** 

**Team members: Mubarak Ganiyu, Alvin Chen**

# Overview
## Model
**Model Intro:** 
> **[_facebook/bart-large-cnn_](https://huggingface.co/facebook/bart-large-cnn?text=The+tower+is+324+metres+%281%2C063+ft%29+tall%2C+about+the+same+height+as+an+81-storey+building%2C+and+the+tallest+structure+in+Paris.+Its+base+is+square%2C+measuring+125+metres+%28410+ft%29+on+each+side.+During+its+construction%2C+the+Eiffel+Tower+surpassed+the+Washington+Monument+to+become+the+tallest+man-made+structure+in+the+world%2C+a+title+it+held+for+41+years+until+the+Chrysler+Building+in+New+York+City+was+finished+in+1930.+It+was+the+first+structure+to+reach+a+height+of+300+metres.+Due+to+the+addition+of+a+broadcasting+aerial+at+the+top+of+the+tower+in+1957%2C+it+is+now+taller+than+the+Chrysler+Building+by+5.2+metres+%2817+ft%29.+Excluding+transmitters%2C+the+Eiffel+Tower+is+the+second+tallest+free-standing+structure+in+France+after+the+Millau+Viaduct.)** - BART(large-sized model) with pretrained checkpoints fine-tuned on CNN Daily Mail
> - BART model pre-trained on English language, and fine-tuned on CNN Daily Mail. It was introduced in the paper BART: Denoising Sequence-to-Sequence Pre-training for Natural Language Generation, Translation, and Comprehension by Lewis et al. and first released in [this repository](https://github.com/pytorch/fairseq/tree/master/examples/bart).

**Model Description:**
> - BART is a transformer encoder-encoder (seq2seq) model with a bidirectional (BERT-like) encoder and an autoregressive (GPT-like) decoder. 
> - BART is pre-trained by (1) corrupting text with an arbitrary noising function and (2) learning a model to reconstruct the original text.
> - BART is particularly effective when fine-tuned for text generation (e.g. summarization, translation) but also works well for comprehension tasks (e.g. text classification, question answering). This particular checkpoint has been fine-tuned on CNN Daily Mail, a large collection of text-summary pairs.

## Datasets
**Datasets Intro:**
> **[_amazon_reviews_multi_](https://huggingface.co/datasets/amazon_reviews_multi)** - The Multilingual Amazon Reviews Corpus
> - It provides an Amazon product reviews dataset for multilingual text classification. The dataset contains reviews in English, Japanese, German, French, Chinese and Spanish, collected between November 1, 2015 and November 1, 2019. Each record in the dataset contains the review text, the review title, the star rating, an anonymized reviewer ID, an anonymized product ID and the coarse-grained product category (e.g. ‘books’, ‘appliances’, etc.) The corpus is balanced across stars, so each star rating constitutes 20% of the reviews in each language.
> - For each language, there are 200,000, 5,000 and 5,000 reviews in the training, development and test sets respectively. The maximum number of reviews per reviewer is 20 and the maximum number of reviews per product is 20. All reviews are truncated after 2,000 characters, and all reviews are at least 20 characters long.

**Data Structure:**
> Each data instance corresponds to a review - JSON instance:
```bash
{
    "review_id":"de_0784695",
    "product_id":"product_de_0572654",
    "reviewer_id":"reviewer_de_0645436",
    "stars":"1",
    "review_body":"Leider, leider nach einmal waschen ausgeblichen . Es sieht super h\u00fcbsch aus , nur leider stinkt es ganz schrecklich und ein Waschgang in der Maschine ist notwendig ! Nach einem mal waschen sah es aus als w\u00e4re es 10 Jahre alt und hatte 1000 e von Waschg\u00e4ngen hinter sich :( echt schade !",
    "review_title":"Leider nicht zu empfehlen",
    "language":"de",
    "product_category":"home"
}

```

**Data Field:**
> - _**review_id**_: A string identifier of the review.
> - _**product_id**_: A string identifier of the product being reviewed.
> - _**reviewer_id**:_ A string identifier of the reviewer.
> - _**stars**_: An int between 1-5 indicating the number of stars.
> - _**review_body**_: The text body of the review.
> - _**review_title**_: The text title of the review.
> - _**language**_: The string identifier of the review language.
> - _**product_category**_: String representation of the product's category.

## API
**How to use**

Use this model with the [pipeline API](https://huggingface.co/transformers/main_classes/pipelines.html):
```bash
from transformers import pipeline
summarizer = pipeline("summarization", model="mabrouk/reddit-summarizer-bart")
review = """ I really like this book. It takes a step-by-step approach to introduce the reader to the IBM Q Experience, to the basics underlying quantum computing, and to the reality of the noise involved in the current machines. This introduction is technical and shows the user how to use the IBM system either directly through the GUI on their website or by running Python code on one's own machine. The text provides examples of small exercises to try and stimulates ideas of new things to try. The IBM Q Exp Qiskit software modules are identified and introduced - Terra, Aer, Ignis, and Aqua, as well as the backends that one can choose to do the computing. The book ends with two great chapters on quantum algorithms.
"""
print(summarizer(review))
>>> [{'summary': 'I really like this book. It takes a step-by-step approach to introduce the reader to the IBM Q Experience, to the basics underlying quantum computing, and to the reality of the noise involved in the current machines. The book ends with two great ...'}]
```

Model card: [Our Hugging Face API](https://huggingface.co/mabrouk/amazon-review-summarizer-bart)

## Video
Explore our model via [YouTube Link](https://youtu.be/v7L6HpE_WTQ)

## Resources
> Mike Lewis et al. **BART: Denoising Sequence-to-Sequence Pre-training for Natural Language Generation, Translation, and Comprehension**. *arXiv preprint arXiv:1910.13461, 2019* - [Link](https://arxiv.org/abs/1910.13461)



