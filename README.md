# 📞 Contacts API (FastAPI + PostgreSQL)

## 📌 Опис проєкту
Цей проєкт – REST API для управління контактами.  
Реалізований на `FastAPI` з використанням `PostgreSQL` та `SQLAlchemy`.  

### 🔹 **Функціонал API:**
✅ Додавання нового контакту  
✅ Отримання списку всіх контактів  
✅ Отримання контакту за ID  
✅ Оновлення контакту  
✅ Видалення контакту  
✅ Пошук контактів за ім'ям, прізвищем або email  
✅ Отримання контактів з днями народження у найближчі 7 днів  

---

## ⚙️ **Встановлення та запуск**
### **🔹 1️⃣ Клонування репозиторію**
```bash
git clone https://github.com/jure-s/goit-pythonweb-hw-08.git
cd goit-pythonweb-hw-08
```

### **🔹 2️⃣ Створення та активація віртуального середовища**
```bash
python -m venv venv
# Активація (Windows)
venv\Scripts\activate
# Активація (Linux/macOS)
source venv/bin/activate
```

### **🔹 3️⃣ Встановлення залежностей**
```bash
pip install -r requirements.txt
```

### **🔹 4️⃣ Налаштування змінних середовища**
Створи файл `.env` у корені проєкту та додай:
```
DATABASE_URL=postgresql://postgres:твій_пароль@localhost:5433/contacts_db
```

---

## 🛠 **Запуск проєкту**
### **🔹 1️⃣ Запуск FastAPI**
```bash
uvicorn app.main:app --reload
```
**📌 API буде доступне за адресою:**  
🔗 [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs) (Swagger UI)  
🔗 [http://127.0.0.1:8000/redoc](http://127.0.0.1:8000/redoc) (ReDoc)

---

## 🔍 **API-ендпоінти**
### 📌 **Створення контакту**
**`POST /contacts/`**  
```json
{
  "first_name": "John",
  "last_name": "Doe",
  "email": "john.doe@example.com",
  "phone": "380-99-123-45-67",
  "birthday": "1990-06-15",
  "extra_info": "Friend"
}
```

### 📌 **Отримання всіх контактів**
**`GET /contacts/`**

### 📌 **Отримання контакту за ID**
**`GET /contacts/{contact_id}`**

### 📌 **Оновлення контакту**
**`PUT /contacts/{contact_id}`**  
```json
{
  "first_name": "Jane",
  "last_name": "Doe",
  "email": "jane.doe@example.com"
}
```

### 📌 **Видалення контакту**
**`DELETE /contacts/{contact_id}`**

### 📌 **Пошук контактів**
**`GET /contacts/search/?name=John`**  
**`GET /contacts/search/?email=john.doe@example.com`**

### 📌 **Контакти з днями народження у найближчі 7 днів**
**`GET /contacts/upcoming_birthdays/`**

---

## 🗄 **База даних**
📌 Перед першим запуском створіть базу **PostgreSQL**:
```sql
CREATE DATABASE contacts_db;
```
🔹 **Переконайтеся, що PostgreSQL працює на порту `5433`** (або змініть у `.env`).

---

## 📌 **Docker (опціонально)**
### **🔹 1️⃣ Запуск PostgreSQL через Docker**
```bash
docker-compose up -d
```

### **🔹 2️⃣ Запуск FastAPI в контейнері**
```bash
docker build -t contacts-api .
docker run -p 8000:8000 --env-file .env contacts-api
```

---

