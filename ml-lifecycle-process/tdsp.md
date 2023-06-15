---
description: >-
  Технологічний процес команди Data Science (TDSP) - це гнучка, ітеративна
  методологія роботи з даними, спрямована на ефективну розробку прогнозувальних
  аналітичних рішень та інтелектуальних додатків.
---

# TDSP

### Ключові компоненти TDSP <a href="#key-components-of-the-tdsp" id="key-components-of-the-tdsp"></a>

TDSP включає такі елементи:

* A **data science lifecycle** definition
* A **standardized project structure**
* **Infrastructure and resources** recommended for data science projects
* **Tools and utilities** recommended for project execution

### Життєвий цикл проекту Data science&#x20;

The Team Data Science Process (TDSP) provides a lifecycle to structure the development of your data science projects. The lifecycle outlines the full steps that successful projects follow.

This lifecycle has been designed for data science projects that ship as part of intelligent applications. These applications deploy machine learning or artificial intelligence models for predictive analytics. Exploratory data science projects or improvised analytics projects can also benefit from using this process. But in such cases some of the steps described may not be needed.

The lifecycle outlines the major stages that projects typically execute, often iteratively:

* **Business Understanding**
* **Data Acquisition and Understanding**
* **Modeling**
* **Deployment**

Here is a visual representation of the **Team Data Science Process lifecycle**.

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

The goals, tasks, and documentation artifacts for each stage of the lifecycle in TDSP are described in the [Team Data Science Process lifecycle](https://learn.microsoft.com/en-us/azure/architecture/data-science-process/lifecycle) topic. These tasks and artifacts are associated with project roles:

* Solution architect
* Project manager
* Data engineer
* Data scientist
* Application developer
* Project lead

The following diagram provides a grid view of the tasks (in blue) and artifacts (in green) associated with each stage of the lifecycle (on the horizontal axis) for these roles (on the vertical axis).

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

### Стандартизована структура проекту <a href="#standardized-project-structure" id="standardized-project-structure"></a>

Мати спільну структуру каталогів для всіх проектів і використання шаблонів для документів проекту спрощує пошук інформації про проекти для членів команди. Весь код і документи зберігаються у системі контролю версій (СКВ) такій як Git, TFS або Subversion для сприяння командній співпраці. Відстеження задач і функцій у системі відстеження проектів згідно з методологією Agile, такої як Jira, Rally або Azure DevOps, дозволяє ближче відстеження коду для окремих функціональностей. Таке відстеження також дозволяє командам отримувати кращі оцінки витрат. TDSP рекомендує створювати окремий репозиторій для кожного проекту у системі контролю версій для забезпечення контролю версій, захисту інформації та співпраці. Стандартизована структура для всіх проектів допомагає накопичувати інституційний досвід в усій організації.

Ми надаємо шаблони для структури каталогів і необхідних документів у стандартних розташуваннях. Ця структура каталогів організовує файли, які містять код для дослідження даних і вилучення ознак, а також записи ітерацій моделей. Ці шаблони полегшують розуміння роботи, виконаної іншими членами команди, і включення нових учасників до команд. Для відображення і оновлення документів використовуйте шаблони у форматі Markdown. Використовуйте шаблони, щоб надавати чек-листи з ключовими питаннями для кожного проекту, щоб переконатися, що проблема коректно визначена і що результати відповідають очікуваній якості. Приклади включають:

* Шаблон постановки задачі проекту, щоб задокументувати бізнес-проблему та обсяг проекту.
* Звіти про дані для задокументування структури та статистики вихідних даних.
* Звіти моделі для задокументування отриманих ознак.
* Метрики продуктивності моделі, такі як криві ROC або середньоквадратична помилка (MSE).

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

### Інфраструктура data science проекту <a href="#infrastructure-and-resources-for-data-science-projects" id="infrastructure-and-resources-for-data-science-projects"></a>

TDSP надає рекомендації щодо управління спільною аналітичною та зберіганою інфраструктурою, такою як:

* Хмарні файлові системи для зберігання наборів даних.
* Бази даних.
* Кластери великих даних (SQL або Spark).
* Сервіси машинного навчання.

Інфраструктура аналітики та зберігання, де зберігаються сирі та оброблені набори даних, може бути в хмарі або на власних серверах. Ця інфраструктура забезпечує відтворюваність аналізу. Вона також уникне дублювання, що може призвести до невідповідностей та непотрібних витрат на інфраструктуру. Надаються інструменти для розгортання спільних ресурсів, їх відстеження та забезпечення кожному члену команди безпечного з'єднання з цими ресурсами. Також є хорошою практикою, щоб учасники проекту створювали однорідне обчислювальне середовище. Різні члени команди можуть реплікувати та перевіряти експерименти.

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

### Інструменти реалізації <a href="#tools-and-utilities-for-project-execution" id="tools-and-utilities-for-project-execution"></a>

Впровадження процесів у більшості організацій є викликом. Інструменти, що надаються для впровадження процесу та життєвого циклу науки про дані, допомагають знизити бар'єри та підвищити послідовність їх використання. TDSP надає початковий набір інструментів і скриптів для швидкого впровадження TDSP в команді. Він також допомагає автоматизувати деякі загальні завдання у життєвому циклі науки про дані, такі як дослідження даних та базове моделювання. Існує чітка структура, яка дозволяє індивідуально внести спільні інструменти та утиліти до спільного репозиторію коду команди. Ці ресурси потім можуть бути використані іншими проектами в команді або організації. Microsoft надає широкий набір інструментів у Azure Machine Learning, що підтримують як відкритий код (Python, R, ONNX та популярні фреймворки для глибинного навчання), так і власні інструменти Microsoft (AutoML).
