
# Kakao Arena(2020)

##  Melon Playlist Continuation

https://arena.kakao.com/c/7
|기간|대회내용|결과|
|------|-----------|---|
|20.04.30 ~20.07.26|플레이리스트에 숨겨진 노래와 태그를 예측|**TOP 2%**|

----------------------------------

## 📌 Technique 
#### Recommender System 


## 📌 주요 인사이트 

### 1) KNN + CF
![image](https://user-images.githubusercontent.com/62705839/115150786-e0b57080-a0a4-11eb-99ac-542994ca45b5.png)

- Song의 개수가 70만개로 너무 크고, Item 기반 추천알고리즘은 매우 Sparse한 결과와 Memory Error를 낳았음 (RAM 20GB 사용시)
- 따라서 CF 진행 전 Clustering을 **KNN**으로 진행하고, 이 후 CF를 적용하여 **각 Active user와 유사한 song_id를 출력**함 (유사도는 cosine 사용)
- **If-Else**로 Song만 있는 경우, Tag만 있는 경우, 둘 다 있/없는 경우를 나누어 모델링
- 이 후 대회 마지막 과정에서 다양한 K를 설정하여 그 결과를 **앙상블**


### 2) Side infomation
- 플레이리스트의 제목, 발매 일자, 가수명, 앨범이름, 장르 등의 song_meta data에 있는 song의 side information을 자유롭게 CF에 첨가함
- 특히 제목은 Sentencepiece를 이용해 벡터화하였음
- 이들의 정보를 담은 Sind-info 행렬을 만들고 모두 곱하여 최종 추천에 이용함

