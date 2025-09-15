## BioNNE-L Shared Task Dataset

### Overview
The BioNNE-L Shared Task Dataset is a biomedical NLP resource for Named Entity Recognition (NER) and relation extraction. It includes annotated English scientific and clinical texts, identifying entities like genes, proteins, chemicals (CHEM), diseases (DISO), and anatomical terms (ANATOMY). Ideal for training and evaluating biomedical text mining models.

### Dataset Structure
Text Files (/data/texts/en/):

Subdirectories: train/, dev/, test/.
Format: Text files named by document_id (e.g., 25591652_en.txt) containing biomedical literature.

Annotation Files (/data/tsv/en/):

Files: bionnel_en_train.tsv, bionnel_en_dev.tsv, bionnel_en_test.tsv.
Format: TSV with columns:

document_id: Links to text file.
text: Entity word/phrase.
entity_type: DISO, CHEM, or ANATOMY.
spans: Character positions (e.g., 976-983).
UMLS_CUI: Medical terminology identifier.


### Example:
textdocument_id     text       entity_type  spans      UMLS_CUI
25591652_en    Seizure    DISO         976-983    C0949003

### Key Features
Annotations: Precise entity spans and types for NER tasks.
Entity Types: Focuses on DISO, CHEM, and ANATOMY.
Real-World Data: Sourced from authentic biomedical literature.
Challenges: Handles overlapping spans and multi-word entities.

### Project Usage
Preprocessing: Loaded texts and annotations, removed overlapping spans, cleaned malformed spans.
Model Training: Used spaCy with a blank NER model, trained for 150 epochs on 54 training documents, achieving a loss of ~31.36.
Evaluation: Strong performance on training data; detected 34/57 entities in test data.
Output: Saved model as nerel_bio_ner_model.zip.

### Technical Details
Data Size: 54 train, 6 dev, 153 test documents.
Dependencies: Python, spaCy, pandas, numpy.
Limitations: Small training set, high loss, some missed entities in testing.

### Applications
Biomedical text mining, clinical decision support, drug discovery, relation extraction.

### Limitations
Small training set limits generalization.
High loss suggests potential overfitting.
Overlapping spans require preprocessing.
