# SQL

### 기본 CRUD 로직

1. 조회

```mysql
SELECT * FROM users_user;
```

2. user 레코드 생성

```mysql
INSERT INTO users_user ('first_name', 'last_name', 'age', 'country', 'phone', 'balance')
VALUES ('근제', '성', 80, '서울', '011-123-1324', 999999999999999999999);
```

3. 해당 user 레코드 수정

```mysql
UPDATE user_user
SET last_name='최'
WHERE id = 100;
```

4. 해당 user 레코드 삭제

```mysql
DELETE FROM users_user
WHERE id = 102;
```



### 조건에 따른 쿼리문

1. 전체 인원 수

```mysql
SELECT COUNT(*) FROM users_user;
```

2. 나이가 30인 사람의 이름

```mysql
SELECT NAME FROM users_user WHERE age=30;
```

3. 나이가 30살 이상인 사람의 인원 수

```mysql
SELECT COUNT(*) FROM users_user WHERE age>=30;
```

4. 나이가 30이면서 성이 김씨인 사람의 인원 수

```mysql
SELECT COUNT(*) FROM users_user WHERE age=30 AND last_name='김';
```

5. 지역번호가 02인 사람의 인원 수

```mysql
SELECT COUNT(*) FROM users_user WHERE phone LIKE '02-%';
```



### 정렬 및 LIMIT, OFFSET

1. 나이가 많은 사람 10명(내림차순)

```mysql
SELECT * FROM users_user ORDER BY age DESC LIMIT 10;
```

2. 잔액이 적은 사람 10명(오름차순)

```mysql
SELECT * FROM users_user ORDER BY balance LIMIT 10;
```

3. 성, 이름 내림차순 순으로 5번째 있는 사람

```mysql
SELECT * FROM users_user ORDER BY last_name DESC, first_name DESC
LIMIT 1 OFFSET 4;
```



### 표현식

1. 전체 평균 나이

```mysql
SELECT AVG(age) FROM users_user;
```

2. 김씨의 평균 나이

```mysql
SELECT AVG(age) FROM users_user WHERE last_name='김';
```

3. 계좌 잔액 중 가장 높은 값

```mysql
SELECT MAX(balance) FROM users_user;
```

4. 계좌 잔액 총액

```mysql
SELECT SUM(balance) FROM users_user;
```



### GROUP BY

1. 지역별 인원 수

```mysql
SELECT country, COUNT(country) FROM users_user GROUP BY country;
```

2. 지역별 인원 수가 10 이상인 값

```mysql
SELECT country, COUNT(country) FROM users_user 
GROUP BY country HAVING COUNT(country) >= 10
```



### CASE

> CASE WHEN 조건절 THEN 참일때 값 ELSE 거짓일때 값 END 컬럼명 



### UNION

> SELECT name FROM my_table1
>
> **UNION**
>
> SELECT name FROM my_table2
>
> **UNION**
>
> SELECT name FROM my_table3;
>
> **// 모든 결과를 name열에 출력함.**
>
> **// 모든 결과를 합치는 동작.**
>
> // 중복 데이터는 없다.
>
> // 열의 개수는 같아야 한다.
>
> // 위에서 한 개 이면 밑에도 동일해야 한다.



### UNION ALL

> SELECT name FROM my_table1
>
> **UNION ALL**
>
> SELECT name FROMy_table2
>
> **UNION ALL**
>
> SELECT name FROM my_table3;
>
> **// UNION ALL을 사용하면 중복된 값들도 전부 출력한다.**



### JOIN

![SQL_JOIN](./SQL_JOIN.png)

- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- FULL OUTER JOIN

--------------------------------------------------------------------------------------------------------------------------------------



### 추가

- DISTINCT (중복제거)

- IFNULL(A,B)
  
  - A가 NULL이면 B를, 그렇지 않으면 A 반환
  
- DATE_FORMAT

  ```mysql
  SELECT DATE_FORMAT(NOW(), "%Y %c/%E %r")
  ```

  - %M  : 월(January, December, ...)
  - %W : 요일(Sunday, Monday, ...)
  - %D : 월(1st, 2nd, ...)
  - %Y : 연도(1987, 2000, 2020)
  - %y : 연도(87,00,20)
  - %a : 요일(Sun, Mon, ...)
  - %d : 일(00,01,02, ...)
  - %e : 일(0, 1, 2, ...)
  - %c : 월(1, 2, ...)