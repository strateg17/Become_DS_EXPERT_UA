---
description: >-
  Cross-Industry Standard Process for the development of Machine Learning
  applications with Quality assurance methodology (CRISP-ML(Q))
---

# CRISP-ML(Q)

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>Machine Learning Development Life Cycle Process.</p></figcaption></figure>

В цілому процес CRISP-ML(Q) можна поділити на шість етапів:

1. Розуміння постановки бізнес завдання та даних (Business and Data Understanding)
2. Підготовка даних(Data Engineering / Data Preparation)
3. Моделювання (Machine Learning Model Engineering)
4. Тестування (Quality Assurance for Machine Learning Applications)
5. Дослідно-промислова експлуатація (Deployment)
6. Моніторинг та технічна підтримка (Monitoring and Maintenance).

Для кожної фази моделі процесу підхід до забезпечення якості в CRISP-ML(Q) вимагає визначення вимог і обмежень (наприклад продуктивність, вимоги до якості даних, стійкість моделі тощо), визначення конкретних завдань (наприклад, вибір алгоритму ML, навчання моделі тощо), специфікація ризиків, які можуть негативно вплинути на ефективність та успіх ML моделі (наприклад зміщення, перенавчання, складно відтворити результати), методи забезпечення якості для зменшення ризиків (наприклад, перехресна перевірка, документування процесів та результатів тощо).

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption><p><a href="https://arxiv.org/pdf/2003.05155.pdf">CRISP-ML(Q)</a> підхід для забезпечення якості на кожному із шести етапів </p></figcaption></figure>

### Розуміння потреб бізнесу та даних (Business and Data Understanding) <a href="#business-and-data-understanding" id="business-and-data-understanding"></a>

Developing machine learning applications starts with identifying the scope of the ML application, the success criteria, and a data quality verification. The goal of this first phase is to ensure the feasibility of the project.

