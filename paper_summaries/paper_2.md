

**BLIP-2 (2023)**

Paper Link: https://arxiv.org/abs/2301.12597

* **Task:** VQA / Image Captioning / Image-Text Retrieval / Vision-to-Language Generation

* **Domain:** General Vision-Language (not medical)

* **Dataset(s):** Pre-training: COCO, Visual Genome, CC3M, CC12M, SBU, LAION-400M (129M images total); Downstream: VQAv2, Visual Genome, COCO Caption, NoCaps, Flickr30K

* **Model Type:** MLLM / VLM based on frozen components (Vision Transformer + LLM with trainable Q-Former)

* **Key Idea:** Efficient vision-language pre-training by freezing pre-trained image encoders and LLMs, using only a lightweight Querying Transformer (Q-Former) as a trainable modality bridge—avoiding expensive end-to-end training while achieving SOTA performance.

* **Method (Short):** 
  - Stage 1: Vision-language representation learning (Q-Former trained with ITC, ITM, ITG losses on frozen ViT encoder)
  - Stage 2: Vision-to-language generative learning (Q-Former adapted to frozen LLM input space for text generation)
  - Q-Former: BERT-like transformer with learned query tokens + shared self-attention layers between image and text interaction

* **Key Results:** 
  - VQAv2 zero-shot: 8.7% improvement over Flamingo-80B with 54× fewer trainable parameters
  - SOTA on image captioning (COCO, NoCaps), image-text retrieval (COCO, Flickr30K)
  - Emerging zero-shot instruction-following capability for visual reasoning and conversational understanding

* **Strengths:**
  - Massive parameter efficiency: leverages frozen pre-trained models, only trains lightweight Q-Former
  - Strong generalization: achieves SOTA across multiple vision-language tasks despite simpler architecture
  - Flexibility: compatible with different frozen encoders (ViT-L/14, ViT-g/14) and LLMs (OPT, FlanT5)

* **Limitations:**
  - Relies on quality of frozen components; performance bounded by underlying image encoder and LLM
  - Stage 1 representation learning critical for performance (catastrophic forgetting observed without it; 15% drop in OPT models)
  - Limited to capabilities of frozen models; cannot improve visual understanding beyond pre-trained encoder capacity
  - Zero-shot performance gaps vs. specialized models; secondary to Flamingo on OK-VQA (open-world knowledge bias)

* **Relevance to Your Review:** 
  Foundational MLLM architecture using efficient modality bridging rather than end-to-end training. Demonstrates how to adapt frozen unimodal models for multimodal tasks—principle directly applicable to medical VLMs. Absence of medical domain evaluation limits direct relevance, but training strategy is influential for resource-constrained medical AI systems.