---
language: en
thumbnail: SOCIAL_LINK
tags:
- huggingtweets
widget:
- text: "My dream is"
---

<div>
<div style="width: 132px; height:132px; border-radius: 50%; background-size: cover; background-image: url('USER_PROFILE')">
</div>
<div style="margin-top: 8px; font-size: 19px; font-weight: 800">USER_NAME 🤖 AI Bot </div>
<div style="font-size: 15px">@USER_HANDLE bot</div>
</div>

I was made with [huggingtweets](https://github.com/borisdayma/huggingtweets).

Create your own bot based on your favorite user with [the demo](https://colab.research.google.com/github/borisdayma/huggingtweets/blob/master/huggingtweets-demo.ipynb)!

## How does it work?

The model uses the following pipeline.

![pipeline](https://github.com/borisdayma/huggingtweets/blob/master/img/pipeline.png?raw=true)

To understand how the model was developed, check the [W&B report](https://wandb.ai/wandb/huggingtweets/reports/HuggingTweets-Train-a-Model-to-Generate-Tweets--VmlldzoxMTY5MjI).

## Training data

The model was trained on [@USER_HANDLE's tweets](https://twitter.com/USER_HANDLE).

| Data | Quantity |
| --- | --- |
| Tweets downloaded | TWEETS_DL |
| Retweets | RETWEETS |
| Short tweets | SHORT_TWEETS |
| Tweets kept | TWEETS_KEPT |

[Explore the data](WANDB_PREPROCESS/artifacts), which is tracked with [W&B artifacts](https://docs.wandb.com/artifacts) at every step of the pipeline.

## Training procedure

The model is based on a pre-trained [GPT-2](https://huggingface.co/gpt2) which is fine-tuned on @USER_HANDLE's tweets.

Hyperparameters and metrics are recorded in the [W&B training run](WANDB_TRAIN) for full transparency and reproducibility.

At the end of training, [the final model](WANDB_TRAIN/artifacts) is logged and versioned.

## How to use

You can use this model directly with a pipeline for text generation:

```python
from transformers import pipeline
generator = pipeline('text-generation',
                     model='huggingtweets/USER_HANDLE')
generator("My dream is", num_return_sequences=5)
```

## Limitations and bias

The model suffers from [the same limitations and bias as GPT-2](https://huggingface.co/gpt2#limitations-and-bias).

In addition, the data present in the user's tweets further affects the text generated by the model.

## About

*Built by Boris Dayma*

[![Follow](https://img.shields.io/twitter/follow/borisdayma?style=social)](https://twitter.com/intent/follow?screen_name=borisdayma)

For more details, visit the project repository.

[![GitHub stars](https://img.shields.io/github/stars/borisdayma/huggingtweets?style=social)](https://github.com/borisdayma/huggingtweets)
