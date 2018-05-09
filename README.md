# Sequence-Models---Operations-on-word-vectors---Debiasing

Welcome to our first assignment of this week!

Because word embeddings are very computionally expensive to train, most ML practitioners will load a pre-trained set of embeddings.

After this assignment we will be able to:

Load pre-trained word vectors, and measure similarity using cosine similarity
Use word embeddings to solve word analogy problems such as Man is to Woman as King is to __.
Modify word embeddings to reduce their gender bias
Let's get started! Run the following cell to load the packages we will need. (refer wv.py [ln 1])

Next, lets load the word vectors. For this assignment, we will use 50-dimensional GloVe vectors to represent words. Run the following cell to load the word_to_vec_map.(refer wv.py[ln 2])

You've loaded:

words: set of words in the vocabulary.
word_to_vec_map: dictionary mapping words to their GloVe vector representation.
You've seen that one-hot vectors do not do a good job cpaturing what words are similar. GloVe vectors provide much more useful information about the meaning of individual words. Lets now see how you can use GloVe vectors to decide how similar two words are.

1 - Cosine similarity
To measure how similar two words are, we need a way to measure the degree of similarity between two embedding vectors for the two words. Given two vectors  u  and  v , cosine similarity is defined as follows:

CosineSimilarity(u, v)=u.v/||u||2||v||2=cos(θ)
 
where  u.v  is the dot product (or inner product) of two vectors,  ||u||2  is the norm (or length) of the vector  u , and  θ  is the angle between  u  and  v . This similarity depends on the angle between  u  and  v . If  u  and  v  are very similar, their cosine similarity will be close to 1; if they are dissimilar, the cosine similarity will take a smaller value.

(see images)
Figure 1: The cosine of the angle between two vectors is a measure of how similar they are

Exercise: Implement the function cosine_similarity() to evaluate similarity between word vectors.

Reminder: The norm of  uu  is defined as  ||u||2=√∑ni=1u2i

(refer wv.py[1n 3])

Expected Output:

cosine_similarity(father, mother) =	0.890903844289
cosine_similarity(ball, crocodile) =	0.274392462614
cosine_similarity(france - paris, rome - italy) =	-0.675147930817
After you get the correct expected output, please feel free to modify the inputs and measure the cosine similarity between other pairs of words! Playing around the cosine similarity of other inputs will give you a better sense of how word vectors behave.

2 - Word analogy task
In the word analogy task, we complete the sentence "a is to b as c is to __". An example is 'man is to woman as king is to queen' . In detail, we are trying to find a word d, such that the associated word vectors  ea,eb,ec,ed  are related in the following manner:  eb−ea≈ed−ec . We will measure the similarity between  eb−ea  and  ed−ec  using cosine similarity.

Exercise: Complete the code below to be able to perform word analogies! (refer wv.py [ln 4])

Run the cell below to test your code, this may take 1-2 minutes. (refer wv.py [ln 5])

Expected Output:

italy -> italian ::	spain -> spanish
india -> delhi ::	japan -> tokyo
man -> woman ::	boy -> girl
small -> smaller ::	large -> larger
Once you get the correct expected output, please feel free to modify the input cells above to test your own analogies. Try to find some other analogy pairs that do work, but also find some where the algorithm doesn't give the right answer: For example, you can try small->smaller as big->?.

Congratulations!
We've come to the end of this assignment. Here are the main points you should remember:

Cosine similarity a good way to compare similarity between pairs of word vectors. (Though L2 distance works too.)
For NLP applications, using a pre-trained set of word vectors from the internet is often a good way to get started.



