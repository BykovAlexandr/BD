<h1 align="center">📊 БАЗЫ ДАННЫХ</h1>

<div align="center">
  
  **Студент:** Быков Александр  
  **Группа:** ПМИ-32БО  
  **Вариант:** 7

</div>

---

<h1 name="content" align="center">
  <a href="">
    <img src="https://github.com/user-attachments/assets/e080adec-6af7-4bd2-b232-d43cb37024ac" width="20" height="20"/>
  </a> 
  MSSQL
</h1>

<p align="center">
  <a href="#-lab1"><img alt="lab1" src="https://img.shields.io/badge/Lab1-blue"></a> 
  <a href="#-lab2"><img alt="lab2" src="https://img.shields.io/badge/Lab2-red"></a>
  <a href="#-lab3"><img alt="lab3" src="https://img.shields.io/badge/Lab3-green"></a>
  <a href="#-lab4"><img alt="lab4" src="https://img.shields.io/badge/Lab4-yellow"></a>
  <a href="#-lab5"><img alt="lab5" src="https://img.shields.io/badge/Lab5-gray"></a>
  <a href="#-lab6"><img alt="lab6" src="https://img.shields.io/badge/Lab6-orange"></a> 
  <a href="#-lab7"><img alt="lab7" src="https://img.shields.io/badge/Lab7-brown"></a>
  <a href="#-lab8"><img alt="lab8" src="https://img.shields.io/badge/Lab8-purple"></a>
  <a href="#-lab9"><img alt="lab9" src="https://img.shields.io/badge/Lab9-violet"></a> 
</p>

# <a id="-lab1"></a><img src="https://github.com/user-attachments/assets/e080adec-6af7-4bd2-b232-d43cb37024ac" width="20" height="20"/> Lab1
[Назад](#content)

<h3 align="center">
  Лабораторная работа №1
</h3>

### ER-model:
![ER-model](https://github.com/BykovAlexandr/BD/blob/main/Модели/ER.jpg)

### Relational model:
![REL-model](https://github.com/BykovAlexandr/BD/blob/main/Модели/Реляционная%20модель.jpg)

# <a id="-lab2"></a><img src="https://github.com/user-attachments/assets/e080adec-6af7-4bd2-b232-d43cb37024ac" width="20" height="20"/> Lab2
[Назад](#content)

<h3 align="center">
  Лабораторная работа №2
</h3>

### Создание SQL таблицы:

```sql
CREATE TABLE Группа (
    ID_группы INT PRIMARY KEY,
    Название NVARCHAR(100) NOT NULL,
    Программа NVARCHAR(50),
    Макс_детей INT CHECK (Макс_детей > 0),
    Возраст SMALLINT CHECK (Возраст > 0)
);

CREATE TABLE Воспитатель (
    ID_воспитателя INT PRIMARY KEY,
    Имя NVARCHAR(50) NOT NULL,
    Фамилия NVARCHAR(50) NOT NULL,
    Отчество NVARCHAR(50),
    Телефон NVARCHAR(20)
);

CREATE TABLE Ребенок (
    ID_ребенка INT PRIMARY KEY,
    Имя NVARCHAR(50) NOT NULL,
    Фамилия NVARCHAR(50) NOT NULL,
    Отчество NVARCHAR(50),
    Дата_рождения DATE NOT NULL,
    Адрес NVARCHAR(200),
    ID_группы INT,
    FOREIGN KEY (ID_группы) REFERENCES Группа(ID_группы)
);

CREATE TABLE Ведет (
    ID_воспитателя INT REFERENCES Воспитатель(ID_воспитателя),
    ID_группы INT REFERENCES Группа(ID_группы),
    PRIMARY KEY (ID_воспитателя, ID_группы)
);

CREATE TABLE Родственник (
    ID_родственника INT PRIMARY KEY,
    Имя NVARCHAR(50) NOT NULL,
    Фамилия NVARCHAR(50) NOT NULL,
    Отчество NVARCHAR(50),
    Место_работы NVARCHAR(200),
    Телефон NVARCHAR(20),
    Тип_родства NVARCHAR(20) NOT NULL,
    ID_ребенка INT REFERENCES Ребенок(ID_ребенка)
);

CREATE TABLE Измерения (
    ID_измерения INT PRIMARY KEY,
    Рост DECIMAL(5,2) CHECK (Рост > 0),
    Вес DECIMAL(5,2) CHECK (Вес > 0),
    Дата DATE NOT NULL,
    ID_ребенка INT REFERENCES Ребенок(ID_ребенка)
);

CREATE TABLE Болезнь (
    ID_болезни INT PRIMARY KEY,
    Название NVARCHAR(50) NOT NULL
);

CREATE TABLE Больничный (
    ID_больничного INT PRIMARY KEY,
    Дата_н DATE NOT NULL,
    Дата_к DATE NOT NULL,
    ID_ребенка INT REFERENCES Ребенок(ID_ребенка),
    ID_болезни INT REFERENCES Болезнь(ID_болезни),
    CHECK (Дата_к >= Дата_н)
);
```

### Таблица Болезнь:
![Рисунок1](https://github.com/BykovAlexandr/BD/blob/main/скрины/Рисунок1.png)
### Таблица Больничный:
![Рисунок2](https://github.com/BykovAlexandr/BD/blob/main/скрины/Рисунок2.png)
### Таблица Ведет:
![Рисунок3](https://github.com/BykovAlexandr/BD/blob/main/скрины/Рисунок3.png)
### Таблица Воспитатель:
![Рисунок4](https://github.com/BykovAlexandr/BD/blob/main/скрины/Рисунок4.png)
### Таблица Группа:
![Рисунок5](https://github.com/BykovAlexandr/BD/blob/main/скрины/Рисунок5.png)
### Таблица Измерения:
![Рисунок6](https://github.com/BykovAlexandr/BD/blob/main/скрины/Рисунок6.png)
### Таблица Ребенок:
![Рисунок7](https://github.com/BykovAlexandr/BD/blob/main/скрины/Рисунок7.png)
### Таблица Родственник:
![Рисунок8](https://github.com/BykovAlexandr/BD/blob/main/скрины/Рисунок8.png)
### Диаграмма таблицы:
![Рисунок9](https://github.com/BykovAlexandr/BD/blob/main/скрины/Рисунок9.png)

# <a id="-lab1"></a><img src="https://github.com/user-attachments/assets/e080adec-6af7-4bd2-b232-d43cb37024ac" width="20" height="20"/> Lab3
[Назад](#content)
<h3 align="center"> Лабораторная работа №3 </h3>

[Part 1-2](/Модели/Быков_ПМИ-32БО(ЛАБ3).docx)

# <a id="-lab1"></a><img src="https://github.com/user-attachments/assets/e080adec-6af7-4bd2-b232-d43cb37024ac" width="20" height="20"/> Lab4
[Назад](#content)
<h3 align="center"> Лабораторная работа №4 </h3>

[File](/Модели/Быков_ПМИ-32БО(ЛАБ4).docx)

# <a id="-lab1"></a><img src="https://github.com/user-attachments/assets/e080adec-6af7-4bd2-b232-d43cb37024ac" width="20" height="20"/> Lab5
[Назад](#content)
<h3 align="center"> Лабораторная работа №5 </h3>

[File](/lab5.docx)
