# Capstone Part 1 - ERA-V1 

## Pretraining of Language Model Microsoft

### 1. Large Language Model Microsoft-phi-1.5 pre-trained from scratch on NVIDIA-A100 40GB GPU.

Memory optimized using following:
* Optimizer used to manage memory: 8bit BNB quantized optimizer ( bitsandbytes.optim.Adam8bit )
* torch.cuda.amp.autocast(enabled=True)
* torch.cuda.empty_cache() and gc.collect()
* batch_size = 1
* gradient_accumulation_steps = 4

#### 2. Training logs- Training loss dropped from 11.2392 to 6.2432 in 4000 iterations (steps 1000)

Minimum loss achieved = 5.4183

![image](https://github.com/MPGarg/ERA1_Capstone/assets/120099863/42d641e7-fbe8-469b-9601-cfaad633efc7)
![image](https://github.com/MPGarg/ERA1_Capstone/assets/120099863/6552e023-4271-4ca6-a018-f5ad2cf2f5b2)




