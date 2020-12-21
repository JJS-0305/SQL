# MY SQL 순위 함수

## 1. RANK

- RANK 함수는 중복 값들에 대해서 동일 순위로 표시.

- 중복 순위 다음 값에 대해서는 중복 개수만큼 떨어진 순위로 출력

> SELECT score,
>
> RANK() OVER (ORDER BY score DESC) RANK
>
> FROM scores;



**score 	rank**

 400			1

 400			1

 380			3

 350			4



## 2. DENSE RANK

- DENSE_RANK 함수는 중복 값들에 대해서 동일 순위로 표시.
- 중복 순위 다음 값에 대해서는 중복 값 개수와 상관없이 순차적인 순위 값 출력

> SELECT score,
>
> DENSE_RANK() OVER (ORDER BY score DESC) DENSE_RANK
>
> FROM scores;



**score 	dense_rank**

 400				1

 400				1

 380				2

 350				3



## 3. ROW NUMBER

- ROW_NUMBER 함수는 중복 값들에 대해서도 순차적인 순위를 표시.

> SELECT score, 
>
> ROW_NUMBER() OVER (ORDER BY score DESC) ROW_NUMBER
>
> FROM scores



**score 	row_number**

 400				1

 400				2

 380				3

 350				4



## 4. NTILE

- 뒤에 함께 적어주는 숫자 만큼으로 등분.

> SELECT score,
>
> NTILE(4) OVER (ORDER BY score DESC) NTILE
>
> FROM scores



 **score	ntile**

  400	 	1

  400	 	1

  380	 	2

  350	 	2

  330	 	3

  260	 	3

  150	 	4

  150	 	4



## 5. PARTITION BY

- 특정 속성 별로 구분을 해서 순위를 매김.

> SELECT empName, job, salary 
>
> RANK() OVER (PARTITION BY job ORDER BY score DESC) RANK
>
> FROM employee



**empName	 job	salary	rank**

​	박명수		과장	500		1

​	정준하		과장	500		1

​	지석진		과장	350		3

​	유재석		부장	700		1

​	강호동		부장	680		2

​	신동엽		부장	680		2

​	하동훈		대리	300		1

​	이광수		대리	250		2

