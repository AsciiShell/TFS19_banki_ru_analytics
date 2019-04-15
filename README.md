В виде идеи:
Предсказывать по тексту отзыва и его оценке является ли он фейковым (тоесть преподносит банк или принижает его не заслужено) или он честный отзыв. 

### 0. Разобратся в структуре файлов (все) (дедлайн - 8.04)
  Описание данных лежит в файле data_description
### 1. Препроцессинг данных (Артём, Никита).
1. Удаление неинформативных слов
2. Токениазация
3. Лемматизация 
4. Эмбединги 
Пункты 1-3 уже реализованы в данных, поэтому основной поинт препроцессинга - это построение эмбедингов, в наибольшей степени подходящих для моделей из пункта 3 (эксперименты с моделями); с этой целью эмбединги будут сроиться возможно разные (для каждой модели), кроме того, для построения новых эмбедингов, возможно, нужно будет обращаться к пунктам 1-3 и делать там что-то уже другое.
#### 1.a Построение хоть каких-нибудь эмбедингов, чтобы запустить демку, потом будем дорабатывать (дедлайн - 14.04)
#### 1.b Построение нормальных эмбедингов (наиболее адекватные для задачи, дообученные, или обученные самостоятельно) (дедлайн - 22.04)
UPD: прикреплен файл banki ru, в нем реализация простых эмбедингов из fasttext и csv-файлик, там результаты работы алгоритма кластеризации по 5 банкам.
#### 2. Поиск тематик (Лев, Никита, Артем)
  Разбиение сообщения по темам: карты, кредиты, депозиты, страховки и т.д.
  
  A:С помощью ключевых слов: подобрать темы -> подобрать базовые опорные слова -> расширить тематики за счет словарей синонимов или других штук (например, https://wordstat.yandex.ru/) -> кластеризовать данные.
 
  Б: Если получится шаг А, то попытатся построить более продвинутую модель -> найти в кластерах ярких представителей тематик -> потом через Baf of Words или embedding сделать semi-supervised clustering.
  
  Тестируем работу с LDA моделью.
  
  #### 2.a Попробовать простые алгоритмы кластеризации, поварьировать параметры, чтобы получались хоть какие-то классы (дедлайн - 14.04)
  #### 2.b Построить адекватные кластеры, из которых можно заключить, о чем этот кластер, применить метрики оценки кластеризации, улучшить скор по сравнению с baseline (демка) (дедлайн - 22.04)
  UPD: прикреплен файл banki ru, в нем реализация DBSCAN с параметрами, ориентированными примерно на 5 классов,и csv-файлик, там результаты работы алгоритма кластеризации по 5 банкам.
  #### 3. Построение моделей семантического анализа и эксперименты с ними (Артём + Никита)

Построить на основе оценок пользователей модель тональности сообщений.

Или построить модель тональностей на другом корпусе данных и попытаться его применить к моделям банки ру. Оценить тональность отзывов пользователей, сравнить с выставляемми оценками.

Архитектуры:
1. cnn
2. rnn
3. birnn
4. cnn+rnn / birnn
5. другие сети (сиамские какие-нибудь)
6. другие алогоритмы (вдруг сработает)
7. state-of-the-art в области semantic analysis

C каждой архитектурой проводятся эксперименты и попытки улучшить скор.

UPD: подгружен файл rusentiment_elmo, в котором импортится модель, которую будем использовать для определения тональности сообщений
#### 3.a Сделать модель, которая может хотя бы приблизительно предсказывать тональность (дедлайн - 14.04)
#### 3.b Если нужно, поменять модель, чтобы улучшить скор (дедлайн - 22.04)

### 4. Подготовка аналитики (Все)
  Создание красивых тыкабельных графиков и извлечение возможных удивительных фактов (дедлайн - 22.04)
  
