# Text Generator

The program can predict the next word in a pseudo-sentence based on the previous words in the sequence and the data that is used to create a statistical model. Natural language processing and preprocessing with the NLTK library, string operations, and the application of statistics in the code is used in the project.

- Stage 1/6: Preprocess the text corpus

  - Open the given text corpus, break the text into separate words, and obtain some properties of the corpus.
  - Preprocess the text corpus Theory In Natural Language Processing (NLP), most work starts by obtaining and preprocessing a text corpus. The word "corpus" might seem scary at first, but it actually simply refers to a collection of textual data. Its contents might be related thematically or based on some particular linguistic phenomena. Corpora usually have some kind of annotation that contains additional information about the text.
  - For most linguistic tasks, the corpus has to be processed before we can access all the important information. One of the most basic operations is tokenization.
  - In this project, the corpus is stored as a .txt file with UTF-8 encoding. When reading a text file in Python, you can specify the encoding of the document like this:
    - f = open("corpus.txt", "r", encoding="utf-8")
  - Description

    - In this project, we will use a corpus that contains the entire script of Game of Thrones. As the corpus will be used to "train" a probabilistic model that will predict the next word in a chain of words, the generated text will resemble the style and vocabulary of the source material. The naturalness of the generated text depends on the data. The bigger the corpus, the better the results. The corpus that we will be using in this project consists of around 300,000 tokens. That is not perfect, but it's good enough to get interesting results.

    - After you complete this project, you can use any corpus you want to experiment with different styles and lengths — you might even compile your own corpus and go with that. But for now, let's just stick to the corpus provided for this project. By the way, don't hesitate to test your program on your own with our corpus.

  - Objectives

    - In order to prepare the corpus for use in this project, we need to take the following important steps:

    - Open and read the corpus from the provided file corpus.txt. The filename should be specified as user input. Note that the file is written in UTF-8 encoding, and the file should be in the same folder as your Python script.

    - Break the corpus into individual words. To create a Markov model, we use the simplest form of tokenization: tokens are separated by whitespace characters such as spaces, tabulation, and newline characters. Punctuation marks should be left untouched since later on, they will play an important role in signaling where a sentence should end.

    - Acquire and print the following information about the corpus under the section of the output called Corpus statistics: - The number of all tokens; the number of all unique tokens, that is, the number of tokens without repetition.

    - Each of the above should be in a new line.

    - Take an integer as user input and print the token with the corresponding index. Repeat this process until the string exit is input. Also, make sure that the input index is actually an integer that falls in the range of the corpus. If that is not the case, print an error message and request a new input. Error messages should contain the types of errors (Type Error, Index Error, Value Error, etc.).

    - Each token should be printed in a new line.

- Stage 2/6: Break the dataset into bigrams

  - Theory

    - To study how texts are structured, we usually have to take into consideration not just individual words but sequences of words and the relationships between them. These sequences might consist of any number of words, but usually, the number is limited to only two or three.
    - A sequence of any number of adjacent tokens is called an n-gram, where n is the number of tokens. A sequence of two adjacent tokens is called a bigram. Not surprisingly, a sequence of three adjacent tokens is a trigram. For now, we will stick to bigrams only.

  - When referring to bigrams in this project, we divide them into two parts: head and tail. In our case, the first token of the bigram is the head and the second token is the tail. For example, in the bigram good night, good is the head and night is the tail.

  - Description

    - After the training data is acquired and preprocessed, it has to be transformed into a Markov chain model. The first step is to map the connections between tokens in the corpus. For this, we are going to use bigrams.

  - Objectives
    - Transform the corpus into a collection of bigrams. The results should contain all the possible bigrams from the corpus, which means that:
    - Every token from the corpus should be a head of a bigram with the exception of the last token which cannot become a head since nothing follows it;
    - Every token from the corpus should be a tail of a bigram with the exception of the first token which cannot possibly be the tail of a bigram because nothing precedes it.
    - Output the number of all bigrams in the corpus.
    - Take an integer as user input and print the bigrams with the corresponding index. Repeat this process until the string exit is input. Also, make sure that the input is actually an integer that falls in the range of the collection of bigrams. If that is not the case, print an error message and request a new input. Error messages should contain the types of errors (Type Error, Value Error, Index Error, etc.). Each bigram should have the format Head: [head] Tail: [tail] and should be printed in a new line.
    - You should only print the output of the current stage and not the previous one, but like in the previous stage, the name of the file that contains the corpus should be given as user input.

