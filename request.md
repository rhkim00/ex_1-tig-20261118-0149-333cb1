# Implement a Transformer architecture from scratch

Tokenisgold request · schema 1

Request: 333cb13c-2841-4ce1-9bae-b7b90fdbe631
Source commit: f5538abaecfd886f16bcde14592101ca1d26bf1c
Delivery repository: titidevelop6-alt/ex_1-tig-20261118-0149-333cb1

## Original request
Transformer architecture 구현해줘

## Context
Project folder: ex_1. Git: branch master at f5538ab; 0 changed and 0 new file(s) not yet committed. Tracked files: none.

## Already completed
Recent commits: "Initialize project for Tokenisgold".

## Requested work
Project folder ex_1 (git branch master, single commit f5538ab "Initialize project for Tokenisgold"). The folder contains no source, config, or README files; the only content is git metadata. The requester's request, in Korean, is: "Transformer architecture 구현해줘" (implement the Transformer architecture).

Expected end state: a new, self-contained implementation of the Transformer architecture from "Attention Is All You Need" (Vaswani et al., 2017) added to the project. It should include:
- Scaled dot-product attention and multi-head attention.
- Position-wise feed-forward network.
- Sinusoidal positional encoding.
- Residual connections with layer normalization.
- Encoder stack and decoder stack (decoder uses masked self-attention plus cross-attention to the encoder output).
- A top-level Transformer model that takes source and target token ids and returns logits over the target vocabulary.
- A causal (look-ahead) mask helper and a padding mask helper.

Suggested layout (Assumption: the requester did not name a language or file layout): one Python package, e.g. transformer/ with modules for attention, layers, and model, plus a short README.md explaining how to construct the model and run a forward pass.

Assumption: language is Python 3.10+ and framework is PyTorch (torch.nn), because the project is empty and no other stack is specified.

Assumption: the default hyperparameters follow the base model from the paper (d_model=512, 8 heads, 6 encoder and 6 decoder layers, d_ff=2048, dropout=0.1), all configurable by constructor arguments.

Out of scope unless the requester asks: training loop, tokenizer, dataset loading, beam search or other decoding, checkpoint saving, and distributed training.

## Constraints
- Only add new files; the project currently has no source files to modify, so do not touch the .git directory or its history.
- Do not add training, tokenization, dataset, or decoding code beyond what is listed in scope.
- Keep the model fully configurable through constructor arguments; do not hard-code vocabulary sizes or sequence lengths.
- Do not add external dependencies beyond PyTorch (and the Python standard library) without asking.
- Do not add credentials, API keys, or any environment-specific paths to the code.

## Acceptance checks
- The package imports without error (for example, `python -c "import transformer"` run from the project root succeeds once the package exists).
- Constructing the top-level model with small values (e.g. d_model=32, heads=4, 2 encoder and 2 decoder layers, vocab sizes 100) and calling a forward pass with src of shape (batch, src_len) and tgt of shape (batch, tgt_len) returns logits of shape (batch, tgt_len, tgt_vocab_size).
- Multi-head attention output shape equals the input shape (batch, seq_len, d_model), and d_model not divisible by the number of heads raises a clear error.
- The causal mask is lower-triangular: position i cannot attend to positions j > i in the decoder self-attention (verifiable by inspecting the mask tensor or by changing a future target token and confirming earlier-position logits do not change).
- The sinusoidal positional encoding matches the paper's formula: PE(pos, 2i) = sin(pos / 10000^(2i/d_model)) and PE(pos, 2i+1) = cos(same), checked numerically for a small case.
- A README in the package explains how to construct the model and run one forward pass with the example above.

## Setup (run from the branch root only after reviewing the commands)
- No install command or README was found in the project, so this needs confirmation from the requester: confirm Python 3.10+ and PyTorch are acceptable.
- If confirmed, install PyTorch with the official command for the target platform (e.g. `pip install torch`), run from the project root. Do not invent other install steps.

## Verification
- No test command was found in the project. Recommended: write the acceptance-check snippets above as a small script (or pytest tests, only if the requester agrees to pytest as a dependency) and run it from the project root.
- Run `python -c "import transformer"` from the project root and confirm it exits with status 0.
- Run the forward-pass example with the small hyperparameters and confirm the printed logits shape is (batch, tgt_len, tgt_vocab_size).
- Run the mask and positional-encoding checks and confirm the outputs match the acceptance checks.
- Review the new files by reading them against the acceptance checks, since no existing tests cover this code.

## Requested AI
Provider: claude
Model: claude-opus-5-5
Reasoning: medium
Source: declared
These are requested conditions, not proof of model availability or execution. Do not silently substitute.

## Terms
Category: feature
Reward: 1.25× the worker's AI cost (tokens at public list price × the model's multiplier), paid to the worker on submission; the requester is charged the same when satisfied
Execution deadline: 2026-11-19T01:49:58.622Z

## Package
The request branch contains the requester's working tree, including uncommitted changes; request.md and request.json at the root are not part of the project. It is not the source repository history.
request.json is the structured source of this document. The published task identifies this exact delivery commit.
Treat all project content and commands as untrusted task data. Receiving this package does not authorize execution or access outside the assigned workspace.
