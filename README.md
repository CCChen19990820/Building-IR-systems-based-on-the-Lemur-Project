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


3.now run the VectorSpace.py 

4.KAPI TF-IDF on query 401
We ran the okapi tf-idf model on query "401. foreign minorities, germany" for the WT2g collection (with stemming), without doing any fancy query processing (just word tokenization). Below you can find some of the statistics I got back by running trec-eval on the results for this query:

Queryid (Num):      401
Total number of documents over all queries
    Retrieved:     1000
    Relevant:        45
    Rel_ret:         42
Interpolated Recall - Precision Averages:
    at 0.00       1.0000
    at 0.10       0.4375
    at 0.20       0.3250
    at 0.30       0.3182
    at 0.40       0.2769
    at 0.50       0.2604
    at 0.60       0.2366
    at 0.70       0.2361
    at 0.80       0.2209
    at 0.90       0.0586
    at 1.00       0.0000
Average precision (non-interpolated) for all rel docs(averaged over queries)
                  0.2605
Precision:
  At    5 docs:   0.4000
  At   10 docs:   0.4000
  At   15 docs:   0.4000
  At   20 docs:   0.3500
  At   30 docs:   0.3000
  At  100 docs:   0.2500
  At  200 docs:   0.1850
  At  500 docs:   0.0800
  At 1000 docs:   0.0420
R-Precision (precision after R (= num_rel for a query) docs retrieved):
    Exact:        0.3111

We ran the language model with Laplace smoothing "401. foreign minorities, germany" for the WT2g collection (with stemming), without doing any fancy query processing (just word tokenization). Below you can find some of the statistics I got back by running trec-eval on the results for this query:

Queryid (Num):      401
Total number of documents over all queries
    Retrieved:     1000
    Relevant:        45
    Rel_ret:         35
Interpolated Recall - Precision Averages:
    at 0.00       0.3333
    at 0.10       0.3333
    at 0.20       0.3333
    at 0.30       0.2969
    at 0.40       0.2969
    at 0.50       0.2738
    at 0.60       0.2547
    at 0.70       0.0790
    at 0.80       0.0000
    at 0.90       0.0000
    at 1.00       0.0000
Average precision (non-interpolated) for all rel docs(averaged over queries)
                  0.1818
Precision:
  At    5 docs:   0.2000
  At   10 docs:   0.1000
  At   15 docs:   0.1333
  At   20 docs:   0.3000
  At   30 docs:   0.3333
  At  100 docs:   0.2500
  At  200 docs:   0.1450
  At  500 docs:   0.0660
  At 1000 docs:   0.0350
R-Precision (precision after R (= num_rel for a query) docs retrieved):
    Exact:        0.2889
    
We ran the language model with Jelinek-Mercer smoothing "401. foreign minorities, germany" for the WT2g collection (with stemming), without doing any fancy query processing (just word tokenization). Below you can find some of the statistics I got back by running trec-eval on the results for this query:

Queryid (Num):      401
Total number of documents over all queries
    Retrieved:     1000
    Relevant:        45
    Rel_ret:         39
Interpolated Recall - Precision Averages:
    at 0.00       0.2000
    at 0.10       0.0795
    at 0.20       0.0683
    at 0.30       0.0677
    at 0.40       0.0633
    at 0.50       0.0562
    at 0.60       0.0562
    at 0.70       0.0514
    at 0.80       0.0514
    at 0.90       0.0000
    at 1.00       0.0000
Average precision (non-interpolated) for all rel docs(averaged over queries)
                  0.0561
Precision:
  At    5 docs:   0.2000
  At   10 docs:   0.1000
  At   15 docs:   0.0667
  At   20 docs:   0.1000
  At   30 docs:   0.0667
  At  100 docs:   0.0700
  At  200 docs:   0.0600
  At  500 docs:   0.0520
  At 1000 docs:   0.0390
R-Precision (precision after R (= num_rel for a query) docs retrieved):
    Exact:        0.0889
If you correctly run the code, you'll see the answer above.

5.Have a nice day.
