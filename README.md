# CrafterGPT

> Overview

- CrafterGPT is an experiment that utilizes language models to play a procedurally-generated survival game, specifically Crafter, a 2D version of Minecraft.
- CrafterGPT consists of two agents:
  1. Language model with only "think step-by-step" prompting.
  2. Language model fine-tuned with expert human dataset and "think step-by-step" prompting.
- Both agents utilized the `Llama2-7b` model.
- The experiment shows that fine-tuning language models to human datasets can easily lead to overfitting, compromising its performance.

> Prompt-Engineering Only

- The agent with "thinking step-by-step" prompting scored a `0.9` reward on average across 10 random seeds.
- The agent displayed some level of reasoning, although the limited capabilities of the `Llama-2b` model often lead to hallucination during the "think step-by-step" process.

> Fine-Tuning and Prompt Engineering
