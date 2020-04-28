## Getting Started
This blog will solve all your doubts regarding this algo
1. https://medium.com/@pratikbarhate/latent-dirichlet-allocation-for-beginners-a-high-level-intuition-23f8a5cbad71


https://blog.echen.me/2011/08/22/introduction-to-latent-dirichlet-allocation/

Sample documents are (each line represents a document):
I like to eat broccoli and bananas.
I ate a banana and spinach smoothie for breakfast.
Chinchillas and kittens are cute.
My sister adopted a kitten yesterday.
Look at this cute hamster munching on a piece of broccoli.
Suppose we choose k=2 (number of topics are 2) for our model:
Topic A: 30% broccoli, 15% bananas, 10% breakfast, 10% munching, …… (we could interpret topic A to be about food)
Topic B: 20% chinchillas, 20% kittens, 20% cute, 15% hamster, ……… (we could interpret topic B to be about cute animals)
Now some new document can be tagged with the above-given topics using the observations made by the LDA model.
Banana and spinach smoothie is a good combination for a healthy breakfast.
Kittens look cute as they munch on a bowl of milk, bananas, and chocolates.
Here, we can say that sentence 1 is 100% Topic A and sentence 2 is 40% Topic B with 60% Topic A.



To use a topic modeling technique, you need to provide (1) a document-term matrix and (2) the number of topics you would like the algorithm to pick up.

Once the topic modeling technique is applied, your job as a human is to interpret the results and see if the mix of words in each topic make sense. If they don't make sense, you can try changing up the number of topics, the terms in the document-term matrix, model parameters, or even try a different model.

LDA is a probabilistic method. For each document the results give us a mix of topics that make up that document. To be precise, we get a probability distribution over the k topics for each document. Each word in the document is attributed to a particular topic with probability given by this distribution.


The model is Bayesian, and doesn’t admit zero probabilities either for the topic distributions or for the word distributions. This means that in every document each topic has a non-zero probability, and in every topic each word in the vocabulary has a non-zero probability. However, these probabilities can be vanishingly small. Indeed, the model is set up so as to try and encourage most of the probabilities to be very close to zero: we want results that suggest each document is made up a small number of topics, and each topic is primarily composed of a small number of main words.


Alpha parameter is Dirichlet prior concentration parameter that represents document-topic density — with a higher alpha, documents are assumed to be made up of more topics and result in more specific topic distribution per document.
Beta parameter is the same prior concentration parameter that represents topic-word density — with high beta, topics are assumed to made of up most of the words and result in a more specific word distribution per topic.
