# Information Retrieval System - lnc.ltc Scoring: Project Overview:
* Created an IR system that implements the lnc.ltc scoring mechanism to rank the documents based on the query
* Transformed the system to implement the Inverted Index representation, to decrease the amount of space taken by the system data struture.
* Clustered the documents using KNN clustering algorithm, to improve the time taken by the system to return results.

---
### Code and Resources Used:
**Python Version:** 3.7.6\
**Packages:** Pandas, Numpy, Sklearn\
**Dataset:** A partially processed form of english wikipedia available at https://en.wikipedia.org/wiki/Wikipedia:Database_download \
**To Install Dependencies:** `pip install -r requirements.txt`

---
### Vector Space Model:
After cleaning up the dataset, the file was read to represent each document as a vector of **|V|** dimensions, where **V** is the vocabulary set, or the set of all terms present in the corpus. The document vectors were storted in a matrix, with the columns as the documents and the rows as the terms. After filling up the matrix, it was observed that **99.86%** of the cells were empty, hence indiacting a lot of empty space.

#### Computing the lnc for documents:
![equation](https://latex.codecogs.com/gif.latex?Logarithm%5C%20term%5C%20frequency%20%5Cleft%28%20l%20%5Cright%29%3A%201%20&plus;%20%5Clog_%7B2%7D%5Cleft%20%28%20tf_%7Bt%2Cd%7D%20%5Cright%20%29)
![equation](https://latex.codecogs.com/gif.latex?No%5C%20document%5C%20frequency%20%5Cleft%28%20n%20%5Cright%29%3A%201)
![equation](https://latex.codecogs.com/gif.latex?Cosine%5C%20normalisation%20%5Cleft%28%20c%20%5Cright%29%3A%20%5Csqrt%7B%20%5Csum%5Climits_%7Bi%3D1%7D%5E%7BT%7D%20%7Bw%5E%7B2%7D_%7Bi%7D%7D%7D)

#### Computing the ltc for query:
![equation](https://latex.codecogs.com/gif.latex?Logarithm%5C%20term%5C%20frequency%20%5Cleft%28%20l%20%5Cright%29%3A%201%20&plus;%20%5Clog_%7B2%7D%5Cleft%20%28%20tf_%7Bt%2Cd%7D%20%5Cright%20%29)
![equation](https://latex.codecogs.com/gif.latex?Inverse%5C%20document%5C%20frequency%20%5Cleft%28%20n%20%5Cright%29%3A%20%5Clog_%7B2%7D%5Cleft%28%5Cfrac%7BN&plus;1%7D%7Bdf_%7Bt%7D%7D%20%5Cright%29)
![equation](https://latex.codecogs.com/gif.latex?Cosine%5C%20normalisation%20%5Cleft%28%20c%20%5Cright%29%3A%20%5Csqrt%7B%20%5Csum%5Climits_%7Bi%3D1%7D%5E%7BT%7D%20%7Bw%5E%7B2%7D_%7Bi%7D%7D%7D)

#### Finding Scores:
The dot product of each of the document vector with query vector gave the individual document score. The top 10 document with highest scores were then returned.

#### Results:
##### Time taken:
The average time taken to return the results for a corpus of **6000 documents** was observed to be **0.96 seconds**
##### Space Taken:
The amount of space taken to represent the **10 MB** of dataset into the system data structre was **900 MB**

---
