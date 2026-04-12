Paper Link: https://arxiv.org/abs/2307.15189

**Med-Flamingo: a Multimodal Medical Few-shot Learner (2023)**

* Task: Generative Medical Visual Question Answering (VQA)
* Domain: Multimodal Clinical/Medical Imaging (Radiology, Pathology, Clinical Cases)
* Dataset(s): VQA-RAD, PathVQA, SLAKE, Visual USMLE (novel 618-question open-ended clinical dataset); pretraining on paired/interleaved medical image-text from 4000+ medical textbooks and publications
* Model Type: Flamingo-based VLM (generative transformer)
* Key Idea: Adapt OpenFlamingo-9B to medical domain through continued pretraining on curated medical image-text data; enables in-context few-shot multimodal learning rather than requiring fine-tuning on large labeled datasets
* Method (Short): Continued pretraining of OpenFlamingo-9B on paired and interleaved medical image-text from publications/textbooks; supports few-shot in-context prompting with visual+textual examples; generative decoding for open-ended VQA answers
* Key Results: Up to 20% improvement in clinician ratings vs. baselines; average clinical evaluation rank of 1.67 across datasets; first work to conduct physician-reviewed evaluation of generative medical VQA using interactive annotation app
* Strengths: 
  * First medical VLM with true multimodal few-shot in-context learning; no large-scale fine-tuning required
  * Rigorous human evaluation by clinicians using blinded protocol (not just automated metrics)
  * Created high-quality Visual USMLE benchmark covering diverse specialties beyond narrow radiology/pathology focus; addressed data leakage issues in existing VQA-RAD splits
* Limitations: 
  * Weak performance on PathVQA suggests insufficient pretraining on fine-grained pathology image data; limited by small amount of pathology literature in training corpus
  * Automated metrics (BERT-similarity, exact-match) show poor correlation with clinical usefulness, particularly for generative long-form answers; multimodal few-shot rationales lack robustness when predictions are incorrect
  * Model size (9B) and computational requirements for continued pretraining not fully detailed; generalization to other medical domains beyond those in training data unclear
* Relevance to My Review: Landmark work demonstrating few-shot multimodal learning for medical VLMs; establishes importance of domain-specific pretraining and clinician-in-the-loop evaluation; shows trade-offs between automation and clinical validity in generative medical AI