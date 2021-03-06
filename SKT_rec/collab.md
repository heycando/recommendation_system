# Collaborative Filtering
 : 협업필터링은 사용자의 구매 패턴이나 평점을 가지고 다른 사람들의 구매 패턴, 평점을 통해서 추천을 하는 방법; 나에 대한 추천을 위해 내가 평점 준 타 사용자들과 비슷한 사용자들 평가 정보 사용

## Neighborhood based method(KNN)
  * User-based collaborative filtering : 사용자의 구매 패턴(평점)과 유사한 사용자를 찾아서 추천 리스트 생성
    * 유저끼리의 average 점수 평균이 다를 수 있음 -> 적절한 bias 제거 (user 끼리 유사도 측정)
  * Item based collaborative filtering : 특정사용자가준점수간의유사한상품을찾아서추천리스트생성 ( ? contents based랑은 무슨 차이지?)
    * (item 끼리 유사도 측정)
  * (pros) Simple, iterpretation based on item, stable with new items
  * (cons) time/speed/memory requires, 희소성!(Top-K); 아무도 특정 item에 대해 평가하지 않으면 그 아이템에 대한 평가 불가 --> contents based 필요
 
 ## Latent factor collaborative filtering
  * Rating matrix 빈공간 채우기 위해 Latent factor 추론 --> 2가지 행렬 도입
    * user (latent) matrix / item (latent) matrix 곱을 통해 평점 복원 가능
  * SVD : 사용자의 잠재요인과 아이템의 잠재요인을 내적해서 평점 매트릭스를 계산
    * Observed Only MF; weighted MF; SVD
    * ( cons) 결측치가 없어야함
  * SGD : U와 V에 대해 편미분 하고 그 값이 rating matrix와의 차이를 줄일 수 있도록 L2 regularization penalty 줘서 weight matrix 학습! 동시에!
    * row 일반적으로 20 사용?
    * algorithm
      * 초반 U,V를 각각 곱해서 init,
      * U와 V엥 대해 순서대로 partial derivative 값 구해서 업데이트 ( 결측치를 제외하고 )
      * ***update jointly!***
    * (pros) various loss function; parallelizable
    * (cons) slow convergence (but depends on the model)
  * ALS : 하나의 Latent는 고정 
    * Because one is fixed and update alternatively, the other one always become convex; convergence guaranteed
    * 물음표는 0으로,
    * 풀어냈을 때의 값은 최적화 solution으로 analytical하게 정의되어 있어서 대입하면 되어버림

* (pros) no domain knowledge; easy to find new interests; implicit data
* (cons) hard to handle new items(clients) --> need to learn again; hard to integrate side features 
