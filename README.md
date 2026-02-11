
**Дата:** 12 февраля 2026 г. (Среда).
**Группа:** 202-1 (Выпускной курс).
**Основание:** Ведомость тем (Seed: 4570724) и Методические указания (Рег. № с-288-22/02).

**МЕТОДИЧЕСКАЯ РАЗРАБОТКА СЕМИНАРА-ИНТЕНСИВА** (3 пары).

***

# Методичка к семинару

**Тема:** Аудит архитектуры, безопасности и документации курсового проекта (ПМ.09)
**Целевая аудитория:** Группа 202 (Специальность 09.02.07)
**Длительность:** 6 академических часов (3 пары).
**Стек:** PHP 8/Python, JS, SQL, Git, SonarCloud, Beget/PythonAnywhere.

---

## ПАРА 1. ТЕХНИЧЕСКИЙ АУДИТ И «ФИЧА-ЧЕК» (08:30 – 10:05)

### 1. Цель
Убедиться, что структура проекта соответствует паттерну MVC (для PHP), а также проверить реализацию обязательной «Фишки» из индивидуального задания.

### 2. Входной контроль (Чек-лист готовности)
Студент обязан иметь при себе:

*   Развернутый проект на **Beget** (бесплатный тариф).
*   Репозиторий на GitHub/GitLab (минимум 5 коммитов).

### 3. Ход работы

#### Шаг 1. Проверка структуры папок (Стандарт отрасли)
*Инструкция:* Откройте корень проекта. Сравните со эталоном:
*   **PHP (Native/Framework):** Папки `/public`, `/app` (или `/src`), `/views`, `/config`, `/vendor`. Файл `.gitignore` (обязательно исключить `/vendor` и конфиги БД).

#### Шаг 2. Валидация «Фишки» (Feature Compliance)
*Методист обращается к Ведомости распределения тем. Студенты проверяют друг друга (Cross-Review).*

**Примеры проверок (на основе ведомости 202):**
*   **Студент Агапов (Тема 4, LMS):** Покажите код, отвечающий за «Прогресс-бар». Где в БД хранится % прохождения? Если это просто `<div>` с шириной 50% без логики — **незачет**.
*   **Студент Барабашов (Тема 5, Афиша):** Демонстрация сортировки событий. Работает ли она через SQL (`ORDER BY date`) или JS? (Требуется SQL для оптимизации).
*   **Студент Вотинцев (Тема 19, Магазин ПК):** Фильтр совместимости CPU и сокета. Покажите SQL-запрос или логику на бэкенде, которая блокирует выбор несовместимого процессора.
*   **Студент Лещинский (Тема 25, Инвентаризация):** Генерация QR. Используется ли библиотека (напр., `phpqrcode`)? Сканируется ли код телефоном?

#### Шаг 3. Деплоймент-тест
Если проект еще не в сети:
1.  Регистрация на **Beget** (бесплатный хостинг, смс-подтверждение, без карты).
2.  Создание БД MySQL/PostgreSQL.
3.  Заливка файлов через File Manager или FTP.
4.  Правка `config.php` под боевую базу.

---

## ПАРА 2. АУДИТ БЕЗОПАСНОСТИ (OWASP & SONAR) (10:15 – 11:50)

### 1. Цель
Подготовить проект к автоматической приемке кода, выявить уязвимости SQL Injection и XSS.

### 2. Инструментарий
*   **SonarCloud** (Бесплатный тариф для публичных репозиториев GitHub).
*   **VS Code** (расширение SonarLint — желательно).

### 3. Ход работы

#### Шаг 1. Подключение SonarCloud (Strict No-Card Policy)
1.  Зайти на `sonarcloud.io`.
2.  Нажать "Login with GitHub".
3.  Выбрать свой репозиторий курсовой работы.
4.  Запустить "Analyze".

#### Шаг 2. Разбор «Запахов кода» (Code Smells)
Студент должен исправить критические замечания (Bugs & Vulnerabilities).
*   **SQL Injection:** Ищем прямую подстановку переменных (`SELECT * FROM users WHERE id = $id`).
    *   *Исправление:* Переделать на `PDO Prepare/Execute` (PHP) или ORM (Django).
*   **XSS:** Ищем вывод данных без экранирования (`echo $_GET['name']`).
    *   *Исправление:* Использовать `htmlspecialchars()` (PHP) или шаблонизатор (Twig/Jinja2).

#### Шаг 3. Ручное тестирование (Roleplay: «Злой хакер»)
Попробуйте ввести в формы вашего проекта следующие данные:
1.  В поле логина: `' OR '1'='1`
2.  В поле комментария: `<script>alert('Hacked')</script>`
*Если сайт пустил без пароля или всплыло окно — фиксируем ошибку в "List of Bugs".*

