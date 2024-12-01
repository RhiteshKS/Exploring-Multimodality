# Exploring Multimodality and Its Applications

This project implements a **Multimodal Retrieval-Augmented Generation (RAG) System** designed to process and integrate text, images, audio, video, and tables. By leveraging diverse data formats, the system enhances the accuracy and relevance of generated responses for a wide range of applications.

## Datasets
The system utilizes the following datasets:

- **Images:** 
  - [CC0 Stock Images Dataset](https://cc0license.com/)
  - [Pexels Dataset](https://pexels.com)

- **Text:**
  - Wikipedia Example Dataset (25,000 articles)
  - OpenWebText (high-quality web articles)

- **Audio:**
  - ESC-50 (Environmental Sound Classification)
  - TAU Urban Acoustic Scenes 2020 Mobile

- **Video:** 
  - Videos from Pexels converted into frames for processing.

## Video Processing
- Frames extracted from videos using:
  - First frame.
  - Every 5 seconds.
  - Last frame.
- Frames embedded using CLIP and linked back to the original video file.

## Pipelines
### **Pipeline 1**
- **Embedding:** 
  - Used **CLIP** for embedding text, images, and video frames.
  - Used **CLAP** model for embedding audio.
- **VLM:** 
  - Integrated with **GPT-4O** for answering queries.
- **Workflow:** 
  - Query and data embeddings stored in **Chromadb**.
  - Cosine similarity used to retrieve top-k results.
  - Retrieved results passed to GPT-4O for final response generation.

### **Pipeline 2**
- **Embedding:** 
  - Leveraged **ColPali**, an advanced Vision-Language Model (VLM) architecture based on **PaliGemma-3B**, which generates ColBERT-style multi-vector representations for text and images.
- **Token Matching:** 
  - Utilized **ColBert** for late interaction retrieval with token-level matching.
- **VLM:** 
  - Responses generated using **Llama 3.2**.
- **Workflow:** 
  - Each document page treated as an image, divided into patches, and indexed.
  - Queries embedded, matched with stored embeddings, and retrieved data processed via Llama 3.2.

## Tech Stack
- **Programming Language:** Python
- **Database:** Chromadb
- **Models:**
  - **CLIP:** For embedding images and video frames.
  - **CLAP:** For embedding audio features.
  - **ColPali:** For document embeddings, leveraging multi-vector representations from text and visual features.
  - **ColBert:** For token-level matching and late interaction retrieval.
  - **PaliGemma-3B Extension (ColPali):** A specialized Vision-Language Model for document indexing.
  - **GPT-4O** and **Llama 3.2:** For Visual Language Modeling and query responses.

## References
- [CLIP: Learning Transferable Visual Models from Natural Language Supervision](https://arxiv.org/pdf/2103.00020)
- [CLAP: Learning Audio Concepts from Natural Language Supervision](https://arxiv.org/abs/2206.04769)
- [ColPali: Efficient Document Retrieval with Vision-Language Models](https://arxiv.org/abs/2407.01449)
- [HuggingFace Datasets Documentation](https://huggingface.co/docs/datasets/en/index)

## Acknowledgments

This project was inspired by or uses resources from the following repository:

- [Colpali Cookbooks](https://github.com/tonywu71/colpali-cookbooks/tree/main/examples) by [Tony Wu](https://github.com/tonywu71)
- [True Multimodal RAG](https://github.com/ALucek/true-multimodal-rag) by [Adam Łucek](https://github.com/ALucek)
- [Together Cookbook](https://github.com/togethercomputer/together-cookbook/tree/main) by [Together](https://github.com/togethercomputer)
