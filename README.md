# kakao-arena
playlist's songs and tags recommendation 
## << 다은이의 첫 공모전 카카오 아레나 >>  
[ 2020.04.30 ~ 2020.07.26 ]   
### < 이번 공모전에서 성장한 점 >  
1. 추천시스템을 하나도 몰랐는데 3달 남짓동안 추천시스템 전반에 대해 이해할 수 있었다. 엄청 성장했다!
2. 특히 cf에서 클러스터링 기법(KNN 등)을 통해 모델 성능의 향상을 경험했다.
3. re-ranking과 denoising의 중요성을 매우 인지하고있어서 마지막에 특히 reranking에 초점을 맞춰 여러 방법을 시도했다.
나는 완전 실험맨이었다....   

<여러 실험 내역>   
1) xgboost rank:pairwise, 점수 count 앙상블로 여러 result의 reranking시도  
> but xgboost ranking 알고리즘은 단기간에 이해하기 어려웠다;;; x,y에 대체 뭘 넣는지 감조차 오지 않았다... 미래의 내가 시도해줬으면
> count 앙상블을 전날까지 시도했는데 성능이 조금 올랐지만, 최고성능 앙상블에는 떨어졌다 ... 조금만 더 일찍 시도했다면...  
2) denoising을 위해 plylst에서 10번 이상 등장한 song만 추천에 이용
> minor한 곡들이 생각보다 많이 등장해서그런가 성능 떨어짐
3) minor한 곡들을 잡기위해 cosine similarity에 inverse coefficient를 곱하는 작업으로 minor한 애들의 가중치를 높임(논문참고)
> 음... 별로
4) cosine similarity 정규화(논문 min_max 공식에서 착안해서 모든 각 cosine similatity에 max값으로 나눴음)
> 음....... 이것도 딱히?

그래도 이것저것 시도도 해보고 나름 코드도 짜보고 오빠들이랑 친해지고 매우 즐거운 시간이었다

