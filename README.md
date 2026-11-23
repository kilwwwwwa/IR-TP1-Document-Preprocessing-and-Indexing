# IR-TP1-Document-Preprocessing-and-Indexing

## How to Run the Notebook
1. Open the notebook in Google Colab.
2. Install the packages listed in 'requirements.txt' ('nltk' and 'pandas').
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

By analaysing the three versions ( Collection A, B, C ), it showcases how each preprocessing step reshapes the vocabulary and the index in a way or another 
- Version A only lowercases the text and removes punctuation, so "DOCUMENTS" and "documents" count as one term; it has 36 terms and 66 postings.
- Version B drops stop words such as "the", "and" and "to", leaving 30 terms and 59 postings, and documents shrink from 6.9 to 6.1 tokens on average.
- Version C applies Porter stemming, so "documents" and "document" merge, and "retrieval" and "retrieves" both become "retriev", giving 24 terms and 57 postings.

The index is therefore smaller, and a search matches more word variants. The downside is that stems can look odd, unrelated words may merge, and removing stop words shifts the positions of the remaining tokens
