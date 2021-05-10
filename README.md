# Information Retrieval System - lnc.ltc Scoring: Project Overview:
* Created an IR system that implements the lnc.ltc scoring mechanism to rank the documents based on the query
* Transformed the system to implement the Inverted Index representation, to decrease the amount of space taken by the system data struture.
* Clustered the documents using KNN clustering algorithm, to improve the time taken by the system to return results.

---
### Code and Resources Used:
**Python Version:** 3.7.6\
**Packages:** Pandas, Numpy, Sklearn\
**Dataset:** A partially processed form of english wikipedia available at https://en.wikipedia.org/wiki/Wikipedia:Database_download\
**To Install Dependencies:** `pip install -r requirements.txt`

---
### Vector Space Model:
After cleaning up the dataset, the file was read to represent each document as a vector of $\left| V \right|$ dimensions, where $ V $ is the vocabulary set, or the set of all terms present in the corpus. The document vectors were storted in a matrix, with the columns as the documents and the rows as the terms. After filling up the matrix, it was observed that **99.86%** of the cells were empty, hence indiacting a lot of empty space.

#### Computing the lnc for documents:

$$ Logarithm\ term\ frequency \left( l \right): 1 + \log_{2}\left ( tf_{t,d} \right ) $$  

$$ No\ document\ frequency \left( n \right): 1 $$  

$$ Cosine\ normalisation \left( c \right): \sqrt{ \sum\limits_{i=1}^{T} {w^{2}_{i}}} $$  

#### Computing the ltc for query:

$$ Logarithm\ term\ frequency \left( l \right): 1 + \log_{2}\left ( tf_{t,d} \right ) $$ 

$$ Inverse\ document\ frequency \left( n \right): \log_{2}\left(\frac{N+1}{df_{t}} \right) $$   

$$ Cosine\ normalisation \left( c \right): \sqrt{ \sum\limits_{i=1}^{T} {w^{2}_{i}}} $$  

#### Finding Scores:
The dot product of each of the document vector with query vector gave the individual document score. The top 10 document with highest scores were then returned.

#### Results:
##### Time taken:
The average time taken to return the results for a corpus of 6000 documents was observed to be **0.96 seconds**
##### Space Taken:
The amount of space taken to represent the **10 MB** of dataset into the system data structre was **900 MB**