We gather success criteria along with business, machine learning, and economic success criteria during this phase. These criteria are required to be measurable. Therefore, defining clear and measurable Key Performance Indicators (KPI) such as _“time savings per user and session”_ is required. A helpful approach is to define a [non-ML heuristic benchmark](https://learning.oreilly.com/library/view/machine-learning-design/9781098115777/ch08.html) to communicate the impact of machine learning tasks with the business stakeholders.

Confirming the feasibility before setting up the ML project is a best practice in an industrial setting. Applying the [Machine Learning Canvas](https://www.louisdorard.com/machine-learning-canvas) framework would be a structured way to perform this task. The ML Canvas guides through the prediction and learning phases of the ML application. In addition, it enables all stakeholders to specify data availability, regulatory constraints, and application requirements such as robustness, scalability, explainability, and resource demand.

As data guides the process, data collection and data quality verification are essential to achieving business goals. Therefore, one crucial requirement is the documentation of the statistical properties of data and the data generating process. Similarly, data requirements should be stated and documented as well, as it becomes a foundation for data quality assurance during the operational phase of the ML project.

### Підготовка даних (Data Engineering \\( Data Preparation) <a href="#data-engineering-data-preparation" id="data-engineering-data-preparation"></a>

The second phase of the CRISP-ML(Q) process model aims to prepare data for the following modeling phase. _Data selection, data cleaning, feature engineering,_ and _data standardization_ tasks are performed during this phase.

We identify valuable and necessary features for future model training by using either _filter methods, wrapper methods_, or _embedded methods_ for data selection. Furthermore, we select data by discarding samples that do not satisfy data quality requirements. At this point, we also might tackle the problem of unbalanced classes by applying _over-sampling_ or _under-sampling_ strategies.

The data cleaning task implies that we perform error detection and error correction steps for the available data. Adding [unit testing for data](https://ssc.io/pdf/p1993-schelter.pdf) will mitigate the risk of error propagation to the next phase. Depending on the machine learning task, we might need to perform feature engineering and data augmentation activities. For example, such methods include one-hot encoding, clustering, or discretization of continuous attributes.

The data standardization task denotes the process of unifying the ML tools’ input data to avoid the risk of erroneous data. Finally, the normalization task will mitigate the risk of bias to features on larger scales. We build data and input data transformation pipelines for data pre-processing and feature creation to ensure the ML application’s reproducibility during this phase.

### Моделювання (Machine Learning Model Engineering)

The modeling phase is the ML-specific part of the process. This phase aims to specify one or several machine learning models to be deployed in the production. The translation to the ML task depends on the business problem that we are trying to solve. Constraints and requirements from the _Business and Data Understanding_ phase will shape this phase. For example, the application domain’s [model assessment metrics](https://arxiv.org/pdf/1906.10742.pdf) might include _performance metrics, robustness, fairness, scalability, interpretability, model complexity degree,_ and _model resource demand_. We should adjust the importance of each of these metrics according to the use case.

Generally, the modeling phase includes _model selection, model specialization,_ and _model training_ tasks. Additionally, depending on the application, we might use a pre-trained model, compress the model, or apply ensemble learning methods to get the final ML model.

One main complaint about machine learning projects is the lack of reproducibility. Therefore we should ensure that the method and the results of the modeling phase are reproducible by collecting the model training method’s metadata. Typically we collect the following metadata: algorithm, training, validation and testing data set, hyper-parameters, and runtime environment description. The result reproducibility assumes the validation of the model’s mean performance on different random seeds. Following best practices, documenting trained models increases the transparency and explainability in ML projects. A helpful framework here is the [“Model Cards Toolkit”](https://arxiv.org/pdf/1810.03993.pdf).

Many phases in ML development are iterative. Sometimes, we might need to review the business goals, KPIs, and available data from the previous steps to adjust the outcomes of the ML model results.

Finally, we package the ML workflow in a pipeline to create repeatable model training during the modeling phase.

### Оцінювання моделей (Evaluating Machine Learning Models) <a href="#evaluating-machine-learning-models" id="evaluating-machine-learning-models"></a>

Отже, навчання моделі супроводжується етапом оцінювання моделі, також відомим як офлайн-тестування. Під час цього етапу продуктивність навченої моделі потрібно перевірити на тестовому наборі даних. Крім того, надійність моделі слід оцінювати за допомогою шумних або неправильних вхідних даних. Також гарною практикою є розробка зрозумілої (explainable) моделі ML, щоб забезпечити довіру, відповідати нормативним вимогам і керувати людьми у прийнятті рішень за допомогою ML.

Нарешті, рішення про розгортання моделі має прийматися автоматично на основі критеріїв успіху або вручну експертами домену та ML. Подібно до етапу моделювання, усі результати даного етапу оцінювання необхідно документувати.

### Розгортання моделі (Deployment) <a href="#deployment" id="deployment"></a>

Розгортання моделі ML означає процес інтеграції моделі ML в існуючу програмну систему. Після успішного проходження етапу оцінки в життєвому циклі розробки ML модель випускається для розгортання в (перед) виробничому середовищі (test env). Підходи до розгортання визначаються на першому етапі життєвого циклу розробки ML. Вони відрізнятимуться залежно від сценарію використання та режиму навчання та прогнозування, пакетного (batch) або онлайнового. Наприклад, розгортання моделі ML означає надання її прогностичної функціональності у вигляді інтерактивних інформаційних панелей і попередньо обчислених прогнозів, упаковку моделі ML як плагіна в архітектурі програмного забезпечення [мікроядра ](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/ch03.html)або кінцевої точки веб-сервісу в розподіленій системі.

Розгортання моделі ML включає вирішення таких завдань: визначення апаратного забезпечення, оцінка моделі у виробничому середовищі (онлайн-тестування, наприклад, A/B-тестування), тестування зручності використання, забезпечення резервного плану для збоїв моделі та налаштування стратегію розгортання, щоб поступово розгортати нову модель (наприклад, розгортання canary або green/blue).

### Моніторинг та технічна підтримка (Monitoring and Maintenance) <a href="#monitoring-and-maintenance" id="monitoring-and-maintenance"></a>

Коли модель ML запущено, важливо стежити за її продуктивністю та підтримувати її. Коли модель ML працює на реальних даних, основним ризиком є ефект «застарівання моделі», коли продуктивність моделі падає з часом, коли вона починає працювати з даними, які не були присутні у тренувальному наборі. Крім того, на продуктивність моделі впливає продуктивність апаратного забезпечення та наявний стек програмного забезпечення. Таким чином, найкращим способом запобігання падінню продуктивності моделі є виконання завдання моніторингу, коли продуктивність моделі постійно оцінюється, щоб вирішити, чи потрібно модель перенавчати. Цей процес відомий як шаблон неперервної оцінки моделі ([Continued Model Evaluation pattern](https://www.oreilly.com/library/view/machine-learning-design/9781098115777/)). Висновки із моніторингу призводить до оновлення моделі ML. Окрім моніторингу за перенавчанням моделі великий вплив має також бізнес-бачення та зміна стратегічних завдань.

### Висновок <a href="#conclusion" id="conclusion"></a>

Розгортання моделей передбачає багато взаємодіючих компонентів і процесів. У цій статті було розглянуто модель життєвого циклу розробки CRISP-ML(Q). Загалом, CRISP-ML(Q) — це систематична модель процесу для розробки програмного забезпечення для машинного навчання, яка створює усвідомлення можливих ризиків і наголошує на забезпеченні якості, щоб зменшити ці ризики для забезпечення успіху проекту ML. У наведеній нижче таблиці підсумовано основні етапи CRISP-ML(Q) і відповідні завдання:

| CRISP-ML(Q) етапи:                 | Завдання які вирішуються                                                                                                                                                                                                                                                                                                                                                                                                        |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Розуміння бізнес процесів та даних | <ul><li> Визначення бізнес цілей та завдань</li><li>Трансформація бізнес вимог у технічне завдання</li><li>Збір та верифікація даних</li><li>Оцінка реалізації проекту</li><li>Перевірка концепції (ProofOfConcept)</li></ul>                                                                                                                                                                                                   |
| Підготовка даних                   | <ul><li>Вибір факторів</li><li>Вибір джерел даних</li><li>Збалансування класів</li><li>Очистка даних (зменшення шуму, заповнення пропусків)</li><li>Генерація нових факторів</li><li>Збагачення даних</li><li>Стандартизація та нормалізація даних</li></ul>                                                                                                                                                                    |
| Моделювання                        | <ul><li>Визначення метрик оцінки якості моделі</li><li>Вибір ML алгоритмів (baseline)</li><li>Тюніг моделі із застосуванням предметної області </li><li>Навчання моделі</li><li>Опціонально: застосування trainsfer - learning (з використанням попередньо підготовлених моделей)</li><li>Стискання моделей</li><li>Створення ансамблів моделей</li><li>Документування моделей та результатів експериментів</li></ul>           |
| Оцінка результатів                 | <ul><li> Оцінка точності моделей</li><li> Визначення надійності </li><li>Покращення пояснювальності  (explainability) моделі</li><li>Прийняття рішення  про розгортання</li><li>Документування результатів</li></ul>                                                                                                                                                                                                            |
| Розгортання моделі                 | <ul><li>Оцінка розгорнутої моделі</li><li>Забезпечте прийняття користувачами та зручність використання</li><li>Визначення порядку управління</li><li>Розгортання відповідно до обраної стратегії (A/B тестування, багаторукі бандити (multi-armed bandits)</li></ul>                                                                                                                                                            |
| Моніторинг та технічна підтримка   | <ul><li>Відстеження ефективності і дієвості прогнозів моделі</li><li>Порівняння з попередньо визначеними критеріями успіху (порогові значення)</li><li>Перенавчання моделі, якщо потрібно</li><li>Збереження нових даних</li><li>Виконання розмітки нових даних</li><li>Повторіть завдання з етапів <em>Розробка моделі</em> та <em>Оцінка моделі</em></li><li>Безперервна інтеграція, навчання та розгортання моделі</li></ul> |
