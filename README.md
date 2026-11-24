# Experiment 5 : Text Preprocessing on Customer Feedback Using NLTK

## Aim
To perform fundamental Natural Language Processing (NLP) text preprocessing steps—including tokenization, punctuation filtering, stopword removal, and lemmatization—on customer feedback text using Python's `nltk` library.

## Algorithm

1. **Start** the program.
2. **Import Libraries**: Import `nltk` along with `word_tokenize` (from `nltk.tokenize`), `stopwords` (from `nltk.corpus`), and `WordNetLemmatizer` (from `nltk.stem`).
3. **Download NLTK Resources**: Download the required tokenizer models and lexical corpora (`punkt`, `punkt_tab`, `stopwords`, and `wordnet`) using `nltk.download()`.
4. **Define Input Text**: Store the sample customer feedback paragraph in a string variable `text` and display the original text.
5. **Tokenize Text**: Split `text` into individual word and punctuation tokens using `word_tokenize(text)`.
6. **Filter Punctuation & Remove Stopwords**:
   * Load the English stopword set via `set(stopwords.words('english'))`.
   * Retain only alphabetic tokens (`word.isalpha()`) whose lowercase forms are not present in `stop_words`.
7. **Lemmatize Tokens**:
   * Initialize `WordNetLemmatizer()`.
   * Convert each filtered token to lowercase and reduce it to its base dictionary form using `lemmatizer.lemmatize(word.lower())`.
8. **Display Preprocessed Outputs**: Print the tokenized list, stopword-filtered tokens, and final lemmatized words.
9. **Stop** the program.

## Functions and Methods Used

| Category | Function / Class | Purpose / Description |
| :--- | :--- | :--- |
| **Resource Management** | `nltk.download()` | Downloads required NLTK tokenizers (`punkt`, `punkt_tab`) and corpora (`stopwords`, `wordnet`) |
| **Tokenization** | `word_tokenize()` | Splits raw text into individual word and punctuation tokens |
| **Text Filtering** | `stopwords.words('english')` | Retrieves standard English stopwords for noise reduction |
| | `str.isalpha()` & `str.lower()` | Filters out punctuation/numeric tokens and standardizes text casing |
| **Lemmatization** | `WordNetLemmatizer()` | Initializes the WordNet morphological analyzer |
| | `lemmatizer.lemmatize()` | Converts inflected words into their canonical base dictionary forms |

## Program

# Text Preprocessing: Tokenization, Stopword Removal, and Lemmatization using NLTK

import nltk
from nltk.tokenize import word_tokenize
from nltk.corpus import stopwords
from nltk.stem import WordNetLemmatizer

# Step 1: Download NLTK resources
nltk.download('punkt')
nltk.download('punkt_tab')
nltk.download('stopwords')
nltk.download('wordnet')

# Step 2: Sample customer feedback text
text = """The customers were very happy with the products.
The products are amazing, and the delivery services were excellent.
However, some customers complained about delays and poor packaging."""

print("Original Text:")
print(text)

# Step 3: Tokenization
tokens = word_tokenize(text)
print("\nTokenized Words:")
print(tokens)

# Step 4: Stopword Removal & Punctuation Filtering
stop_words = set(stopwords.words('english'))

filtered_words = [
    word for word in tokens
    if word.isalpha() and word.lower() not in stop_words
]

print("\nAfter Stopword Removal and Punctuation Filtering:")
print(filtered_words)

# Step 5: Lemmatization
lemmatizer = WordNetLemmatizer()

lemmatized_words = [
    lemmatizer.lemmatize(word.lower())
    for word in filtered_words
]

print("\nAfter Lemmatization:")
print(lemmatized_words)

## Output
Original Text:
The customers were very happy with the products.
The products are amazing, and the delivery services were excellent.
However, some customers complained about delays and poor packaging.

Tokenized Words:
['The', 'customers', 'were', 'very', 'happy', 'with', 'the', 'products',
 '.', 'The', 'products', 'are', 'amazing', ',', 'and', 'the', 'delivery',
 'services', 'were', 'excellent', '.', 'However', ',', 'some', 'customers',
 'complained', 'about', 'delays', 'and', 'poor', 'packaging', '.']

After Stopword Removal and Punctuation Filtering:
['customers', 'happy', 'products', 'products', 'amazing', 'delivery',
 'services', 'excellent', 'However', 'customers', 'complained',
 'delays', 'poor', 'packaging']

After Lemmatization:
['customer', 'happy', 'product', 'product', 'amazing', 'delivery',
 'service', 'excellent', 'however', 'customer', 'complained',
 'delay', 'poor', 'packaging']

## Result
The program successfully performed tokenization, punctuation filtering, stopword removal, and lemmatization on the customer feedback text using the NLTK library.
