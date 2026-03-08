# Retrieval-Based Chatbot: Master and Margarita

## Dataset
The project uses Mikhail Bulgakov's novel *Master and Margarita*.
The text is split into paragraphs with a minimum length of 120 characters (about 2025 passages in the current run).
No manual labels are required (unsupervised retrieval setup).

## Pipeline
No model training is performed. The notebook uses pre-trained components:
- **Retriever:** `intfloat/multilingual-e5-small` (sentence-transformers)
- **Vector index:** FAISS `IndexFlatIP` (cosine similarity on normalized vectors)
- **Keyword baseline:** BM25 (`rank-bm25`)

Given a user query, the system retrieves the most relevant paragraph(s) and returns:
- retrieved text
- similarity/relevance score

## What Is Included in `main.ipynb`
- Data loading and preprocessing
- BM25 baseline retrieval
- Dense retrieval with sentence embeddings
- FAISS indexing and search
- Inference demo with similarity scores
- BM25 vs Dense/FAISS quantitative comparison
- Qualitative examples (where vector search is better/worse)

## Run in Google Colab
1. Open `main.ipynb` in Google Colab.
2. Upload `Bulgakov_Mihail_Master_i_Margarita.txt`.
3. If needed, update the file path in the data cell (default in notebook: `/content/LLM_1/Bulgakov_Mihail_Master_i_Margarita.txt`).
4. Run all cells top to bottom.
5. Edit `user_query` in the inference section to test your own questions.

## Run Locally
1. Install dependencies:
   `pip install -r requirements.txt`
2. Open and run `main.ipynb`.