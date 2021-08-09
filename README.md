# IR-systems-based-on-the-Lemur-Project

1.Please download the WT2g data collection for this project (Don't distribute it!!!).

2.this project is to implement several different retrieval methods, i.e. algorithms that given a user's request (query) and a corpus of documents assign a score to each document according to its relevance to the query.There are four kind of ranking method, as follow:

(1)Vector space model, terms weighted by Okapi TF (see note) times an IDF value, and inner product similarity between vectors.

Note: You will have to use for the weights OKAPI TF x IDF where OKAPI TF = tf/(tf + 0.5 + 1.5 * doclen / avgdoclen). For queries, Okapi TF can also be computed in the same way, just use the length of the query to replace doclen.
Also note that the definition of OKAPI TF is tf / tf + k1((1 - b) + b * doclen / avgdoclen). In the above formula, you can set k1 = 2 and b = 0.75, to end up with: tf / (tf + 0.5 + 1.5 * doclen / avgdoclen).

(2)Language modeling, maximum likelihood estimates with Laplace smoothing only, query likelihood.

Note: If you use multinomial model, for every document, only the probabilities associated with terms in the query must be estimated because the others are missing from the query-likelihood formula (please refer to our slides).
For model estimation use maximum-likelihood and Laplace smoothing. Use formula (for term i)

where m = term frequency, n=number of terms in document (doc length) , k=number of unique terms in corpus.

(3)Language modeling, Jelinek-Mercer smoothing using the corpus, 0.8 of the weight attached to the background probability, query likelihood.

The formula for Jelinek-Mercer smoothing is,


where P is the estimated probability from document (max likelihood = m_i/n) and Q is the estimated probability from corpus (background probability = cf / terms in the corpus).

(4)Implement any of your ideas to improve one of the above three IR models.
You have to do something that can really improve the rank quality of the chosen IR models, and explain and showcase why your modifications can work.


3.Run VectorSpace.py 
