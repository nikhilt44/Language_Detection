# Language_Detection
Language Detection using N-grams

An n-gram is a contiguous sequence of n items from a given sequence of text or speech. It is an N-character slice of a longer string. Typically, the string is sliced into a set of overlapping N-grams.

Given a novel document to be classified, the system computes the N-gram profile of this document (document profile) and compares the distance between this document profile and the language profiles for all the supported languages. The language profile is basically the top N of the list of bi-grams and tri-grams sorted by frequency. The top 300 or so N-grams are almost always highly correlated to the language. Thus, the language profile of a sporty document will be very similar to the language profile generated from a political document in the same language. This gives us confidence that if we train the system on the Declaration of Human Right we will still be able to classify documents to the correct language even though they might have completely different topics. Starting at around rank 300 or so, an N-gram frequency profile begins to become specific to the topic. For the training and testing we took the data from European Parliament Proceeding Parallel Corpus. The dataset contains text data for 21 european languages.

Given below are the top 50 most frequent combination of bigrams and trigrams for english language that we found from the training corpus.

[of the, in the, to the, the european, on the, it is, the commission, that the, and the, for the, to be, ' s, with the, by the, european union, we are, like to, the european union, that we, is a, we have, member states, the council, in this, this is, i would, at the, is the, will be, is not, of this, i am, from the, there is, that is, of a, has been, of the european, which is, as a, would like, must be, do not, have been, we must, and i, should be, would like to, that it, european parliament]

To reduce the computation we computed the language profile for each language and serialized each one of them. Then, while testing we directly used them after deserializing. For preprocessing the text, tokenization etc. we used the Stanford CoreNlp library .

You can find the full Java code on the Github page. Feel free to use your choice of parameters for generating the language profiles. Awesome, if you could increase the accuracy!!!!.

The N-grams approach achieved an average accuracy of ~89% for the test set. It was observed that our prediction model misclassified appreciable amount of sentences for which the length was less. It couldn't find a match in the language profile and made a mistake. Including the unigrams in the language profile too may help in correctly classifying even the short sentences in the data. Furthermore tuning the hyperparameters on a validation set may further bring an improvement in the accuracy.
