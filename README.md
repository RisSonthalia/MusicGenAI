# MusicGenAI: AI-Powered Image-to-Music Generation and Recommendation

MusicGenAI is an innovative project that combines image analysis, music generation, and song recommendation using advanced AI techniques. This system takes an input image, generates a textual caption, creates original music based on that caption, and recommends similar songs from a vast database.

## Features

- Image captioning using BLIP (Bootstrapping Language-Image Pre-training)
- Music generation from textual descriptions using MusicGen
- Song recommendation based on lyrical similarity using RoBERTa and KNN
- Web interface built with Django

## Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/MusicGenAI.git
   cd MusicGenAI
2. Create a virtual environment and activate it:
   ```sh
   python -m venv venv
   source venv/bin/activate   # On Windows, use `venv\Scripts\activate`
4. Install the required packages:
   ```sh
   pip install -r requirements.txt
6. Run the development server:
   ```sh
   python manage.py runserver
## Usage

1. Navigate to `http://localhost:8000` in your web browser.
2. Upload an image or provide a URL to an image.
3. The system will generate a caption, create music, and provide song recommendations.

## Technical Details

### Music Recommendation

Our music recommendation system leverages a dataset of over 100,000 songs from top 100 billboards since 1958. The process involves several key steps:

1. Data Extraction and Preprocessing:
- Dataset creation using Genius and Spotify APIs
- Rigorous data cleaning to ensure consistency in song structures

2. Model Development:
- Feature Engineering: We employ a pre-trained RoBERTa model within the Sentence Transformer framework to transform lyrics into dense vectors for semantic analysis.
- Semantic Similarity: Cosine distance is used in a K-Nearest Neighbor (KNN) model to find songs with lyrics most similar to user queries.
- Fine-Tuning: The model's understanding of lyrics is improved by fine-tuning with paired lyrics and annotations from the Genius community.

3. Results Ranking and Evaluation:
- Score Calibration: A ranking algorithm emphasizes highly relevant lyrics while penalizing less relevant ones to enhance recommendation quality.
- Model Comparison: Performance of pre-trained and fine-tuned models is compared, noting potential overfitting in the fine-tuned model.

### Music Generation

Our music generation process is a two-step procedure:

1. Image Captioning:
We use the BLIP (Bootstrapping Language-Image Pre-training) model from Salesforce to generate textual captions of images. BLIP utilizes a Transformer-based architecture with two main components:
- Visual Encoder: A convolutional neural network (CNN) or vision transformer (ViT) that processes the input image and generates feature vectors representing different regions of the image.
- Textual Decoder: A language model transformer that generates the caption one word at a time, conditioning on both the previously generated words and the image features.

The caption generation process involves image processing, an attention mechanism, contextual understanding, iterative refinement, and fine-tuning on targeted data.

2. Music Generation:
We use the MusicGen model from Facebook to produce music based on the generated captions. Key aspects of MusicGen include:
- Model Architecture: An autoregressive transformer-based decoder that generates music from text or melody inputs.
- Audio Tokenization: Employs EnCodec with Residual Vector Quantization to convert audio into discrete token streams.
- Transformer and Conditioning: Incorporates causal and cross-attention mechanisms, using positional embeddings to enhance temporal coherence.
- Optimization and Training: Utilizes models with up to 3.3B parameters, optimized with techniques such as AdamW and adaptive learning rates.
- Evaluation: Trained on 20K hours of music and evaluated against the MusicCaps benchmark.

This integrated system bridges the gap between visual inputs and musical outputs, creating a unique and engaging user experience.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Acknowledgments

- Course Project for DA213 (Python Lab)
- Instructor: Assistant Prof. Dr. Teena Sharma
