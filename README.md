# Capstone Part 1 - ERA-V1 

## Pretraining of Language Model Microsoft

Large language model is trained from scratch and loss has reduced from 11 to range of 6. This shows if we apply more resources (GPU time :) ) and train further it can learn even more.

### Large Language Model Microsoft-phi-1.5 pre-trained from scratch on NVIDIA-A100 40GB GPU.

Memory optimized using following:
* Optimizer used to manage memory: 8bit BNB quantized optimizer ( bitsandbytes.optim.Adam8bit )
* torch.cuda.amp.autocast(enabled=True)
* torch.cuda.empty_cache() and gc.collect()
* batch_size = 1
* gradient_accumulation_steps = 4

### Training logs

Training loss dropped from 11.2392 to 6.2432 in 4000 iterations (steps 1000)

Minimum loss achieved = 5.4183

![image](https://github.com/MPGarg/ERA1_Capstone/assets/120099863/42d641e7-fbe8-469b-9601-cfaad633efc7)
![image](https://github.com/MPGarg/ERA1_Capstone/assets/120099863/6552e023-4271-4ca6-a018-f5ad2cf2f5b2)

# Capstone Part 2 - ERA-V1 

## Training of Multi-modal LLM

### Projection Layer Training with COCO 2017 dataset

* Resources used to train: NVIDIA-A100 40GB GPU (Google colab)
* Duration of training: 4 hours (approx)
* Loss started at around 7.0047 and after 10,000 steps (end of training) it was around 4.4909
* Batch size 4
* Optimizer: torch.optim.Adam
* Learning rate: 1e-4

#### Loss graph for these steps:

![image](https://github.com/MPGarg/ERA1_Capstone/assets/120099863/3c43a7a6-39f8-4d00-8575-8a3813d3de62)

#### Training log: 

At start of training:

![image](https://github.com/MPGarg/ERA1_Capstone/assets/120099863/f991ac2a-87f6-49a8-9e2e-70c59a21666d)

At around 10k step (end of training):

![image](https://github.com/MPGarg/ERA1_Capstone/assets/120099863/595943c6-bac5-4229-83f8-7b934914957d)

#### GPU Usage during training:

![image](https://github.com/MPGarg/ERA1_Capstone/assets/120099863/2e2318af-6cfe-4242-aeec-4f950da3e050)

### QLoRa Finetuning

* Resources used to train: NVIDIA-V100 16GB GPU (Google colab)
* Duration of training: 2.5 hours (approx)
* Loss started at around 5.4562 and after 20,000 steps (end of training) it was around 2.8801
* Batch size 4
* Optimizer: torch.optim.Adam
* Clip model "wkcn/TinyCLIP-ViT-61M-32-Text-29M-LAION400M"
* Phi model "microsoft/phi-2"

#### Loss graph for these steps:

![image](https://github.com/MPGarg/ERA1_Capstone/assets/120099863/c288d1d8-c475-424e-93ee-18bd71432660)

#### Training log: 

At start of training:

![image](https://github.com/MPGarg/ERA1_Capstone/assets/120099863/ab4ab061-7f6b-47f6-a6e5-caa5e41f1bb2)

At around 20k step (end of training):

![image](https://github.com/MPGarg/ERA1_Capstone/assets/120099863/a2ab0889-5e49-4cca-9692-05a7029fe0c4)

#### GPU Usage during training:

![image](https://github.com/MPGarg/ERA1_Capstone/assets/120099863/c454ce3d-dccf-40cd-87a9-d2870b845002)

## Deployment of Multi-modal LLM

It is hosted on Hugging Face on following link (CPU Basic): [link](https://huggingface.co/spaces/MadhurGarg/multi-modalLLM)

When tested with text as input in combination with uploaded image:

![image](https://github.com/MPGarg/ERA1_Capstone/assets/120099863/62c58ace-cbaf-4a89-b383-02622c9d9be0)

When tested with audio as input in combination with uploaded image:

![image](https://github.com/MPGarg/ERA1_Capstone/assets/120099863/434fda1f-8e43-4900-b458-64d89fbdf3bd)

Audio here is: "Explain what is happening"

