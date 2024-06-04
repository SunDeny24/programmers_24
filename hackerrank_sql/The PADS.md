# The PADS
https://www.hackerrank.com/challenges/the-pads/problem?isFullScreen=true

### 문제
1. OCCUPATIONS 테이블에서 이름을 알파벳 순서대로 정렬하고, 각 직업의 첫 글자를 괄호 안에 넣어서 출력하세요. 
예를 들어: AnActorName(A), ADoctorName(D), AProfessorName(P), ASingerName(S)와 같이 출력하세요.

2. OCCUPATIONS 테이블에서 각 직업의 발생 횟수를 조회하세요. 발생 횟수를 오름차순으로 정렬하고, 다음 형식으로 출력하세요
##### 입력형식

> There are a total of [occupation_count] [occupation]s.

여기서 [occupation_count]는 OCCUPATIONS 테이블에서 해당 직업의 발생 횟수이고, [occupation]은 소문자로 된 직업 이름입니다. 
만약 여러 직업의 발생 횟수가 동일하다면, 알파벳 순으로 정렬합니다.

### 풀이

```sql
select 
     concat(name , '(' , left(occupation,1 ), ')') 
from OCCUPATIONS 
order by name asc;

select 
      concat('There are a total of ' , count(*), ' ', lower(occupation), 's.' )
 from OCCUPATIONS
 group by occupation
 order by count(*) , occupation;

```
> 문자를 붙혀 사용해주는 concat, 소문자 출력하는 lower, 앞글자만 따올수 있도록 left 함수를 사용함
> 발생수는 직업의 데이터 수임으로 occupation group by로 count(*)를 해서 카운팅해줬다.
> mysql 버전이기 때문에 ';' 를 마지막에 붙혀 두개의 쿼리를 실행시킨다.
