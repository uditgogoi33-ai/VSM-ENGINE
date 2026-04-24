# Vector Space Model (VSM) Search Engine with TF-IDF

This notebook implements a basic Vector Space Model (VSM) search engine using the Term Frequency-Inverse Document Frequency (TF-IDF) weighting scheme. It allows you to search a collection of documents and retrieve the most relevant ones based on your query.

## How it Works

1.  **Document Loading**: Documents are loaded from a JSON file (`data/documents.json`). Each document typically has an ID, title, and content.
2.  **TF-IDF Vectorization**: The loaded documents are transformed into numerical vectors using `TfidfVectorizer` from `sklearn`. TF-IDF assigns a weight to each word in a document, reflecting its importance within that document and across the entire corpus.
    *   **Term Frequency (TF)**: How often a word appears in a document.
    *   **Inverse Document Frequency (IDF)**: A measure of how rare a word is across all documents.
3.  **Cosine Similarity Search**: When a query is entered, it's also vectorized using the *same* TF-IDF model. The cosine similarity between the query vector and all document vectors is calculated. Cosine similarity measures the angle between two vectors, indicating how similar their direction is (and thus how similar the documents are in terms of content).
4.  **Ranking Results**: Documents are ranked by their cosine similarity score (highest similarity first) and the top `k` results are returned.

## Notebook Structure

The notebook is structured into several functional blocks:

*   **Cell 1**: Creates a sample `documents.json` file in a `data` directory if it doesn't exist, providing initial data for the search engine.
*   **Cell 2**: Contains the core Python functions for the search engine:
    *   `load_documents()`: Reads document data from the JSON file.
    *   `build_tfidf_matrix()`: Creates the TF-IDF vectorizer and transforms documents into a TF-IDF matrix.
    *   `search()`: Takes a query, vectorizes it, computes cosine similarity, and returns ranked results.
    *   `display_results()`: Formats and prints the search results.
    *   `main()`: Orchestrates the loading, building, and interactive search loop.

## How to Use

1.  **Run all cells**: Execute all cells in the notebook sequentially.
2.  **Interactive Search**: Once the `main()` function starts, you will see a prompt:
    ```
    🔎 Enter query:
    ```
3.  **Enter your query**: Type your search query (e.g., "Python programming", "Machine Learning") and press Enter.
4.  **View results**: The engine will display the top 5 most relevant documents with their rank, ID, title, similarity score, and a snippet of their content.
5.  **Exit**: Type `quit`, `exit`, or `q` to stop the interactive search.
