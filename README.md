# Оценка уровня Writing по критериям ЕГЭ

 Куратор: Вольф Елена  
 Студенты: Бурлова Альбина, Андрейко Максим, Василенко Павел.

 Датасет:  
 https://docs.google.com/spreadsheets/d/1m0mc1H7ULIZ2HEkT4dha_XRmRjt0gWJ8aht_GJ2lxfw/edit#gid=0

 Модели:
- [Fine-tuned BERT](https://disk.yandex.ru/d/5MBlWdXOSiJWuw)
- [FLAN-T5](https://disk.yandex.ru/d/m8rbGP77RMLoBg)

 Streamlit-приложение:  
 https://app-for-autograde-eng-letter.streamlit.app 

 Telegram bot:  
 https://t.me/letter_checker_bot


 Создан сервис (API) и подключенный к нему UI (streamlit-приложение и телеграм-бот), которые оценивабт ответы к заданиям части Writing в ЕГЭ по английскому языку, выставляя баллы по критериям ЕГЭ. Всего 2 задания разного формата, для которых необходимо предоставить письменный ответ в соответствии с критериями задания. 

- Задание 1: «Электронное письмо личного характера».  
Необходимо ответить на вопросы в письме и задать свои адресанту. Всего 3 критерия, выставляется от 0 до 2 баллов по каждому критерию. Максимальный балл — 6.
- Задание 2: «Эссе с элементами рассуждения на основе таблиц/диаграмм».  
Анализ данных по указанной теме и изложение собственных мыслей. Всего 5 критериев, выставляется от 0 до 3 баллов с 1 по 4 критерий, за 5 критерий - от 0 до 2 баллов. Максимальный балл — 14. 

 Каждому заданию соответствуют собственные критерии. Подробно расписанные критерии и примеры заданий: https://disk.yandex.ru/d/HytFA5aiuGiO_g

 
 # Архитектура сервиса
 ![Архитектура сервиса](images/service_diagram.png)

Организация проекта
------------

    ├── LICENSE
    ├── README.md                                <- Описание проекта
    ├── data
    │   ├── interim                              <- Intermediate data that has been transformed.
    │   ├── processed                            <- The final, canonical data sets for modeling.
    │   └── raw                                  <- The original, immutable data dump.
    │
    │
    ├── notebooks                                <- Jupyter-ноутбуки. Правила наименования: номер (для учета порядка),
    │                                               инициалы автора, и через `-` краткое название, например
    │                                               `1.0-jqp-initial-data-exploration`.
    │
    │
    ├── production                               <- Git-субмодули с исходным кодом сервисов продуктивизации
    │   ├── autograde_api                        <- API-сервис для обработки запросов
    │   ├── EGE-Writing-Autograde-Bot            <- Телеграм-бот для проверки писем
    │   └── Streamli-for-autograde-eng-letter    <- Web-UI для использования модели, и EDA
    │
    │ 
    ├── src                                      <- Исходный код
    │   ├── __init__.py                          <- Для инициализации папки как модуля
    │   │
    │   └── data                                 <- Код для парсинга, чтения, загрузки данных
    │       ├── parser_email_cloudtext.py        <- Парсер писем с ресурса cloudtext
    │       ├── parser_emails_reshu_ege.py       <- Парсер писем с ресурса РЕШУ ЕГЭ
    │       └──read_raw_data.py                  <- Чтение данных из gsheet
    │
    └── tox.ini                                   <- tox файл настроек для запуска tox; см. tox.readthedocs.io


--------
