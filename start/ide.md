---
description: >-
  IDE (interactive development environment) - інтерактивне середовище розробки,
  мабуть один із перших інструментів, які варто встановити починаючому
  розробнику для ефективної роботи.
---

# 📺 IDE

### **Налаштування IDE**

Перелік IDE на які ми орієнтуємося - це VSCode (мабуть найзручніший для WSL), PyCharm, Atom, Sublim, vim та комібнацію середовищ Windows, Windows + WSL, Linux, MacOS.

1.  **VSCode** - при роботі напряму на Linux, Windows та MacOS особливостей не помічено. Чудово працює із поєднанням WSL2 or WSL + Windows за рахунок розширень. Можна запустити проект через саму IDE або через термінал WSL:

    ```bash
    # open the current directory
    code .

    # open another directory
    code ~/workspace/project

    # open vscode without specifying a project
    code
    ```

    Якщо через explorer, то проект має бути на змонтованій WSL машині за адресою, яку можна відкрити у провіднику windows: `\\wsl.localhost\Ubuntu\home\{user}` Extensions:

    * Azure Account
    * Azure Machine Learning
    * Azure Machine Learning - Remote
    * Dev Containers - запуск коду одразу у Docker контейнерах
    * isort - рефакторинг імпортів
    * Jupyter - зозширення для роботи із ноутбуками
    * Jupyter Notebook Renderers - розширення необхідне для рендерингу результатів роботи бібліотек plotly, altair etc
    * Pylance - максимально необхідне розширення, яке має допомогти автоматично генерувати докстрінги для нас. Єдине, що потрібно зауважити - це нам потрібен google-style.
    * Python - підтримує усі додатокові опції для рефакторингу коду.
    * Remote - SSH - для розробки на віддалених середовищах.
    * WSL - для організації роботи через комбінацію Windows + WSL.
2.  **Atom** - При роботі напряму на Linux, Windows та MacOS особливостей не помічено. Проте є певні особливості для Windows + WSL. Проект легко запустити через IDE expolorer. Якщо є бажання налаштувати підхід як у VSCode через CLI, тоді потрібно також внести зміни у файл нашаштування, який можна викачати вже готовий.

    ```bash
    # download the atom script
    sudo curl -o /usr/local/bin/atom     https://gist.githubusercontent.com/voracious/1a1473ea36906c8f6830a17701e7fd21/raw/b8c697ca810022f2fc4be9eef3f72a54c6073b7e/atom.sh

    # make it executable
    sudo chmod +x /usr/local/bin/atom
    ```

    Тепер доступні команди як і для vscode:

    ```bash
    # open the current directory
    atom .

    # open another directory
    atom ~/workspace/project

    # open atom without specifying a project
    atom
    ```

    Слід зауважити, що файл налаштування містить наступний скрипт:

    ```bash
    #!/bin/bash

    # only convert the path if one is provided
    if [ ! -z $1 ]
    then
      linuxPath="$(realpath $1)"
      windowsPath="$(wslpath -w $linuxPath)"
    fi

    # avoid the UNC path warning
    cd /mnt/c/Windows

    # launch atom on Windows
    cmd.exe /c "atom $windowsPath"
    ```

    Корисні та необхідні extensions: [20 ATOM Plug-ins For Python Development](https://medium.com/issuehunt/20-atom-plug-ins-for-python-development-d6b10f8fa33e).
3. **PyCharm** - При роботі напряму на Linux, Windows та MacOS особливостей не помічено. При роботі із комбінацією Window + WSL потрібно буде виконати певні дії. Зокрема відриття проекту відбувається через внутрішній explorer за адресою: `\\wsl.localhost\Ubuntu\home\{user}` Також варто скористатися локальним інтерпритатором для WSL ([Configure an interpreter using WSL](https://www.jetbrains.com/help/pycharm/using-wsl-as-a-remote-interpreter.html)). Extensions: Не бачу якогось прямо супер переліку. Все доволі стандартно і за вибором, оскільки pycharm по дефолту націлений на python. Тому тут більшіть всього необхідного вже є з коробки.
4.  **Sublime** - у даному випадку виділяємо навіть два рішення, серед яких sublime text & sublime merge: Sublime text - для редагування коду. По результатам експериментів нормально працює на Linux, Windows та MacOS особливостей не помічено. Для роботи через Windows + WSL потрібно просто відкрити проект: `\\wsl.localhost\Ubuntu\home\{user}` Extensions: [Setting Up Sublime Text 3 for Full Stack Python Development](https://realpython.com/setting-up-sublime-text-3-for-full-stack-python-development/). Тут потрібно буде погратися із налаштуваннями, адже багато чого потрібно прямо нарощувати під себе з нуля.

    4.1. **Sublime merge** - використовуємо для VCS, дуже зручне локальне рішення. Також прекрасно працює із нашими гілками, що відповідним чином протестовано. Проте потрібно працювати через прямий шлях на диску.

    4.2. **Vim** - конфігурація vim доволі проста і навряд буде використовуватися для розробки коду. Але у цьому і полягає його потужність, якщо є бажання, то можна перетворити його у повноцінну IDE. Для цього можна рекомендувати спочатку його встановити із налаштуванням опцій: [Set up Vim with clipboard on Ubuntu on WSL2](https://gist.github.com/necojackarc/02c3c81e1525bb5dc3561f378e921541). Після чого вже розширювати функціонал за допомогою різних плагінів: [VIM and Python – A Match Made in Heaven](https://realpython.com/vim-and-python-a-match-made-in-heaven/).
5. **Neovim** - більш розширене версія для любителів мінімалізму. Тут варіантів налаштування безліч. Але якщо тільки хочеться познайомитися і налаштувати всі деталі під себе, тоді краще використати ось тикий гайд: [Learn Neovim The Practical Way](https://alpha2phi.medium.com/learn-neovim-the-practical-way-8818fcf4830f). Він містить всі відповідні налаштування, які необхідно провести.
