# Product-Recommendation-System
This project creates a product recommendation system and search engine using Streamlit for a dataset of Amazon products (amazon_product.csv).

Dependencies

 This code requires the following Python libraries:

pandas (pd)
numpy (np)
nltk
sklearn.feature_extraction.text (TfidfVectorizer)
sklearn.metrics.pairwise (cosine_similarity)
streamlit
Pillow (PIL)
Data Processing

Data Loading: The code loads the product data from "amazon_product.csv" using pandas.
Column Removal: The unnecessary "id" column is dropped from the data.
Text Preprocessing:
A SnowballStemmer for English is defined (stemmer).
A function tokenize_and_stem is created to:
Tokenize the text (split into words) and convert to lowercase.
Perform stemming on each token (reduce words to their root form).
A new column "stemmed_tokens" is added to the data containing the stemmed tokens from the combined "Title" and "Description" columns.
Text Vectorization and Similarity

TF-IDF Vectorizer: A TfidfVectorizer object is created using the custom tokenize_and_stem function as the tokenizer. TF-IDF (Term Frequency-Inverse Document Frequency) is a method for weighting words based on their importance within a document and across documents in the corpus.
Cosine Similarity Function: A function cosine_sim is defined to calculate the cosine similarity between two text inputs. It uses the TF-IDF vectorizer to convert the texts to vectors and then calculates the cosine similarity between those vectors. Cosine similarity measures the similarity between documents based on the angle between their vector representations.
Search Functionality

Search Function: The search_products function takes a user query as input.
It performs stemming on the query using the defined function.
It iterates through each row in the DataFrame and calculates the cosine similarity between the stemmed query and the stemmed tokens in the "stemmed_tokens" column. This similarity score represents how relevant each product is to the user's query.
The DataFrame is sorted by the "similarity" score in descending order (most similar first), and the top 10 results are returned. These results include the "Title", "Description", and "Category" columns.
Streamlit Web App

App Title: The Streamlit app displays a title "Search Engine and Product Recommendation System ON Am Data".
Search Input: A text input field is created where users can enter a product name to search for.
Search Button: A button labeled "Search" is displayed.
Search Results: When the user clicks the "Search" button, the search_products function is called with the user's query. The resulting DataFrame containing the top 10 most relevant products is displayed on the app.
How to Use

Ensure you have the required libraries installed (pip install pandas numpy nltk scikit-learn streamlit pillow).
Place this code and the "amazon_product.csv" file in the same directory.
Run the script using python your_script_name.py.
The Streamlit app will open in your web browser (usually at http://localhost:8501).
Enter a product name in the search bar and click "Search" to see recommendations.

