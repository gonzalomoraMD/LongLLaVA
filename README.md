![header](./assets/header.png) 

<p align="center">
   📃 <a href="https://arxiv.org/abs/2409.02889" target="_blank">Paper</a> • 🌐 <a href="" target="_blank">Demo</a> • 🤗 <a href="https://huggingface.co/FreedomIntelligence/LongLLaVA-53B-A13B" target="_blank">LongLLaVA-53B-A13B</a> • 🤗 <a href="https://huggingface.co/FreedomIntelligence/LongLLaVA-9B" target="_blank">LongLLaVA-9B</a> 
</p>

![efficiency](./assets/singleGPU.png) 

## 🌈 Update

* **[2024.09.05]** LongLLaVA repo is published！🎉
* **[2024.10.12]** [LongLLaVA-53B-A13B](https://huggingface.co/FreedomIntelligence/LongLLaVA-53B-A13B), [LongLLaVA-9b](https://huggingface.co/FreedomIntelligence/LongLLaVA-9B) and [Jamba-9B-Instruct](https://huggingface.co/FreedomIntelligence/Jamba-9B-Instruct) are repleased！🎉 

## Architecture

<details>
  <summary>Click to view the architecture image</summary>

  ![Architecture Image](./assets/arch.png)

</details>


## Results

<details>
  <summary>Click to view the Results</summary>

  - Main Results
      ![Main Results](./assets/result1.png) 
  - Diagnostic Results
      ![Diagnostic Results](./assets/diaresult.png)
  - Video-NIAH
      ![Video-NIAH](./assets/NIAH.png)

</details>



## Results reproduction

### 1. Environment Setup

  ```bash
  pip install -r requirements.txt
  ```

### 2. Data DownLoad and Construction

<details>
  <summary>Dataset Taxonomy</summary>

  ![Dataset](./assets/dataset.png) 

</details>

- Dataset DownLoading and Construction
  > Coming Soon.




### 3. Training

- Downloading Language Models
  <p align="left">
   🤗 <a href="https://huggingface.co/FreedomIntelligence/Jamba-9B-Instruct" target="_blank">Jamba-9B-Instruct</a> 
  </p>

- Stage I: Single-image Alignment.
  ```bash
  bash Align.sh
  ```
- Stage II: Single-image Instruction-tuning.
  ```bash
  bash SingleImageSFT.sh
  ```
- Stage III: Multi-image Instruction-tuning. 
  ```bash
  bash MultiImageSFT.sh
  ```

### 4. Evaluation

- Command Line Interface

```bash
python cli.py --model_dir path-to-longllava
```


- Model Inference

```python
query = 'What does the picture show?'
image_paths = ['image_path1'] # image or video path

from cli import Chatbot
bot = Chatbot(path-to-longllava)
output = bot.chat(query, image_paths)
print(output) # Prints the output of the model
```

- Benchmarks
```bash
python Eval.sh
```


### 5. Reproduce other results in Paper

- FLOPs
```bash
python /utils/cal_flops.py
```

- Prefill Time & Throughput & GPU Memory Usage
```bash
python ./benchmarks/Efficiency/evaluate.py
python ./benchmarks/Efficiency/evaluatevllm.py
```

- DownCycling
To Transfer Jamba-MoE to Dense 
```bash
python ./utils/dense_downcycling.py
```


## TO DO

- [ ] Release Data Construction Code

## Acknowledgement

- [LLaVA](https://github.com/haotian-liu/LLaVA): Visual Instruction Tuning (LLaVA) built towards GPT-4V level capabilities and beyond.

## Citation

```
@misc{wang2024longllavascalingmultimodalllms,
      title={LongLLaVA: Scaling Multi-modal LLMs to 1000 Images Efficiently via Hybrid Architecture}, 
      author={Xidong Wang and Dingjie Song and Shunian Chen and Chen Zhang and Benyou Wang},
      year={2024},
      eprint={2409.02889},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2409.02889}, 
}
```
