# Text Generator

The program can predict the next word in a pseudo-sentence based on the previous words in the sequence and the data that is used to create a statistical model. Natural language processing and preprocessing with the NLTK library, string operations, and the application of statistics in the code is used in the project.

- Stage 1/6: Preprocess the text corpus

  - Open the given text corpus, break the text into separate words, and obtain some properties of the corpus.
  - Preprocess the text corpus Theory In Natural Language Processing (NLP), most work starts by obtaining and preprocessing a text corpus. The word "corpus" might seem scary at first, but it actually simply refers to a collection of textual data. Its contents might be related thematically or based on some particular linguistic phenomena. Corpora usually have some kind of annotation that contains additional information about the text.
  - For most linguistic tasks, the corpus has to be processed before we can access all the important information. One of the most basic operations is tokenization.
  - In this project, the corpus is stored as a .txt file with UTF-8 encoding. When reading a text file in Python, you can specify the encoding of the document like this:
    - f = open("corpus.txt", "r", encoding="utf-8")
  - Description

    - In this project, we will use a corpus that contains the entire script of Game of Thrones. As the corpus will be used to "train" a probabilistic model that will predict the next word in a chain of words, the generated text will resemble the style and vocabulary of the source material. The naturalness of the generated text depends on the data. The bigger the corpus, the better the results. The corpus that we will be using in this project consists of around 300,000 tokens. That is not perfect, but it's good enough to get interesting results.    - 

    - After you complete this project, you can use any corpus you want to experiment with different styles and lengths — you might even compile your own corpus and go with that. But for now, let's just stick to the corpus provided for this project. By the way, don't hesitate to test your program on your own with our corpus.
  - Objectives

    - In order to prepare the corpus for use in this project, we need to take the following important steps:

    - Open and read the corpus from the provided file corpus.txt. The filename should be specified as user input. Note that the file is written in UTF-8 encoding, and the file should be in the same folder as your Python script.

    - Break the corpus into individual words. To create a Markov model, we use the simplest form of tokenization: tokens are separated by whitespace characters such as spaces, tabulation, and newline characters. Punctuation marks should be left untouched since later on, they will play an important role in signaling where a sentence should end.

    - Acquire and print the following information about the corpus under the section of the output called Corpus statistics: - The number of all tokens; the number of all unique tokens, that is, the number of tokens without repetition.
 
    - Each of the above should be in a new line.

    - Take an integer as user input and print the token with the corresponding index. Repeat this process until the string exit is input. Also, make sure that the input index is actually an integer that falls in the range of the corpus. If that is not the case, print an error message and request a new input. Error messages should contain the types of errors (Type Error, Index Error, Value Error, etc.).

    - Each token should be printed in a new line.

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
