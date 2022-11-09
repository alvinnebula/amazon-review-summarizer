# Amazon-review-summarizer via bart-large-cnn

![python](https://img.shields.io/badge/Python-3.9.0%2B-blue)
![gradio](https://img.shields.io/badge/Gradio-Gradio%20app-red)
![[data](https://img.shields.io/badge/Hugging%20Face-%20Datasets%3A%20Amazon%20Review-yellow)](https://huggingface.co/mabrouk/reddit-summarizer-bart)
![license](https://img.shields.io/badge/license-MIT-lightgreen)

**DS5899 Special Topics  - Course Project** 
**Author: Mubarak Ganiyu, Alvin Chen**

## Overview
### Model
> **Model:** **[_facebook/bart-large-cnn_](https://huggingface.co/facebook/bart-large-cnn?text=The+tower+is+324+metres+%281%2C063+ft%29+tall%2C+about+the+same+height+as+an+81-storey+building%2C+and+the+tallest+structure+in+Paris.+Its+base+is+square%2C+measuring+125+metres+%28410+ft%29+on+each+side.+During+its+construction%2C+the+Eiffel+Tower+surpassed+the+Washington+Monument+to+become+the+tallest+man-made+structure+in+the+world%2C+a+title+it+held+for+41+years+until+the+Chrysler+Building+in+New+York+City+was+finished+in+1930.+It+was+the+first+structure+to+reach+a+height+of+300+metres.+Due+to+the+addition+of+a+broadcasting+aerial+at+the+top+of+the+tower+in+1957%2C+it+is+now+taller+than+the+Chrysler+Building+by+5.2+metres+%2817+ft%29.+Excluding+transmitters%2C+the+Eiffel+Tower+is+the+second+tallest+free-standing+structure+in+France+after+the+Millau+Viaduct.)** - BART(large-sized model) with pretrained checkpoints fine-tuned on CNN Daily Mail
> - BART model pre-trained on English language, and fine-tuned on CNN Daily Mail. It was introduced in the paper BART: Denoising Sequence-to-Sequence Pre-training for Natural Language Generation, Translation, and Comprehension by Lewis et al. and first released in [this repository (https://github.com/pytorch/fairseq/tree/master/examples/bart).

### Datasets （TODO）
> **Datasets:** **[_amazon_reviews_multi_](https://huggingface.co/datasets/amazon_reviews_multi)**
> - This corpus contains preprocessed posts from the Reddit dataset (Webis-TLDR-17). The dataset consists of 3,848,330 posts with an average length of 270 words for content, and 28 words for the summary.
> - Features includes strings: author, body, normalizedBody, content, summary, subreddit, subreddit_id. Content is used as document and summary is used as summary.



