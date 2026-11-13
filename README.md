Named Entity Recognition (NER) System
An end-to-end NLP project that detects names of people, organizations, locations, and miscellaneous entities in English text. It compares four deep learning models and provides an interactive Gradio dashboard.
What the Project Does
- Uses the CoNLL-2003 dataset with four entity types: PER, ORG, LOC, and MISC.
- Preprocesses text with IOB tags, word/character representations, and subword-label alignment.
- Trains and compares LSTM, BiLSTM, BiLSTM + CRF, and fine-tuned DistilBERT.
- Evaluates models with entity-level precision, recall, and F1-score (seqeval).
- Highlights predicted entities in a dark-themed Gradio interface.
- 
Workflow
CoNLL-2003 → Preprocessing → Model Training → Evaluation → Best Model → Gradio Interface

Results
Entity-level F1 on the held-out test set:
Model	Test F1
LSTM	66.23%
BiLSTM	73.68%
BiLSTM + CRF	78.96%
DistilBERT	89.08%


Best model: DistilBERT, selected using validation F1 (92.66%). Its final test F1 is 89.08%.
Note: In the recorded run, the optional pretrained GloVe file was unavailable, so the recurrent models learned word embeddings from random initialization.

Interactive Demo
The Gradio dashboard lets users paste English text, see color-coded entity highlights, and view entity counts and a results table.

Example:
Elon Musk visited London and met executives from Microsoft.

Expected labels: Elon Musk → PER, London → LOC, Microsoft → ORG.
How to Run (Kaggle)
1. Upload ner-project.ipynb to Kaggle Notebooks.
2. Enable GPU and Internet access (when available).
3. Run the notebook cells to train, compare, and export the models.
4. Run the final Gradio cell in the same notebook—no separate app.py is required.
The exported model files are saved under /kaggle/working/deployment_bundle/. If you start a fresh Kaggle session, restore them or rerun the export workflow.
Tech Stack
Python · PyTorch · Hugging Face Transformers · DistilBERT · seqeval · Gradio · Kaggle
Notes
Results are from the notebook's recorded experiment on CoNLL-2003. Accuracy may change on text outside the dataset's news domain. This is an independent educational NLP project.