---

## ПАРА 3. НАПИСАНИЕ ПОЯСНИТЕЛЬНОЙ ЗАПИСКИ (12:30 – 14:05)

### 1. Цель
Сформировать черновик Введения и Главы 1 согласно ГОСТ и методичке (стр. 9-13).

### 2. Работа с шаблоном (Генерация контента)
*Используем данные из PDF «Методические указания».*

#### Блок А: Актуальность (Шаблон-конструктор)
Студенты пишут 1-2 абзаца, отвечая на вопрос: «Почему это нужно сейчас?».
*   *Для группы 202:* «В 2026 году наблюдается рост [сферы из вашей темы, например, онлайн-образования для Агапова / внутреннего туризма для Барабашова]. Существующие решения либо дороги, либо перегружены функционалом. Разработка [Название темы] позволит автоматизировать [Процесс] с учетом специфики [Малого бизнеса/Госучреждения].»

#### Блок Б: Объект и Предмет (Самая частая ошибка!)
*   **Объект:** Сфера деятельности (Широко).
    *   *Пример (Агапов):* Процесс организации дистанционного обучения.
    *   *Пример (Сенеджук, Недвижимость):* Деятельность агентства недвижимости.
*   **Предмет:** Программное обеспечение/Веб-приложение (Узко).
    *   *Пример:* Веб-приложение для автоматизации продажи курсов с функцией прогресс-бара.

#### Блок В: Цель и Задачи (Глаголы)
**Цель:** Разработка веб-приложения [Название] для [Заказчик/Сфера].
**Задачи (строго по методичке, стр. 11):**
1.  Провести анализ предметной области [Ваша сфера].
2.  Спроектировать базу данных (ER-диаграмма).
3.  Разработать интерфейс и серверную часть с использованием [Ваш стек].
4.  Реализовать модуль [Ваша «Фишка» из ведомости].
5.  Провести тестирование.

#### Блок Г: Глава 1 (Анализ аналогов)
Задание на дом: Найти 3 конкурента вашей темы.
*   *Пример для Орловой (Прокат инвентаря):* Найти сайты проката лыж. Сделать скриншоты. Написать, чего у них НЕТ (например, таймера стоимости в реальном времени), чтобы обосновать свою разработку.

### 3. Результат семинара (Output)
К концу 3-й пары каждый студент отправляет преподавателю (или заливает в репозиторий в папку `/docs`) файл `Draft_PZ.docx`, содержащий:
1.  Титульный лист (по шаблону из стр. 21).
2.  Написанное Введение.
3.  Скриншот SonarCloud с рейтингом ("A" или "B").
4.  Ссылку на рабочий прототип на хостинге.

***

# FORMAT: NOTEBOOKLM_PROMPT (Сценарий для генерации лекции/презентации)

**Instruction for the User:** Copy the block below into Google NotebookLM. Upload the two PDF files provided (Methodology and Topics).

```text
Act as the Head of the Methodological Department of Applied Informatics (Year 2026).
Based on the uploaded "Methodological Instructions" and "Topic Distribution List (Group 202)", create a detailed slide deck outline for a seminar titled "Coursework Defense Preparation: Code, Security, and Documentation".

Target Audience: 4th-year students (SPO).
Tone: Professional, urgent, strictly compliant with Russian academic standards.

Directives & Constraints:
1. NO paid tools. Suggest ONLY: VS Code, Penpot, Beget (Free Hosting), PythonAnywhere, SonarCloud, GitHub.
2. Specifically address the "Features" (Фишки) listed in the Topic Distribution PDF.
3. Structure the output as 3 distinct Seminar Blocks.

Deep Research Questions to answer in the slides:
1. Analyze the specific "Competencies" (PK 9.1 - PK 9.10) from the Methodology PDF. How does connecting a GitHub repo to SonarCloud prove PK 9.5 (Testing)?
2. Extract the exact structure of the "Introduction" (Введение) from pages 9-11 of the Methodology PDF. Create a "Fill-in-the-blanks" template for students.
3. Using the "Topic Distribution" PDF, select 3 distinct students (e.g., Agapov, Belozertseva, Votintsev) and generate a specific "Architecture Validation Question" for each of their unique "Features".
4. Explain the difference between "Object" and "Subject" of research based on the examples in the Methodology PDF (Page 10-11).

Output Format for the Presentation Plan:
- Slide Title
- Key Visual (Description of diagram/screenshot)
- Core Content (Bullet points)
- Speaker Notes (Direct address to students, e.g., "Ivanov, pay attention to...")

Special Requirement:
Create a slide specifically for "Common Pitfalls" based on the Methodology PDF (e.g., volume of the report, prohibited formatting errors from Section 5).
```
