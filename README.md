# colossalai-training-code

This is the training code we used for the first prototype models.

Notably, it's based on an old version of HuggingFace's `run_clm.py` example, which was then [adapted by the ColossalAI developers](https://github.com/hpcaitech/ColossalAI/tree/main/examples/language/opt) to make use of some their optimizations. It was then slightly improved to be usable in real-world scenarios (Tensorboard support, proper checkpointing, etc.).

## Usage

This is being committed for archiving purposes, but if you'd like to use it, it _probably_ works. The TL;DR version is:

- Get all the dependencies installed.
  - I have not documented this properly, but installing `transformers` and `colossalai` should _probably_ cover it.
- Put your data in a file called [./data/train.json](./data/).
  - It should be a file where each line is a JSON object containing a `text` field, which contains the actual text that will be tokenized and fed into the model in the training loop.
- Adjust any relevant config parameters in [finetune.bash](./finetune.bash) and run it. If you're lucky, the training loop will eventually start!
  - Metrics should be logged to a `runs` folder inside the OUTPUT_DIR you've specified, so you can host a Tensorboard server there to watch them.
- When it's done, you'll probably want to get a proper HF model out of the training checkpoints. You can do that using the provided [convert_to_hf.py](./src/convert_to_hf.py) utility script.
