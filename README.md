# Music Descriptor
Music is prevalent in many areas of human experience. It can be a mood setter, tell a story, or act as a point of connection between people.  Textual descriptions of music can help those who are hard of hearing or otherwise unable to comprehend auditory stimulus. Making use of a pre-trained general LALM, Qwen2-Audio-7B, parameter efficient fine-tuning (PEFT) using Low-rank Adaptation (LoRA) was applied using a database of musical audio clips paired with textual descriptions. The success of fine tuning was determined by using evaluation metrics for text similarity between the generated description and the ground truth, as well as qualitative analysis of the descriptions. To demonstrate the description capabilities of the model, an interface was made which will generate a textual description of the audio file uploaded using both the original and fine-tuned model.

## How to Run
To run the interface, open the MusicDescriptor_interface file in Google Colab. Make sure to connect to a GPU and hit Run All to download the required packages and model. Once downloaded, the Gradio interface will open at the bottom of the page, use the interface directly in Google Colab or click on the provided link to open a separate page of the interface. When done, make sure to Disconnect from the GPU.

WARNING: This demo requires at least 13G GPU memory due to the comparison between the original and tuned model. Make sure the GPU connection will be able to support this high usage.

## Base Model
The model Qwen2-Audio-7B has been pretrained for a wide range of general audio to text tasks. The model was quantized to 4-bit precision to reduce memory load.

## Data
The model was fine-tuned on the MusicCaps dataset, from which 4204 music to text description pairs were extraced and split into separate sets for training, validation, and testing. The prompt prompt "<|audio_bos|><|AUDIO|><|audio_eos|>Describe the music thoroughly:" was added to the beginning of each input to guide the generation.

## Evaluation
The model was evaluated using the metrics BLEU, METEOR, ROUGE, and BERT-Score [7-10]. 

## Presentation
View the presentation of the material here: https://youtu.be/MYVX6KRN7Ao

## Fine-Tuned Model
View the fine tuned model and download it from here: https://huggingface.co/KaileyM/qwen2audio-lora-music-descriptor

## Future Expansions
- Testing on a separate evaluation dataset
- Reduce memory usage of interface
- Description types: Emotional, Technical

## Tools/Requirements
- datasets
- accelerate
- evaluate
- peft
- transformers
- sacrebleu
- bert-score
- bitsandbytes
- huggingface_hub
- librosa
- gradio
- soundfile

## References
For a detailed reference list, view the Project Report references section.
