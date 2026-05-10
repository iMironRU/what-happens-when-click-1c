# Что happens когда я кликаю по ярлыку 1С

Технический лонгрид в духе [what-happens-when](https://github.com/alex/what-happens-when) Алекса Гейнора, но про 1С.

**Аудитория:** начинающие разработчики 1С и разработчики, переходящие с других платформ (Java, C#, Node.js).

**Рамки и допущения:**
- Основной маршрут — Windows-клиент в доменной среде
- Linux/macOS/мобильный/веб-клиент упоминается как отклонение
- Платформа 8.3 актуального релиза
- Внешнее соединение, COM-коннектор и фоновые задания — только упоминаем

---

## Содержание

### [Часть 0. Базовые понятия](chapters/00_bazovye-ponyatiya/00-01_konfiguraciya-i-infobaza.md)

- [0.1. Конфигурация и информационная база — это разные вещи](chapters/00_bazovye-ponyatiya/00-01_konfiguraciya-i-infobaza.md)
- [0.2. Два режима работы платформы: «Предприятие» и «Конфигуратор»](chapters/00_bazovye-ponyatiya/00-02_dva-rezhima.md)
- [0.3. Откуда берутся информационные базы](chapters/00_bazovye-ponyatiya/00-03_otkuda-infobazy.md)
- [0.4. Где живёт код конфигурации (и почему именно там)](chapters/00_bazovye-ponyatiya/00-04_gde-zhivyot-kod.md)
- [0.5. Как устроены объекты конфигурации: уровни наследования и событийная модель](chapters/00_bazovye-ponyatiya/00-05_obekty-konfiguracii.md)
- [0.6. Что значит «указать путь к информационной базе»](chapters/00_bazovye-ponyatiya/00-06_put-k-infobaze.md)
- [0.7. Расширения конфигурации — современный способ дорабатывать чужое решение](chapters/00_bazovye-ponyatiya/00-07_itog.md)

---

### [Часть I. До запуска: что уже есть в системе](chapters/01_do-zapuska/01-01_chto-na-diske.md)

- [1.1. Что лежит на диске после установки платформы](chapters/01_do-zapuska/01-01_chto-na-diske.md)
- [1.2. Что ещё установлено рядом с платформой](chapters/01_do-zapuska/01-02_chto-eshche-ustanovleno.md)
- [1.3. Ярлык на рабочем столе и что в нём записано](chapters/01_do-zapuska/01-03_yarlyk.md)
- [1.4. Что происходит, когда пользователь щёлкает по ярлыку](chapters/01_do-zapuska/01-04_zapusk-processa.md)
- [1.5. Что происходит на стороне ОС после успешного CreateProcess](chapters/01_do-zapuska/01-05_itog.md)

---

### [Часть II. Лаунчер `1cestart.exe`](chapters/02_launcher/02-01_zachem-launcher.md)

- [2.1. Что делает лаунчер и почему он вообще существует](chapters/02_launcher/02-01_zachem-launcher.md)
- [2.2. Что лаунчер делает первым делом](chapters/02_launcher/02-02_pervye-shagi.md)
- [2.3. Чтение конфигурационных файлов](chapters/02_launcher/02-03_chtenie-konfigfajlov.md)
- [2.4. Сборка списка информационных баз](chapters/02_launcher/02-04_spisok-baz.md)
- [2.5. Окно выбора базы и выбор пользователя](chapters/02_launcher/02-05_okno-vybora.md)
- [2.6. Какую версию платформы запускать](chapters/02_launcher/02-06_versiya-platformy.md)
- [2.7. Автоматическая загрузка недостающей версии](chapters/02_launcher/02-07_avtozagruzka.md)
- [2.8. Какой клиент запускать: тонкий, толстый, веб](chapters/02_launcher/02-08_vybor-klienta.md)
- [2.9. Формирование командной строки и запуск целевого клиента](chapters/02_launcher/02-09_zapusk-klienta.md)
- [2.10. Что мы имеем к концу работы лаунчера](chapters/02_launcher/02-10_itog.md)

---

### [Часть III. Сетевой путь до сервера](chapters/03_setevoy-put/03-01_chto-znaet-klient.md)

- [3.1. Что клиент знает к этому моменту](chapters/03_setevoy-put/03-01_chto-znaet-klient.md)
- [3.2. Разрешение имени хоста: DNS](chapters/03_setevoy-put/03-02_dns.md)
- [3.3. Установка TCP-соединения](chapters/03_setevoy-put/03-03_tcp.md)
- [3.4. Особый путь для веб-варианта: HTTP, TLS, прокси](chapters/03_setevoy-put/03-04_web-variant.md)
- [3.5. Что мы имеем к концу сетевого пути](chapters/03_setevoy-put/03-05_itog.md)

---

### [Часть IV. Подключение к информационной базе](chapters/04_podklyuchenie/04-01_fajlovaya-baza.md)

- [4.1. Файловая база: всё в одном процессе](chapters/04_podklyuchenie/04-01_fajlovaya-baza.md)
- [4.2. Клиент-серверная база: цепочка ragent → rmngr → rphost](chapters/04_podklyuchenie/04-02_klient-server.md)
- [4.3. Топологии развёртывания: кто на каком хосте живёт](chapters/04_podklyuchenie/04-03_topologii.md)
- [4.4. Подключение rphost к СУБД](chapters/04_podklyuchenie/04-04_rphost-subd.md)
- [4.5. Веб-публикация: три способа](chapters/04_podklyuchenie/04-05_web-publikaciya.md)
- [4.6. Согласование версий клиента и сервера](chapters/04_podklyuchenie/04-06_versii.md)
- [4.7. Что мы имеем после успешного подключения](chapters/04_podklyuchenie/04-07_posle-podklyucheniya.md)
- [4.8. Практический разворот: как от строки подключения дойти до физической базы](chapters/04_podklyuchenie/04-08_itog.md)

---

### [Часть V. Идентификация и авторизация](chapters/05_identifikaciya/05-01_autentifikaciya.md)

- [5.1. Аутентификация пользователя](chapters/05_identifikaciya/05-01_autentifikaciya.md)
- [5.2. Где хранятся пользователи и хеши паролей](chapters/05_identifikaciya/05-02_gde-polzovateli.md)
- [5.3. Параметры сеанса](chapters/05_identifikaciya/05-03_parametry-seansa.md)
- [5.4. Лицензирование: общая картина](chapters/05_identifikaciya/05-04_licenzirovanie.md)
- [5.5. Проверка серверной лицензии](chapters/05_identifikaciya/05-05_licenziya-servera.md)
- [5.6. Поиск клиентской лицензии](chapters/05_identifikaciya/05-06_licenziya-klienta.md)
- [5.7. Проверка комплектации: базовая, ПРОФ, КОРП](chapters/05_identifikaciya/05-07_komplektaciya.md)
- [5.8. Что мы имеем после успешной авторизации](chapters/05_identifikaciya/05-08_itog.md)

---

### [Часть VI. Подготовка прикладного решения к работе](chapters/06_podgotovka-resheniya/06-01_zagruzka-metadannyh.md)

- [6.1. Загрузка метаданных конфигурации в rphost](chapters/06_podgotovka-resheniya/06-01_zagruzka-metadannyh.md)
- [6.2. Применение расширений конфигурации](chapters/06_podgotovka-resheniya/06-02_rasshireniya.md)
- [6.3. Расчёт прав пользователя](chapters/06_podgotovka-resheniya/06-03_prava-polzovatelya.md)
- [6.4. Проверка права на запуск выбранного типа клиента](chapters/06_podgotovka-resheniya/06-04_pravo-na-zapusk.md)
- [6.5. Что мы имеем после подготовки прикладного решения](chapters/06_podgotovka-resheniya/06-05_itog.md)

---

### [Часть VII. Компиляция модулей](chapters/07_kompilyaciya/07-01_model-ispolneniya.md)

- [7.1. Модель исполнения: байт-код стек-машины](chapters/07_kompilyaciya/07-01_model-ispolneniya.md)
- [7.2. Контексты компиляции: серверный и клиентский](chapters/07_kompilyaciya/07-02_konteksty.md)
- [7.3. Что обязательно компилируется при старте](chapters/07_kompilyaciya/07-03_chto-kompiliruetsya.md)
- [7.4. Что мы имеем после компиляции](chapters/07_kompilyaciya/07-04_itog.md)

---

### [Часть VIII. Старт сеанса и построение интерфейса](chapters/08_start-seansa/08-01_sozdanie-seansa.md)

- [8.1. Создание сеанса в кластере](chapters/08_start-seansa/08-01_sozdanie-seansa.md)
- [8.2. Обработчики ПередНачаломРаботыСистемы и ПриНачалеРаботыСистемы](chapters/08_start-seansa/08-02_handlery-nachala.md)
- [8.3. Подсистемы конфигурации](chapters/08_start-seansa/08-03_podsistemy.md)
- [8.4. Построение главного окна](chapters/08_start-seansa/08-04_glavnoe-okno.md)
- [8.5. Движок управляемых форм](chapters/08_start-seansa/08-05_upravlyaemye-formy.md)
- [8.6. Рендеринг по платформам: один декларативный, разные реализации](chapters/08_start-seansa/08-06_rendering.md)
- [8.7. Открытие рабочего стола и передача управления пользователю](chapters/08_start-seansa/08-07_otkrytie-rabochego-stola.md)
- [8.8. Что мы прошли в восьмой части](chapters/08_start-seansa/08-08_itog.md)

---

### [Часть IX. Сквозные темы](chapters/09_skvoznye-temy/09-01_oshibki-diagnostika.md)

- [9.1. Ошибки и общие принципы диагностики](chapters/09_skvoznye-temy/09-01_oshibki-diagnostika.md)
- [9.2. Логи и инструменты диагностики](chapters/09_skvoznye-temy/09-02_logi-instrumenty.md)
- [9.3. Кеши на разных уровнях](chapters/09_skvoznye-temy/09-03_keshi.md)
- [9.4. Где в 1С своё, а где — мировые стандарты](chapters/09_skvoznye-temy/09-04_svoe-i-standarty.md)
- [9.5. Что мы прошли в девятой части](chapters/09_skvoznye-temy/09-05_itog.md)

---

### [Приложения](chapters/10_appendices/10-01_glossariy.md)

- [Приложение A. Глоссарий терминов](chapters/10_appendices/10-01_glossariy.md)
- [Приложение B. Внешние ссылки для углубления](chapters/10_appendices/10-02_ssylki.md)
- [Приложение C. Шпаргалка «куда смотреть, если не запускается»](chapters/10_appendices/10-03_shpargalka.md)
- [Финальное напутствие](chapters/10_appendices/10-04_itog.md)
