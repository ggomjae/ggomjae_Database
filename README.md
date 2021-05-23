DATABASE 🐻
============ 

GGOMJAE
------
* Author 민경재[ggomjae] <br>
* 개인 개발 블로그 2 링크 <https://velog.io/@ggomjae> <br>
* 개인 개발 블로그 및 일상 링크 <https://blog.naver.com/ggomjae> <br>

계획
-------
* 데이터베이스 기술 모음 저장소 [ 개발블로그에 링크 및 README에 정리를 할 계획 ]
* 공부하는 책 목록 : real mysql, 친절한 sql 튜닝, MySQL 퍼포먼스 최적화, SQL 코딩의 기술
-------


### 개발 [블로그](https://velog.io/@ggomjae) 정리 모음

#### velog
* [2021-04-04] MySQL TimeZone 설정 - serverTimezone=Asia/Seoul 로 수정할 때 [BLOG에 정리한 부분](https://velog.io/@ggomjae/MySQL-TimeZone-%EC%84%A4%EC%A0%95-serverTimezoneAsiaSeoul-%EB%A1%9C-%EC%88%98%EC%A0%95%ED%95%A0-%EB%95%8C)
* [2021-04-04] Mysql Query Between 과 >=, <= 성능 차이 비교 ( 더미데이터 50만 ) [BLOG에 정리한 부분](https://velog.io/@ggomjae/Mysql-Query-Between-%EA%B3%BC-%EC%84%B1%EB%8A%A5-%EC%B0%A8%EC%9D%B4-%EB%B9%84%EA%B5%90-%EB%8D%94%EB%AF%B8%EB%8D%B0%EC%9D%B4%ED%84%B0-50%EB%A7%8C)
* [2021-04-10] Cluster Index vs Non-Cluster Index 이론 및 성능 비교 ( JPA + MYSQL ) [BLOG에 정리한 부분](https://velog.io/@ggomjae/Cluster-Index-vs-Non-Cluster-Index-%EC%84%B1%EB%8A%A5-%EB%B9%84%EA%B5%90-%EB%B0%8F-%EC%9D%B4%EB%A1%A0)
* [2021-05-18] MySQL의 데이터 흐름 및 특징 - 답이 아닌 책을 읽으면서 나의 머리에 있는 흐름을 정리한 글 [BLOG에 정리한 부분](https://velog.io/@ggomjae/MySQL%EC%9D%98-%ED%8A%B9%EC%A7%95)
* [2021-05-20] 쿼리 성능 진단은 최적화의 기초 [BLOG에 정리한 부분](https://velog.io/@ggomjae/%EC%BF%BC%EB%A6%AC-%EC%84%B1%EB%8A%A5-%EC%A7%84%EB%8B%A8%EC%9D%80-%EC%B5%9C%EC%A0%81%ED%99%94%EC%9D%98-%EA%B8%B0%EC%B4%88)
* [2021-05-22] where 조건 이해 [BLOG에 정리한 부분](https://velog.io/@ggomjae/Where-%EC%A1%B0%EA%B1%B4-%EC%9D%B4%ED%95%B4)
* [2021-05-23] 스토리지 엔진 레벨에서의 접근법(https://velog.io/@ggomjae/%EC%8A%A4%ED%86%A0%EB%A6%AC%EC%A7%80-%EC%97%94%EC%A7%84-%EB%A0%88%EB%B2%A8%EC%97%90%EC%84%9C%EC%9D%98-%EC%A0%91%EA%B7%BC%EB%B2%95)

#### naver 
* [2021-01-17] FK로 인해 삭제가 되지 않을 때 [BLOG에 정리한 부분](https://blog.naver.com/ggomjae/222210143484)
* [2021-03-12] 날짜 더미데이터 및 쿼리 [BLOG에 정리한 부분](https://blog.naver.com/ggomjae/222272961474)
* [2020-03-31] Join에 대한 정리 [BLOG에 정리한 부분](https://blog.naver.com/ggomjae/221883631299)
* [2020-03-07] Group by에 대한 흐름 정리 [BLOG에 정리한 부분](https://blog.naver.com/ggomjae/221842203247)

### 프로그래머스 SQL 문제 
1 ) ```SELECT```

```mysql based
SELECT * FROM ANIMAL_INS ORDER BY ANIMAL_ID
SELECT NAME ,DATETIME FROM ANIMAL_INS ORDER BY ANIMAL_ID DESC
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION = 'Sick' ORDER BY ANIMAL_ID
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION != 'Aged' ORDER BY ANIMAL_ID
SELECT ANIMAL_ID , NAME , DATETIME FROM ANIMAL_INS ORDER BY NAME ASC, DATETIME DESC
SELECT NAME FROM ANIMAL_INS ORDER BY DATETIME LIMIT 1
```
* 만약 ```LIMIT 4,6``` 라면 5부터 6개 추출

<br>

2 ) ```SUM``` ```MAX``` ```MIN```

```mysql based
SELECT ANIMAL_ID, MAX(DATETIME) AS 시간 FROM ANIMAL_INS
SELECT DATETIME AS 시간 FROM ANIMAL_INS ORDER BY DATETIME limit 1
SELECT count(*) AS count FROM ANIMAL_INS
SELECT COUNT(distinct NAME) FROM ANIMAL_INS
``` 
* 중복, NULL 제거 * -> ```distinct```
  <br>

3 ) ```GROUP BY```

```mysql based
SELECT ANIMAL_TYPE , count(*) AS count FROM ANIMAL_INS GROUP BY ANIMAL_TYPE ORDER BY ANIMAL_TYPE
SELECT NAME , COUNT(*) AS COUNT FROM ANIMAL_INS GROUP BY NAME HAVING COUNT(NAME)>= 2 ORDER BY NAME
SELECT HOUR(DATETIME) AS HOUR , COUNT(DATETIME) FROM ANIMAL_OUTS WHERE HOUR(DATETIME) >= 9 AND HOUR(DATETIME) <= 19 GROUP BY HOUR(DATETIME) ORDER BY HOUR(DATETIME)

``` 
* ```COUNT(*)``` : 조회된 전체행 건수를 반환한다
* ```COUNT(컬럼)``` : 컬럼의 값이 NULL인 행은 카운트 하지 않는다
* ```COUNT(DISTINCT 컬럼)``` : 컬럼 값을 중복제거하고, 컬럼의 값 건수를 반환한다

<br>

4 ) ```IS NULL```

```mysql based
SELECT ANIMAL_ID FROM ANIMAL_INS WHERE NAME IS NULL ORDER BY ANIMAL_ID
SELECT ANIMAL_ID FROM ANIMAL_INS WHERE NAME IS NOT NULL ORDER BY ANIMAL_ID
SELECT ANIMAL_TYPE , IFNULL(NAME,'No name') AS NAME , SEX_UPON_INTAKE FROM ANIMAL_INS ORDER BY ANIMAL_ID
``` 
* ```IFNULL``` 중요

<br>

5 ) ```JOIN```

```mysql based
SELECT B.ANIMAL_ID ,B.NAME FROM ANIMAL_INS A RIGHT JOIN ANIMAL_OUTS B ON A.ANIMAL_ID = B.ANIMAL_ID WHERE A.ANIMAL_ID IS NULL ORDER BY ANIMAL_ID
SELECT A.ANIMAL_ID, A.NAME FROM ANIMAL_INS A JOIN ANIMAL_OUTS B ON A.ANIMAL_ID = B.ANIMAL_ID WHERE A.DATETIME > B.DATETIME ORDER BY A.DATETIME
SELECT A.NAME , A.DATETIME FROM ANIMAL_INS A LEFT JOIN ANIMAL_OUTS B  ON A.ANIMAL_ID = B.ANIMAL_ID WHERE B.DATETIME IS NULL ORDER BY A.DATETIME LIMIT 3
SELECT B.ANIMAL_ID, B.ANIMAL_TYPE , B.NAME FROM ANIMAL_INS A JOIN ANIMAL_OUTS B ON A.ANIMAL_ID = B.ANIMAL_ID WHERE A.SEX_UPON_INTAKE LIKE 'Intact%' AND (B.SEX_UPON_OUTCOME LIKE 'Spayed%' OR B.SEX_UPON_OUTCOME LIKE 'Neutered%') ORDER BY B.ANIMAL_ID
``` 

<br>

6 ) ```String``` ```DATE```

```mysql based
SELECT ANIMAL_ID, NAME, SEX_UPON_INTAKE FROM ANIMAL_INS WHERE NAME IN ('Lucy', 'Ella', 'Pickle', 'Rogan', 'Sabrina', 'Mitty') ORDER BY ANIMAL_ID
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE NAME LIKE '%el%' AND ANIMAL_TYPE = 'DOG' ORDER BY NAME
SELECT ANIMAL_ID, NAME , CASE WHEN SEX_UPON_INTAKE LIKE 'Neutered%' THEN 'O' WHEN SEX_UPON_INTAKE LIKE 'Spayed%' THEN 'O' ELSE 'X' END AS 중성화 FROM ANIMAL_INS ORDER BY ANIMAL_ID
SELECT * FROM (SELECT A.ANIMAL_ID, A.NAME FROM ANIMAL_INS A, ANIMAL_OUTS B WHERE A.ANIMAL_ID = B.ANIMAL_ID ORDER BY  A.DATETIME - B.DATETIME) WHERE ROWNUM <= 2
SELECT ANIMAL_ID , NAME , DATE_FORMAT(DATETIME,'%Y-%m-%d') AS 날짜 FROM ANIMAL_INS ORDER BY ANIMAL_ID
``` 
* ```CASE WHEN THEN ELSE END``` 중요
* ```A.DATETIME``` - ```B.DATETIME```
-------
