# CrafterGPT

> Overview

- CrafterGPT is an experiment that utilizes language models to play a procedurally-generated survival game, specifically [Crafter](https://github.com/danijar/crafter), a 2D version of Minecraft.
- CrafterGPT consists of two agents:
  1. Language model with only "think step-by-step" prompting.
  2. Language model fine-tuned with expert human dataset and "think step-by-step" prompting.
- Both agents utilized the Llama2-7b model.
- Since the Crafter environment, which is implemented as a wrapper of OpenAI Gymnasium, returns observations as a 2D image, the [SmartPlay](https://github.com/microsoft/SmartPlay) library was used to provide a textual description of the observation.
- The experiment shows that fine-tuning language models to human datasets can easily lead to overfitting, compromising its performance.

> Prompt-Engineering Only

- The agent with "thinking step-by-step" prompting scored a `0.9` reward on average across 10 random seeds.
- The agent displayed some level of reasoning, although the limited capabilities of the Llama-2b model often lead to hallucination during the "think step-by-step" process.

> Fine-Tuning and Prompt Engineering

- The expert human dataset available for the Crafter environment was utilized for fine-tuning the language model.
- Since the human dataset only contained numeric observations of the Crafter environment, custom code was implemented to generate a textual representation of each observation.
- Afterwards, the Llama-7b model was fine-tuned with the human dataset using supervised fine-tuning.
- Due to the small size of the model, the supervised fine-tuning easily leads to overfitting, where the agent would output the same action regardless of the observation.
- Thus, it was demonstrated that fine-tuning smaller language models for specific agentic tasks is not feasible.

> Reward Log

Prompt-Engineering Only:
| Rewards (Random Seeds) |
| --- |
| 3.1 |
| 1.1 |
| 0.1 |
| 0.1 |
| 1.1 |
| 0.1 |
| 0.1 |
| 0.1 |
| 2.1 |
| 1.1 |
| **0.9** (avg) |

Fine-Tuned:
| Rewards (Random Seeds) |
| --- |
| -0.9 |
| -0.9 |
| -0.9 |
| -0.9 |
| 0.1 |
| -0.9 |
| -0.9 |
| -0.9 |
| -0.9 |
| -0.9 |
| **-0.8** (avg) |

> File Structure

- `CrafterGPT_SFT_Data_Engineering.ipynb`: Colab notebook for generating textual training dataset from Crafter expert human dataset.
- `CrafterGPT_SFT_Fine_Tuning.ipynb`: Colab notebook for fine-tuning Llama-7b model on training dataset.
- `CrafterGPT_Step_By_Step_Prompt_Engineering.ipynb`: Colab notebook for running prompt-engineering only agent on Crafter environment.
- `CrafterGPT_Step_By_Step_Prompt_Engineering_With_Fine_Tuned_Model.ipynb`: Colab notebook for running fine-tuned agent on Crafter environment.

> HuggingFace Repositories

- [techandy42/llama-2-7b-craftergpt-v1.1](https://huggingface.co/techandy42/llama-2-7b-craftergpt-v1.1): Fine-tuned Llama-7b model.
-  [techandy42/CrafterGPT-Training-Dataset](https://huggingface.co/datasets/techandy42/CrafterGPT-Training-Dataset): Textual training dataset.
