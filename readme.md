| GitHub | Documentation | Demo |
| ------ | ------------- | ---- |
| [![GitHub](https://img.shields.io/badge/GitHub-nhatbao1504-blue?logo=github)](https://github.com/nhatbao1504) | [![Documentation](https://img.shields.io/badge/Documentation-nhatbao1504-blue?logo=read-the-docs)](https://drive.google.com/file/d/1swbB-zVuNQvrPK9n6aYtHmk7V2K9rzf7/view?usp=drive_link) | [![Demo](https://img.shields.io/badge/Youtube-Demo-006BFF?logo=youtube)](https://youtu.be/DEnVh9WBYo8) |

# STUDY ON TECHNIQUES FOR CONVERTING NATURAL LANGUAGE QUERIES TO SQL COMMAND WITH LARGE LANGUAGE MODEL
Data is one of the most valuable resources today, but querying it with **SQL** is often a barrier for non-technical users.   This project studies and develops a **Vietnamese Text-to-SQL system** powered by **Large Language Models (LLMs)** such as **Qwen2.5, Llama3.2, and Ministral-3B**.  
This project focuses on building a **Vietnamese Text-to-SQL system** powered by **Large Language Models (LLMs)** such as **Qwen2.5, Llama3.2, and Ministral-3B**.  

The goal is to enable users to ask questions in **natural Vietnamese language** and automatically generate corresponding **SQL queries** that can be executed on relational databases.  

By leveraging **fine-tuning techniques** (SFT, LoRA/QLoRA), **prompt engineering**, and **Unsloth optimization**, the system achieves efficient training and high execution accuracy.  

![Vietnamese-Text-to-SQL](https://github.com/nhatbao1504/Text-to-SQL-Vietnamese/blob/main/assets/pipeline.png?raw=true)

## 🚀 Key Features
- Convert Vietnamese natural language questions into SQL queries.  
- Support multiple database schemas.  
- Fine-tuned with advanced techniques:
  - **Supervised Fine-Tuning (SFT)**
  - **LoRA / QLoRA** (parameter-efficient fine-tuning)
  - **Prompt Engineering** (Alpaca-style prompts)
  - **Unsloth** (training optimization for speed & memory).  
- Evaluated using **Execution Accuracy (EA)** and **Exact Match Accuracy (EM)**.  

---

## 🗄️ Database
We use two widely recognized **Text-to-SQL benchmark datasets**:  

- [**WikiSQL**](https://arxiv.org/abs/1709.00103) (Zhong et al., 2017): Contains simple queries with basic `SELECT` and `WHERE` clauses.  
- [**Spider**](https://arxiv.org/abs/1809.08887) (Yu et al., 2018): A large-scale dataset with **complex queries**, requiring `JOIN`, `GROUP BY`, `ORDER BY`, and nested subqueries.

### 🔄 Translation into Vietnamese
Since both datasets are originally in English, we translated **natural language questions** and **database schemas** into Vietnamese.  

#### Example (WikiSQL):
- **Original question (EN):**  
  `What is the population of California?`  

- **Translated question (VN):**  
  `Dân số của California là bao nhiêu?`  

- **Original schema (EN):**  
  `states(id, name, population)`  

- **Translated schema (VN):**  
  `bang(id, ten, dan_so)`  

- **Generated SQL:**  
  ```sql
  SELECT dan_so 
  FROM bang 
  WHERE ten = 'California';
  ```

#### Example (Spider):
- **Original question (EN):**  
  `List the names of students who enrolled in 2020.`  

- **Translated question (VN):**  
  `Liệt kê tên sinh viên đã ghi danh vào năm 2020.`  

- **Schema (VN):**  
  ```
  sinh_vien(id, ten, nam_ghi_danh)
  ```  

- **Generated SQL:**  
  ```sql
  SELECT ten 
  FROM sinh_vien 
  WHERE nam_ghi_danh = 2020;
  ```

---

## 📊 Experimental Results
| Model           | Dataset (VN) | EM (%) | EA (%) |
|-----------------|--------------|--------|--------|
| Qwen2.5-3B      | Spider       | 78.5   | 82.1   |
| Llama3.2-3B     | Spider       | 75.2   | 79.3   |
| Ministral-3B    | Spider       | 73.6   | 80.4   |

---

## 📐 Evaluation Metrics
- **Exact Match (EM):** Measures whether the predicted SQL query exactly matches the gold (reference) query.  
- **Execution Accuracy (EA):** Measures whether the predicted query, when executed on the database, returns the same result as the gold query.  

These two metrics complement each other: EM is stricter (requires identical syntax), while EA allows flexibility as long as the results are correct.  

---

## ✨ Demo
[![Watch the demo](https://img.youtube.com/vi/DEnVh9WBYo8/0.jpg)](https://www.youtube.com/watch?v=DEnVh9WBYo8)
