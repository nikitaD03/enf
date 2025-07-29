#  ERD — Интернет-магазин одежды (Django + HTMX + Alpine.js)

##  Особенности проекта

- Стек технологий: **Django + HTMX + Alpine.js**
- Две платёжные системы: **Stripe** и **Heleket** (криптовалюта)
- **Docker-контейнеризация** с PostgreSQL
- Кастомизированная модель пользователя
- Защищённые настройки (CSRF, HTTPS, Security Headers)

---

## 🚀 Запуск проекта

## 1. Локальный запуск

**Установите зависимости:**
```bash
python -m pip install -r requirements.txt
```
### 2. Создайте и активируйте виртуальное окружение:
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate    # Windows
```
### 3. Настройте переменные окружения:
```bash
# Заполните .env своими значениями
```
### 4. Запустите миграции:
```bash
python manage.py migrate
```
### 5. Создайте суперпользователя:
```bash
python manage.py createsuperuser
```
### 6. Запустите сервер:
```bash
python manage.py runserver
```

## 2. Запуск на сервере с SSL

### 1. Подготовьте домен:
- Установите DNS-запись для `domen.com`, направив её на ваш IP-адрес сервера.

### 2. Настройте `.env`:

```env
SECRET_KEY='example'

POSTGRES_DB=enfdb
POSTGRES_USER=enfdb
POSTGRES_PASSWORD=enfdb
POSTGRES_HOST=localhost  
POSTGRES_PORT=5432

STRIPE_SECRET_KEY='example'
STRIPE_WEBHOOK_SECRET='example'

HELEKET_API_KEY='example'
HELEKET_SECRET_KEY='example'
```
### 3. Получите SSL-сертификаты с помощью certbot:
```bash
sudo certbot --nginx -d domen.com -d www.domen.com
```
### 4. Соберите и запустите контейнеры:
```bash
docker-compose up --build -d
```
### 5. Соберите статику:
```bash
docker-compose exec web python manage.py collectstatic --no-input
```

# 🔒 Настройки безопасности

## Основные меры защиты:

- ✅ CSRF защита включена
- ✅ Secure Cookies активированы
- ✅ Заголовки безопасности настроены
- ✅ HTTPS включён при работе через Docker

## 🔗 Доступ к проекту:

- 🌐 Локально: [http://localhost:8000](http://localhost:8000)
- 🔐 В Docker с SSL: [https://domen.com](https://domen.com)






