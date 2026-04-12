Paper Link: https://arxiv.org/abs/2305.06500

**InstructBLIP (2023)**

* **Task:** Multi-task vision-language instruction following (VQA, image captioning, visual reasoning, visual dialog)

* **Domain:** General-purpose vision-language understanding (not domain-specific medical)

* **Dataset(s):** 26 publicly available vision-language datasets grouped into 11 task categories; 13 held-in for instruction tuning, 13 held-out for zero-shot evaluation (includes GQA, TextVQA, VSR, HatefulMemes, IconQA, ScienceQA, NoCaps, Flickr30K, iVQA, VizWiz, Visual Dialog)

* **Model Type:** MLLM (Transformer-based); extends BLIP-2 with instruction-aware Q-Former

* **Key Idea:** Instruction-aware visual feature extraction enables task-adaptive representation learning instead of static instruction-agnostic features; Q-Former receives instruction tokens as additional input to produce task-specific visual embeddings

* **Method (Short):** Initialize from pre-trained BLIP-2 (frozen image encoder + frozen LLM); finetune instruction-aware Q-Former on 26 datasets transformed to instruction format; use language modeling loss for response generation

* **Key Results:** State-of-the-art zero-shot on all 13 held-out datasets with ~15% relative improvement over BLIP-2; 90.7% ScienceQA accuracy; outperforms larger Flamingo model on zero-shot tasks

* **Strengths:**
  - Comprehensive systematic study with 26 datasets spanning diverse vision-language capabilities
  - Instruction-aware approach demonstrates superior zero-shot generalization vs. multitask learning on unseen tasks
  - Open-sourced models with multiple backbone configurations (FlanT5-XL/XXL, Vicuna-7B/13B)

* **Limitations:**
  - Not designed for domain-specific medical imaging; limited applicability to diagnostic/clinical workflows
  - Only 4 task categories held out at task level; evaluation focuses on general VQA/captioning rather than specialized downstream performance
  - Frozen image encoder and LLM prevent full task-specific adaptation

* **Relevance to Medical VLM/MLLM Review:** Foundational MLLM instruction tuning methodology applicable to medical domain; demonstrates instruction-aware feature extraction as generalizable technique, but lacks medical dataset curation, clinical task diversity, and domain validation necessary for healthcare deployment.