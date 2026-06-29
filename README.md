# Parkinson-s-Disease-Severity-Assessment-on-the-UPDRS-Using-Text-Embeddings-Generated-from-Speech
A speech-to-text embedding pipeline is implemented using the pre-trained Whisper transformer model in combination with a transformer-based sentence-embedding model. Specifically, the aim of this implementation is the design of an end-to-end pipeline that transforms pathological speech into meaningful semantic representations. 

## Pipeline Stages
# 1. Dataset indexing
Scans WAV files recursively
Extracts speaker IDs and task labels
Builds structured dataset index
# 2. Metadata integration
Loads clinical metadata (UPDRS, Age, Gender, Hoehn & Yahr)
Merges with audio index
Filters valid PD and HC samples
# 3. Audio transcription
Uses Whisper (large-v2)
Converts speech → text (Spanish)
Uses chunking with overlap for long recordings
# 4. Text embeddings
Uses SentenceTransformer: mixedbread-ai/mxbai-embed-large-v1
Converts transcripts into dense embeddings
Aggregates embeddings per speaker
# 5. Machine learning model
SVR (Support Vector Regression)
Grid search over kernels (RBF, linear, sigmoid)
PCA + scaling pipeline
Leave-One-Out cross-validation

## Dataset (PC-GITA)

This project uses the PC-GITA dataset for Parkinson’s disease speech analysis.

The dataset is **not included in this repository** due to size and licensing constraints.

To run the pipeline, download PC-GITA separately and set the path:

```bash
export PCGITA_DATA_PATH=/path/to/PC-GITA

##Instead of the existing hardcoded root path, replace it with the environment variable `PCGITA_ROOT`.
