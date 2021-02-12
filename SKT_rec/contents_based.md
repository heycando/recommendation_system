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
    * to overcome following limitation;
     * memory issue; no use of mini-batch, parallelization using gpu; hard to improve learning pipeline
    * 추론 : 주변 단어(맥락)이 주어졌을 때 “?”에 무슨 단어(중심단어)가 들어가는지를 추측하는 작업
    * Word2Vec은 “비슷한 위치에 등장하는 단어들은 비슷한 의미를 가진다“ 라는 가정을 통해서 학습을 진행합니다
     * 원-핫벡터 형태의 sparse matrix 이 가지는 단점을 해소하고자 저차원의 공간에 벡터로 매핑하는 것이 특징
    * CBOW: inferencing the middie word using neighborhood
    * Skip-gram: inferencing neighbor words using the middle words
   
 * (pros) cold start에 좋을 수 있고(feature 들어오면 embedding 시켜서 유사도 계산하면 됨으로) ; 설명 용이
 * (cons) metadata가 없으면 잘 안되는 경우 존재 --> feature 추출에 대한 중요성
