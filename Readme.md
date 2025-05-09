

## Chapter 1:
- Supervised Finetuning (SFT): Fine tuning a base model to function as a chat model

## Chapter 2:
- Preference Alignment with 2 techniques:
    - Direct Preference Optimization (DPO): 
        - Requires the models first be trained with SFT and then aligned based on converstation records.
          Each record has to have a chosen and a rejected converstation to help the model understand
          what type of converstation it should move forward with.
        - Builds on the converstational knowledge the model has gained from SFT.
    - Odds Ratio Performance Optimization (ORPO) :
        - Combines SFT and preference alignment together in a single training pipeline.
        - Start trainig the model from scractch to have a task specific converstation.

## Chapter 3:
- Parameter Efficient Fine-tuning : 
  Adapaters are low rank (certain number of rows and columns per matrix) that can be fine-tune and added to LLM 
  weights to align the LLM output to a specific case. 
  - __finetune_sft_peft__ notebook describes the steps to setup LoraConfig and SFTConfig to fine-tune adapters.
    - Original model weights are kept frozen at the time of fine-tuning. Only adapter weights are updated.
    - The adapaters weights are small. Can be added back to the original model weights or kept separate.
- Prompt Tuning :
  - Soft prompts are generated from the frozen model weights. These prompts are vectors and not actual text although they start as actual text (example the original prompt or question that the model could not respond to).
  - Effective if you have a big model with > 10B parameters. Does not seem to be effective for small models.

## Chapter 4 : Using LightEval HF library to setup pipleine for eval
- Add evaluations to the pipeline
- Design your custom eval tasks and metrics.
- Note : library has some issue with Torch and HF versions. Use with caution.