- Stage 3/6: Create a Markov chain model

  - Theory

    - We already mentioned Markov chains a few times. A Markov chain is a statistical model in which the probability of each event depends on the previous event. It can be described as a set of states and transitions between them. Each transition has a probability that is determined by some kind of statistical data. In this project, a state corresponds to a token, and each transition represents going from one word of a sentence to another. The probability of transitions is calculated from the bigrams we collected in the previous stage. The basic idea of this project is that from a dictionary we can create a model that will consider all the possible transitions from one word to another and choose the most probable one based on the previous word.

  - Description

    - This is the final step where we will work on creating a Markov chain model. We will use the data prepared in the first two stages and transform it into a model. This model will contain probabilistic information that will tell us what the next word in a chain might be.

    - We already have a list of all bigrams from the corpus. As we discussed earlier, this can already be used to make some naive predictions. There is a problem, though: right now our data contains a lot of repetition. As we have seen at the first stage, the total number of tokens is almost 10 times greater than the number of unique tokens. This ratio must be about the same in the list of bigrams. Some bigrams might be very common, others — relatively rare. At the moment, we have no way of telling which are which.

    - To resolve this problem, we will make a simplified version of a Markov chain model.

  - Objectives

    - The data should be reorganized in such a way that every head is repeated only once, and all the possible tails can be directly accessed by querying that head. For example: head — good, tails — night, bye, bye, night, to, to, bye, boy. As you can see, there are still some repetitions among the tails.
    - Instead of repeating tails every time they occur, each tail should appear only once and the number of repetitions should be stored as an integer. For example, the previous example should look like this: head — good, tails — night: 2, bye: 3, to: 2, boy: 1.
    - You can see that the data is more readable after this transformation!
    - Besides creating the model, we should also check that it works correctly. To test it, let's take a string as user input and print all the possible tails and their corresponding counts. If the model does not contain the specified head print the following error message Key Error. The requested word is not in the model. Please input another word. and ask for another until it is valid. Repeat until the string exit is input.

    - You should only print the output of the current stage and not the previous one, but like in the previous stage, the name of the file that contains the corpus should be given as user input.

- Stage 4/6: Generate random text

  - Theory

    - We suggest using the method random.choices() to select the most probable tail from the list of possible tails based on the corresponding repetition counts. This method is similar to random.choice() with the exception that it also considers user-specified weights during the process. The method takes four arguments: population, weights, cum_weights, and k. For this project, we only care about the first two arguments: population, which is a list of elements to choose from, and weights, which is a list of relative weights that correspond to the elements of the population. Since the other two arguments have sensible default values, we don't necessarily have to specify them.

  - Description

    - We have our model, fantastic! What's next? Well, the model can already be used to predict the next word in a chain by feeding it any head (of a bigram) from the corpus and retrieving the most probable tail from the corresponding entry. But how do we start the chain, what should be the first word?

    - Of course, we could choose a word manually, but this is an error-prone solution because we might take a word that is not in the corpus. A better way to start is to choose a random word from the corpus and feed it to the model so that it predicts the next word.
    - After the next word is acquired, it should be used to predict the following word, and so on, thus continuing the chain.

  - Objectives

    - Choose a random word from the corpus that will serve as the first word of the chain.
    - The second word should be predicted by looking up the first word of the chain in the model and choosing the most probable next word from the set of possible follow-ups. Right now, an entry contains all the possible tails that might follow the selected head along with their corresponding repetition counts. Using the repetition counts, you will be able to choose the most probable option.
    - The second step should be repeated until the length of the chain is 10 words, but this time, the current last word of the chain should be used to look up another probable word to continue the sentence.
    - Using the algorithm described above, generate chains consisting of 10 tokens, join the resulting tokens together, and print them as a pseudo-sentence. Keep in mind that a pseudo-sentence can consist of multiple actual sentences, so having punctuation marks inside pseudo-sentences is completely valid.

    - Generate and print 10 sentences like that. Keep in mind that every generated pseudo-sentence should be on a new line.

    - You should only print the output of the current stage and not the previous one. The name of the file that contains the corpus should be given as a command line input.

