# Contents based Recommendation
: recommend 'similar' products compared to previous bought items

### Reprecsented Items : item into vector (e.g, BERT, word count)
* how to compute vector similarity?
  * Euclidan similarity : \frac{1}{euclidian distance epsilon} where epsilon \approx 1e-05
    * (pros): easy to compute
    * (cons): different distributions of p,q or different range(+scale) --> lost correlation
  * cosine similarity --> \theta! similar direction
    * (pros): 벡터의 크기가 중요하지 않은 경우에 거리를 측정하기 위한 메트릭으로 사용. (예 : 문서내에서 단어의 빈도수 - 문서들의 길이가 고르지 않더라도 문서내에서 얼마나 나왔는지라는 비율를 확인하기 때문에 상관없음. )
    * (cons): no work when vector magitude is important
  * pearson similarity : correlation, similarity among documents
  * Jacard similarity : union in the set

### how to vectorize?
  * TF-IDF: ***특정 문서 내에 특정 단어가 얼마나 자주 등장하는 지를 의미하는 단어 빈도(TF)*** 와 ***전체 문서에서 특정 단어가 얼마나 자주*** 등장하는지를 의미하는 역문서 빈도(DF)를 통해서 “다른 문서에서는 등장하지 않지만 특정 문서에서만 자주 등장하는 단어"를 찾아서 문서 내 단어의 가중치를 계산하는 방법입니다.
용도로는 문서의 핵심어를 추출, 문서들 사이의 유사도를 계산, 검색 결과의 중요도를 정하는 작업등에 활용할 수 있습니다.
  * 빈도수를 기반으로 많이 나오는 중요한 단어들을 잡아준다. 이러한 방법을 Counter Vectorizer --> 조사/관사에 penalty
    * (pros): intuitive
    * (cons): memory issue when handdling big corpus; sparse matrix
  * Word2Vec
    * 
