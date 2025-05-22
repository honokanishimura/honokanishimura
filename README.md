# PHP + SQLite FTS Filter Backend (NTT East Style)

This repository contains a backend prototype for a multi-category filter and full-text search engine, built using PHP, SQLite (FTS5), and MeCab.  
It replicates the core logic of a real-world enterprise project developed for NTT East Japan.

---

## 💻 Technologies Used

| Technology      | Description |
|------------------|-------------|
| PHP             | Plain PHP for backend logic |
| SQLite + FTS5   | Full-text search support for Japanese keywords |
| MeCab           | Japanese tokenizer for indexing search terms |
| GET Parameters  | Encoded multi-filter values (e.g., `sv=2|3`) |
| Simple MVC-style| Separated logic files: index, common, connect |

---

## 📷 Screenshots

| Production-style UI | 
|---------------------|
| ![search](https://github.com/user-attachments/assets/aa5cc731-6cf9-449e-9fd3-72f84c2457b1)
| ![search](https://github.com/user-attachments/assets/6396a35c-61bd-4c01-9c8d-1d42443fabe5)

These screenshots show how multi-category checkboxes and keyword input work together to filter results.  
This project emphasizes backend logic and functionality, not frontend styling.

---

## 🔍 Features

- Multi-category filtering using dynamic GET parameters
- URL structure: `?sv=2|3&issues=1|4` (OR within / AND between categories)
- Full-text search in Japanese via MeCab + SQLite FTS5
- Supports scalable page types: Column / Case Study / Video / Document
- Core filter logic centralized in `common.php` for maintainability

---

## 📁 File Overview

| File             | Purpose |
|------------------|---------|
| `index.php`      | Displays form and handles GET submission |
| `common.php`     | Parses filters and builds SQL queries |
| `db_connect.php` | Manages connection to SQLite database |
| `data_loader.php`| Seeds test data into the DB |
| `ntt_east.db`    | Prebuilt database with FTS5 support |
| `examples.json`  | Sample article and category data |

---

## 🧠 Structure Overview

```txt
GET: ?k=keyword&sv=2|3&issues=1|4
↓
common.php parses parameters
↓
FTS MATCH + OR/AND logic assembled
↓
SQL executed on FTS5-indexed SQLite DB
↓
Filtered results returned to index.php
