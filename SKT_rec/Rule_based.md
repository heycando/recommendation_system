# Recommendation_system
Based on SKT program @210212

## Main Abstraction of Recomendation system
* Association Analysis
  * Rule based; association between products;
  * "How frequently bought together?
  * correlcation between products
  * Metric
    * support(그냥 확률?)
    * life(독립성)
    * confidence(conditional)
  * Exponentially increasing according to the number of items --> Apriori Algorithm
### Apriori Algorithm
  * Implicit Feedback Data ( the algorithm has seen, not sure whether the consumer likes it or not, but anyway recommends..)
  * algorithm
    * generate one-item frequent set
    * compute support
    * select(filter out below the support value)
    * from the selected one, group 2 item frequent set ex) {a,b}, {a,c} ,{b,c} in {a,b,c}
    * repeat
  * (pros) easy&understandable(oppisite to black-box recommendation), meaninggful buying pattern 
  * (cons) huge computation / correlation doesn't mean causality
 ```
 from mlxtend.frequent_patterns import apriori
 df = pd.DataFreame('data_ary', columns="")
 apriori(df, min_support=0.5)
 ```
 ### FP-Growth
  * to overcome computation burdenness in Apriori algorithm
  * algorithm
    * generate one-item frequent set
    * ***sort out by more frequent items in the set in descent manner***
    * ***make a tree;
      * if new item, start from the parent; otherwiese expands from the existing nodes.
    * compute from the lowest priori, and generate conditional pattern ( reference example in ppt)
    * repeat
    
## What about cold-start? (new clients)
