# 條件查詢

---

## 語法

---

> Select

> > 查詢列表(3)

> from

> > 表名(1)

> where

> > 篩選條件(2)

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
  SELECT \*
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
