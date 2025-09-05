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

| Model         | EM Accuracy (%) | Execution Accuracy (%) |
|---------------|-----------------|-------------------------|
| Qwen2.5-3B    | 42              | 54                      |
| Llama3.2-3B   | 42              | 48                      |
| Ministral-3B  | 34              | 46                      |

---

## 📐 Evaluation Metrics
- **Exact Match (EM):** Measures whether the predicted SQL query exactly matches the gold (reference) query.  
- **Execution Accuracy (EA):** Measures whether the predicted query, when executed on the database, returns the same result as the gold query.  

These two metrics complement each other: EM is stricter (requires identical syntax), while EA allows flexibility as long as the results are correct.  

---

## 🔎 Analysis of Results
The models show varying strengths in Text-to-SQL generation:  

- **Qwen2.5-3B** achieved the highest **Execution Accuracy (54%)**, indicating stronger semantic understanding and better ability to generate queries that execute correctly, even if the syntax does not exactly match.  
- **Llama3.2-3B** had comparable **Exact Match (42%)** but lower **Execution Accuracy (48%)**, suggesting that while it often produced syntactically correct queries, they were more prone to semantic errors when executed.  
- **Ministral-3B** performed weakest (**34% EM, 46% EA**), reflecting both lower syntactic precision and weaker semantic alignment.  

### ⚠️ Important Note on Scoring
During evaluation, minor syntactical differences—such as:  
- Extra whitespace (`COUNT(*)` vs `COUNT ( * )`),  
- Case sensitivity of SQL keywords,  
- Returned column names (`COUNT(*)` vs `COUNT ( * )`),  

can **artificially reduce EM scores**. If normalization is not applied, these discrepancies may also lower **Execution Accuracy**, since mismatched column names can cause query results to be treated as different.  

To focus on **semantic correctness**, our detailed error analysis sets aside these minor issues and instead evaluates whether the **query structure and logic** align with the intended meaning of the natural language question.  

---

## ✨ Demo
[![Watch the demo](https://img.youtube.com/vi/DEnVh9WBYo8/0.jpg)](https://www.youtube.com/watch?v=DEnVh9WBYo8)
