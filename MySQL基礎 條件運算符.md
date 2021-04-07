# 條件查詢

---

## 語法

---

> Select

> 查詢列表(3)

> from

> 表名(1)

> where

> 篩選條件(2)

#### 執行順序(1)->(2)->(3)

---

## 分類

---

### 按條件表達式篩選

### 條件運算符: > < = <> >= <=

### 按邏輯表達式篩選

### 邏輯運算符: && || ! and or not

### 模糊查詢

### like between and in is null

---

- ## 案例一 查詢工資>12000 的員工訊息
  SELECT  
  \*  
  FROM  
  employee  
  WHERE salary > 12000

---

- ## 案例二 查詢部門編號不等於 90 號的員工名和部門編號
  SELECT  
  last_name, department_id  
  FROM  
  employees  
  WHERE department<>90

---

## 按邏輯表達式篩選

- ## 案例一 查詢工資 Z 在 10000 到 20000 之間的員工名，工資以及獎金
  SELECT  
  salary,  
  last_name,  
  commission_pct  
  FROM  
  employees  
  WHERE  
  salary>=10000 AND salary<=20000;
- ## 案例二 查詢部門編號不是在 90 到 110 之間，或著工資高於 15000 的員工訊息
  SELECT  
  \*  
  FROM  
  employees  
  WHERE department_id<90 AND department_id>110 OR salary>15000;

---

## 模糊查詢

> like

- 特點:
- - 一般和通配符搭配使用
- - 通配符:
- - % 任意多個字符
- - \_ 任意多個字符
- - \ 轉移符號

- ## 案例一 查詢員工名中包含字符 a 的員工訊息
  SELECT  
  \*  
  FROM  
  employees  
  WHERE last_name LIKE "%a%";
- ## 案例二 查詢員工名中第三個字符為 n， 第五個字符為 l 的員工名和工資
  SELECT  
  last_name,  
  salary  
  FROM  
  employees  
  WHERE last_name LIKE "\_\_n_l%";
- ## 案例三 查詢員工名中第二個字符為\_的員工名
  SELECT  
  last*name,
  FROM  
  employees  
  WHERE last*name LIKE "\_\\\_\*%";

> between and

- 特點:
- - 提高簡潔度
- - 包含連結值>= <=
- - 兩個臨界值不要調換順序

- ## 案例一 查詢員工編號在 100 到 120 之間的員工訊息

  SELECT  
  \*  
  FROM  
  employees  
  WHERE employees_id>=100 AND employees_id<=120;

  ***

  #### 同上

  SELECT  
  \*  
  FROM  
  employees  
  WHERE employees_id between 100 AND 120;

  > in

- 特點:
- - 判斷某字段的值是否屬於 IN 列表中的某一項
- - 使用 in 提高語句簡潔度
- - in 列表的值類型必須一致或兼容

- ## 案例一 查詢員工的工種編號是 IT_PROG、AD_VP、AD_PRES 中的一個員工名和工種編號

  SELECT  
  last_name,  
  job_id  
  FROM  
  employees  
  WHERE job_id = "IT_PROG" OR job_id = "AD_VP" OR job_id = "AD_PRES";

  #### 同上

  SELECT  
  last_name,  
  job_id  
  FROM  
  employees  
  WHERE job_id IN("IT_PROG","AD_VP","AD_PRES");

  > is null| is not null

- 特點:
- - =或<>不能用於判斷 null 值
- - is null 或 is not null 可以判斷 null 值

- ## 案例一 查詢沒有獎金的員工名和獎金率

  SELECT  
  last_name,  
  commission_pct  
  FROM  
  employees  
  WHERE commission_pct IS NULL;

- ## 案例二 查詢有獎金的員工名和獎金率

  SELECT  
  last_name,  
  commission_pct  
  FROM  
  employees  
  WHERE commission_pct IS NOT NULL;

  > 安全等於 <=>

- 特點:
- - 可以判斷 null 值，又可以判斷普通的數值，但可讀性低
- -

- ## 案例一 查詢沒有獎金的員工名和獎金率

  SELECT  
  last_name,  
  commission_pct  
  FROM  
  employees  
  WHERE commission_pct <=> NULL;

- ## 案例二 查詢工資為 12000 的員工訊息

  SELECT  
  last_name,  
  salary  
  FROM  
  employees  
  WHERE salary <=> 12000;