- Stage 5/6: Generate full sentences

  - Description

    - As you can see, the algorithm is now capable of generating pseudo-random text based on Markov chains. The problem is that the resulting text does not resemble real sentences at all. First, the resulting text is always ten tokens long. Second, it does not always start with capital letters. Third, it usually does not even end with correct punctuation such as periods, exclamation marks, or question marks.

    - Luckily, by identifying the problem, a good programmer can always find ways to resolve it.

  - Objectives

    - Make the algorithm more realistic by generating pseudo-sentences instead of just random text.
    - The sentences that are being generated should:
      - always start with capitalized words ("This is beautiful.", "You are a great programmer!", etc.);
      - not start with a word that ends with a sentence-ending punctuation mark ("Okay.", "Nice.", "Good.", "Look!", "Jon!", etc.);
      - always end with a sentence-ending punctuation mark like ., !, or ?;
      - should not be shorter than 5 tokens.
    - Generate and print exactly 10 pseudo-sentences that meet these criteria. A pseudo-sentence should end when the first sentence-ending punctuation mark is encountered after the minimal sentence length (5 tokens) is reached.
    - Note that every generated pseudo-sentence should be on a new line.

    - You should only print the output of the current stage and not the previous one. The name of the file that contains the corpus should be given as user input.

- Stage 6/6: Generate sentences based on trigrams

  - Description

    - The generated text finally looks like actual sentences! It's a great step in the right direction, but do they actually make sense? Unfortunately, the algorithm most likely generates gibberish that can hardly be called a product of an artificial "intelligence". This happens because the algorithm considers nothing but the preceding word when trying to predict the next one in the chain. It basically works like a person who forgets the beginning of their sentence while speaking and pronounces the first probable word that comes into their mind without really connecting it to the original idea of the sentence.

    - To improve the quality of the generated sentences, we need to take into account the longer bits of the preceding text. This is not an easy task!

  - Objectives

    - Right now, the model is based on bigrams, that is, we only consider one word when trying to predict the next word in the chain.

    - The algorithm should be extended so that it can use not only bigrams but also trigrams. We have already talked about trigrams in Stage 2. They are very similar to bigrams, the only difference being their length: trigrams consist of three tokens instead of just two. In the case of trigrams, every head should consist of two tokens. Tails should stay the same length as before since we are still aiming to predict the next word in the chain.

    - This change implies the following tasks:

      - The list of bigrams should be transformed into a list of trigrams. It should still consist of heads and tails, but now, heads should consist of two space-separated tokens concatenated into a single string. The tails should still consist of one token. For example: head — winter is, tail — coming.
      - The model should be trained based on the list of trigrams. The model creation requires no modifications since trigrams still consist of a head and a tail.
      - The beginning of the chain should be a randomly chosen head from the model, not just any word from the corpus.
      - When predicting the next word, the model should be fed the concatenation of the last two tokens of the chain separated by a space.
      - After making all these modifications, the output should look rather similar to the result of the previous stage, but now the generated pseudo-sentences should make a little more sense.

      - Keep in mind that every generated pseudo-sentence should be in a new line.

      - You should only print the output of the current stage and not the previous one. The name of the file that contains the corpus should be given as user input.
