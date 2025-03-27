------------------------------------------
Emotion Recognition -- Theradia WoZ corpus
------------------------------------------

This script processes audio/video files to predict affective labels, dimension summaries, and continuous dimensions using the baseline models trained on the Theradia corpus [1].  
This includes training on three datasets: the corpus of old adults (A-corpus), young adults (J-corpus), and their mixture (mixed corpus). We provide models trained using different feature extraction methods, including expert representations from audio, video, and text (TF-IDF, MFB, FAU) and deep representations (BERT, Wave2Vec XLSR, and CLIP), as well as the multimodal models from expert representations and deep representations.

### Installation:
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

### Usage:

python script.py <file_path> --model <model_type> --corpus <corpus_type> [--output <output_folder>]

file_path: Path to the input audio/video file.
--model: Model type: audio_expert, text_expert, video_expert, text_deep, audio_deep, video_deep, multimodal_expert, multimodal_deep
--corpus: Corpus type: A-Corpus, J-corpus, mixed-corpus
--output: Output folder for saving features and predictions

Example Command:

python main.py sample.mp4 --model multimodal_expert --corpus mixed-corpus --output results_folder

### Output Files

The script generates the following structured output in the results/ directory:



results/
  ├── <file_name>/
  │   ├── Data/
  │   │   ├── Audio/               # Extracted audio file from video
  │   │   ├── Features/            # Extracted features
  │   │   ├── transcription.txt    # Text transcription from audio (google ASR)
  │   ├── predictions/
  │   │   ├── audio_deep/
  │   │       ├── dimsum.csv   # Dimensional Summary predictions
  │   │       ├── continuous_dimensions.csv  # Continuous dimensions 
  │   │       ├── labels.csv   #  Labels Predictions
  │   ├── config.txt    # Configuration used for inference



### References 

[1] FOURNIER, Hippolyte, ALISAMIR, Sina, AZZAKHNINI, Safaa, et al. THERADIA WoZ: An Ecological Corpus for Appraisal-based Affect Research in Healthcare. arXiv preprint arXiv:2405.06728, 2024.
