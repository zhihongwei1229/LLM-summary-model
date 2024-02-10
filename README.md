## LLM-summary-model
The notebook file can run in AWS Sagemaker to fine-tune a sequence-to-sequence model for summarizing dialogs.
The Base model is google/flan-t5-base from Huggingface. The training dataset is knkarthick/dialogsum from Huggingface.
I used PEFT(Lora) to fine-tune the base model.
I use RLHF(PPO) to reduce the generated text's hate speech (Detoxify). I use a small pertained model facebook/roberta-hate-speech-dynabench-r4-target as the reward model.

## Issue in the running
Use the latest version of datasets(>2.15.0), an earlier version may cause exceptions.
Do not use urllib3 version 2.2.0, it will cause an exception when uploading files to s3. Version 1.26.17 should work.
Use ml.m5.2xlarge or higher instance in Sagemaker and ensure load flan-t5 as torch_dtype=bfloat16. Otherwise, the kernel may crash.

## Next step
I will add a prompt engineer module to improve performance. Such as templates, few-shot Inference, etc.
I will create an app by Flask to utilize this summary model.
