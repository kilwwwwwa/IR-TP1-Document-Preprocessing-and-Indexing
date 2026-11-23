# IR-TP1-Document-Preprocessing-and-Indexing

## How to Run the Notebook
1. Open the notebook in Google Colab.
2. Install the packages listed in 'requirements.txt' if needed ('nltk' and 'pandas').
3. Run all cells from top to bottom (the notebook downloads NLTK English 'stopwords' and uses 'PorterStemmer').
4. Mount Google Drive to save the output files into the 'results/' folder.

## Implementation

- **Collection:** 10 documents (D1–D10) stored in a Python dictionary.
- **Version A:** lowercase, remove punctuation (regex), split to tokens.
- **Version B:** A + NLTK English stopword removal.
- **Version C:** B + Porter stemming.
- **Vocabulary:** sorted set of unique tokens per version.
- **Matrices:** binary and term-frequency term–document matrices built with plain dictionaries and displayed with pandas.
- **Inverted index:** built with `defaultdict`.`search_term()` returns the sorted list of documents containing a term.
- **Verification (Part 5):** checks `search_term` (single-doc, multi-doc, stemmed and unknown terms), checks that every stored position matches the token, checks the matrices against raw counts, and compares the hand-written `small_index` with the generated one.


## Interpretation

Preprocessing makes the vocabulary and the index smaller. The vocabulary drops from 36 terms in version A to 30 after removing stopwords (B) and 24 after stemming (C). Removing stopwords such as "the" and "and" reduces postings from 66 to 59 and stored positions from 69 to 61, because these words carry little meaning. Stemming groups word variants such as document/documents into one term, which lowers postings to 57 and lets a query for "document" match all related documents. The number of positions stays at 61 because stemming changes terms, not token counts. The drawback is that exact forms like "documents" no longer exist in the index.
