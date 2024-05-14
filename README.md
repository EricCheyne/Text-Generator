# Text Generator

The program can predict the next word in a pseudo-sentence based on the previous words in the sequence and the data that is used to create a statistical model. Natural language processing and preprocessing with the NLTK library, string operations, and the application of statistics in the code is used in the project.

- Stage 1/6: Preprocess the text corpus
  - Open the given text corpus, break the text into separate words, and obtain some properties of the corpus.
- Stage 2/6: Break the dataset int bigrams
  - Bigrams are sequences of two consecutive words from the dataset. Transform the preprocessed corpus into a list of bigrams.
- Stage 3/6: Create a Markov chain model
  - Create a Markov chain model that shows the probability of certain words appearing after a given chain of words.
- Stage 4/6: Generate random text
  - Use the Markov model to generate a text starting with a user-specified word and handle exceptions.
- Stage 5/6: Generate full sentences
  - Modify the algorithm so that sentences always start with capital letters and end with punctuation marks.
- Stage 6/6: Generate sentences based on trigrams
  - Extend the program to create a Markov model based on trigrams in order to generate more sensible sentences.
