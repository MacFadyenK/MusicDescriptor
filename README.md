# Music Descriptor
Music can be an important mood setter, a topic for discussion, and a point of connection between people. 
Being able to translate music into textual descriptions is extremely helpful in cases where one cannot listen to audio. 
Efficient generation of these textual descriptions can be used in movie captioning, song summaries, and more. 

The goal of this project is to fine-tune a pre-trained audio transformer/LLM model to create textual descriptions from an audio clip.

## Methods
As LLMs and transformer models are powerful tools for text generation, this music descriptor will utilize a pre-trained audio LLM model to develop this product.
The pre-trained Qwen2-Audio-7B model will be used as a basis for further fine-tuning for the music description task. This model can process audio inputs and output text [1].
Fine tuning will be done through the HuggingFace library, using Parameter-Efficient Fine Tuning (PEFT) methods like Low-Rank Adaptation (LoRA) [2], as it reduces computational cost and has superior performance compared to full fine-tuning [3].

For training, the LP-MusicCaps and/or MusicCaps datasets of music audio and natural langauge captions/descriptions of each audio sample will be used. MusicCaps contains 5521 audio/text pairs which were written by humans [4]. 
LP-MusicCaps is larger, with 0.5M audio clips and 2.2M textual descriptions linked to a music clip [5]. Though it is larger, the captions have been artificially generated with an LLM from audio tags as opposed to being directly written by a human, which might result in less accurate descriptions than those in the original MusicCaps. 
LP-MusicCaps can be used if a larger dataset is needed to increase accuracy of the model.

These datasets will be prepared for input into Qwen2-Audio with additional text instruction telling Qwen2-Audio to describe the music in addition to the audio sample input.

For model evaluation, a portion of the MusicCaps dataset will be set aside for testing. An additional dataset, the Song Describer dataset (SDD), which contains 1106 textual descriptions of 706 2 minute audio samples [6], can be used for more rigorous model evaluation, as it would be completely separated from the model training.

The model will be evaluated using cross-entropy loss metric, as well as other metrics common in music captioning such as BLEU, METEOR, ROGUE, and BERT-score [7-10].

## Sources
[1] Y. Chu et al., “Qwen2-Audio Technical Report,” Jul. 15, 2024, arXiv: arXiv:2407.10759. doi: 10.48550/arXiv.2407.10759.<br>
[2] E. J. Hu et al., “LoRA: Low-Rank Adaptation of Large Language Models,” Oct. 16, 2021, arXiv: arXiv:2106.09685. doi: 10.48550/arXiv.2106.09685.<br>
[3] V. B. Parthasarathy, A. Zafar, A. Khan, and A. Shahid, “The Ultimate Guide to Fine-Tuning LLMs from Basics to Breakthroughs: An Exhaustive Review of Technologies, Research, Best Practices, Applied Research Challenges and Opportunities,” Oct. 30, 2024, arXiv: arXiv:2408.13296. doi: 10.48550/arXiv.2408.13296.<br>
[4] A. Agostinelli et al., “MusicLM: Generating Music From Text,” Jan. 26, 2023, arXiv: arXiv:2301.11325. doi: 10.48550/arXiv.2301.11325.<br>
[5] S. Doh, K. Choi, J. Lee, and J. Nam, “LP-MusicCaps: LLM-Based Pseudo Music Captioning,” Jul. 31, 2023, arXiv: arXiv:2307.16372. doi: 10.48550/arXiv.2307.16372.<br>
[6] I. Manco et al., “The Song Describer Dataset: a Corpus of Audio Captions for Music-and-Language Evaluation,” Nov. 22, 2023, arXiv: arXiv:2311.10057. doi: 10.48550/arXiv.2311.10057.<br>
[7] K. Papineni, S. Roukos, T. Ward, and W.-J. Zhu, “Bleu: a Method for Automatic Evaluation of Machine Translation,” in Proceedings of the 40th Annual Meeting of the Association for Computational Linguistics, P. Isabelle, E. Charniak, and D. Lin, Eds., Philadelphia, Pennsylvania, USA: Association for Computational Linguistics, Jul. 2002, pp. 311–318. doi: 10.3115/1073083.1073135.<br>
[8] S. Banerjee and A. Lavie, “METEOR: An Automatic Metric for MT Evaluation with Improved Correlation with Human Judgments,” in Proceedings of the ACL Workshop on Intrinsic and Extrinsic Evaluation Measures for Machine Translation and/or Summarization, J. Goldstein, A. Lavie, C.-Y. Lin, and C. Voss, Eds., Ann Arbor, Michigan: Association for Computational Linguistics, Jun. 2005, pp. 65–72. https://aclanthology.org/W05-0909/<br>
[9] C.-Y. Lin, “ROUGE: A Package for Automatic Evaluation of Summaries,” in Text Summarization Branches Out, Barcelona, Spain: Association for Computational Linguistics, Jul. 2004, pp. 74–81. https://aclanthology.org/W04-1013/<br>
[10] T. Zhang, V. Kishore, F. Wu, K. Q. Weinberger, and Y. Artzi, “BERTScore: Evaluating Text Generation with BERT,” in International Conference on Learning Representations (ICLR) 2020, Addis Ababa, Ethiopia: International Conference on Learning Representations, Feb. 2020. doi: 10.48550/arXiv.1904.09675.
