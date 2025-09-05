| GitHub | Documentation | Demo |
| ------ | ------------- | ---- |
| [![GitHub](https://img.shields.io/badge/GitHub-nhatbao1504-blue?logo=github)](https://github.com/nhatbao1504) | [![Documentation](https://img.shields.io/badge/Documentation-nhatbao1504-blue?logo=read-the-docs)](https://drive.google.com/file/d/1swbB-zVuNQvrPK9n6aYtHmk7V2K9rzf7/view?usp=drive_link) | [![Demo](https://img.shields.io/badge/Youtube-Demo-006BFF?logo=youtube)](https://gurubase.io/g/vanna) |

# STUDY ON TECHNIQUES FOR CONVERTING NATURAL LANGUAGE QUERIES TO SQL COMMAND WITH LARGE LANGUAGE MODEL
Data is one of the most valuable resources today, but querying it with **SQL** is often a barrier for non-technical users.   This project studies and develops a **Vietnamese Text-to-SQL system** powered by **Large Language Models (LLMs)** such as **Qwen2.5, Llama3.2, and Ministral-3B**.  
The main goal is to allow users to ask questions in natural Vietnamese language → the system will automatically generate valid **SQL queries** compatible with the database schema. 

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
