---
description: >-
  Система контролю версій (GIT) є основним інструментом в розробці програмного
  забезпечення. GIT відстежує будь-які зміни, внесені в код, дозволяючи
  користувачу переглянути повну історію
---

# Git Basics

Серед інструментів контролю версій Git, який спочатку був створений Лінусом Торвальдсом, вважається майже стандартом серед програмістів (хоча не єдиним, наприклад, існує також Mercurial).

Існує два "варіанти" систем контролю версій: централізована та розподілена.

Централізована використовує один сервер, який відповідає за зберігання історії проекту. Користувач може "синхронізуватися" з останнім кодом та "відправляти" зміни на сервер (наприклад, Subversion).

Git є прикладом розподіленої системи контролю версій (далі - СКВ): користувачі, які "клонують" проект з "репозиторію", мають доступ до повної історії і стають рівноправними учасниками. Історія проекту стає деревом, яке легко розгалужувати, об'єднувати, ...

Більшість операцій з GIT-ом виконуються локально.&#x20;

![](https://lh6.googleusercontent.com/d5ZT824DnpIOTzK3WOA7oVudLbHObOqQkDrkzx\_RZmxerl55OhIGHiASKI4dNFeWnAR05uy2290o9DC2BTh5R9Kz367QyfZm21XhNc3uFRnEBg3G-X2aPIzW4p5-JoL9UZdW8VwTJD5d75riONO5W8ot=s2048)![](https://lh4.googleusercontent.com/Sx\_X0DYRT\_Mod\_bUE8XuO\_FGRWAx0VfoOHyEMz0nYtVVsZeVpAqaDvnMqSlhfosHnPixXxMv7J\_xWKlttauMZprR-OG3ZY6dvufmJOkz1XSHYcRy9PHq5ArH9p-53Opxo65nU9V4MhqjyOH\_4Zv3kXMi=s2048)

Git зберігає так звані "знімки" проекту (коміти). В той же час централізована система контролю версій зберегіє тільки зміни. Файли, які не змінювалися зберігаються прив'язку до попереднього "знімку" (snapshot) проекту, що описує останній збережений його стан коду.

<figure><img src="https://lh6.googleusercontent.com/4VyohiWpMo0f7377K_B_QWA99XYvBnt4ggubiJn9-9BiSW7IygSd2q8J42dO_srK3V7bzMVBW_fo64TlFuWlZHILzPlhx37tRW_mQXYJuWzZLWkDNJ-gB9LDRbTEwejc8onuC34MTVlAqfRH2715LcIB=s2048" alt=""><figcaption></figcaption></figure>

Файли в репозиторії можуть бути відстежуваними або не відстежуваними за допомогою Git. Якщо відстежуваний файл змінюється, його можна перемістити до області підготовки (staging area), і зміни, які були підготовлені, будуть використовуватися для створення нового коміту в репозиторії (знімку).

![](https://lh3.googleusercontent.com/IG2FgDsuc3ImNePBSuLRaqQ0TPwmkLRDDj000MloBAdAw5qWjFjjFINLlG5f\_2QcC6-MTgYMzN5DMxRJonu-rImnY1Dap7pnoY7GvfKrHaReyHp5RZN9lPja4LKAxidyuqVc1XT5HRVOr0IR20\_lc\_XR=s2048)![](https://lh3.googleusercontent.com/9x2S2iCJcGHjGBd4QHh-NAThmSKcYauN1uVA3JrEMsFmuiilFppDxAP8VVLJnukN6JeRcu-olic8jO5E\_enpV6\_cYhPahYOXdQyTVcTdVDPqpQ8rqnCLa6nKULbE5kykvVXufRqwG3exQL0Rf4SlUpuf=s2048)

Проект Git може бути настільки простим, як лінійна послідовність комітів на одному комп'ютері:

<figure><img src="https://lh6.googleusercontent.com/0PEFZFDP-nEPOXyZQjb0w6W6DqcCLLiiEeDIWr9YlUtGp_Q2W_ZviguYME-_NzODYOF9O5tvI10Xk5r-ivnggklwwdtX-plgqIVYoKbE3ZL6WG638oM4IycEVkoH2vSyLvozOv9kivQyvuRGVQzlaoCU=s2048" alt=""><figcaption></figcaption></figure>

Або деревом змін (гілок). Зверніть увагу, що різні користувачі можуть мати різні дерева!

<figure><img src="https://lh3.googleusercontent.com/1HRTqeKeHWWtZI0vJwk8M_zeGJ1BVsXrhPHHbok-O8PnK41uEkD8st0EWQsXU9hzLZw2LiZqnkGAjF-rA8T6lnRsR7cU2ZmDr3bgmfpexakAsKUJG6XYOl5wLjLOk7t8vosLgvDp_xsBepp8PM4oTwBS=s2048" alt=""><figcaption></figcaption></figure>

Мабуть найбільш правильним використанням GIT-у варто зазначити саме застосування командного рядка (CLI). Проте сьогодні можна знайти безліч окреми рішень із вже готовим графічним інтетфейсом, або навіть розширень до вашої улюбленої IDE.

![](https://lh4.googleusercontent.com/ezeVG\_VqWQcOqm1hmy14JZAm1dtEHVys-Ej30tTArtb6AllbY3I8WuIaGZkcVrYLNR1\_AQ7zwHCPVvXwY9gqEbUY-6MS82NR9xsy-V6A6cNtTqkNjAtfc0iKwf722hrNOc2qxpGqI74dg01JBCtXUgur=s2048)![](https://lh4.googleusercontent.com/iDkSDj2F1Ab1W44nNOSh5QKv9whDhV9JuV9Ip9Kfd2ECKeqlEyLbbiAyUHgsMGBmrtAPz\_B2cVf\_p-UxOyOCXIXQjktbnh1jYj37I4KfOsq-Kn-YldKLhncUJJiflQ0TtTFZ3X4f6QPR0MS3Ov1C\_O4G=s2048)

Найпоширеніший сценарій використання Git - це робота із віддаленим Git-хостингом, наприклад, GitHub, GitLab.

У цьому випадку хостований репозиторій виступає як "офіційна" копія проекту.

Більшість Git-хостингів пропонують ряд додаткових функцій, поза чистим Git-ом (наприклад, запити на об'єднання, розгалуження, дії, релізи і т.д.).&#x20;

Щоб встановити клієнт Git, потрібно дотримуватися наступних кроків:

1. Відвідати офіційний веб-сайт Git за адресою https://git-scm.com/.
2. Завантажте відповідний клієнт Git для вашої операційної системи (Windows, macOS, Linux) з розділу завантажень на веб-сайті.
3. Запустіть інсталятор та дотримуйтесь інструкцій на екрані, щоб завершити установку.
4.  Після встановлення Git відкрийте термінал або командний рядок, щоб перевірити установку. Введіть наступну команду:

    ```git
    git --version
    ```

    Ця команда відобразить встановлену версію Git, якщо встановлення пройшло успішно.

Після встановлення Git потрібно налаштувати вашу інформацію користувача. Ця інформація буде пов'язана з вашими комітами. Щоб налаштувати вашого користувача, відкрийте термінал або командний рядок та виконайте наступні команди:

1.  Встановіть ваше ім'я користувача:

    ```
    git config --global user.name "Ваше Ім'я"
    ```

    Замініть "Ваше Ім'я" на ваше справжнє ім'я.
2.  Встановіть вашу електронну адресу:

    ```
    git config --global user.email "ваша-електронна-адреса@example.com"
    ```

    Замініть "ваша-електронна-адреса@example.com" на вашу справжню електронну адресу.

Тепер ви готові почати використовувати Git на вашій системі.



Існують два основних способи ініціалізації репозиторію. Перший спосіб - створити новий репозиторій з вказаної теки (папки):

```
git init
```

Інакше, ми можемо склонувати існуючий віддалений репозиторій:

```
git clone username@host:/path/to/repository
```

Доброю практикою вважається, налаштування SSH-ключів для автоматичної та захищеної авторизації.

Слід зауважити, що початкова гілка для репозиторію називається "main" (можна налаштувати інше значення), або "master" для старих репозиторіїв.\


<figure><img src="https://lh5.googleusercontent.com/OjI4cr0kzqJa6rHChbsaaArXY0fiLuYzTWcAEvdfiXEY2u660hBy1pPs9xXT6cnDhBQrZoP67-JPEivspNXlTd12fkzcKiVetaOjeDV5cEztjaFrJAYf0CLMH2_mWOSqnNlwz72b_rblnTs7mn6oyGTA=s2048" alt=""><figcaption></figcaption></figure>

Є три основних концепції, які варто запам'ятати:

1. HEAD - це вказівник на останній коміт у гілці, в якій ви знаходитесь.
2. Робочий каталог - це поточний стан вашого проекту.
3. Індекс (також відомий як область підготовки) - це місце, куди ви переміщуєте змінені файли, щоб їх закомітити.

1\) Move a file from the working directory to the staging area:

```
git add <file>
```

2\) Check that there are staged, uncommited modifications:

```
git status
```

\
3\) Create a new commit (with HEAD as parent) from the staging area:

```
git commit -m "Message"
```

If you cloned, you now have a commit in your local repository which is not present in the hosted repository! You can synchronize the two as:

```
git push origin main
```

Otherwise, you can manually add a remote repository:

```
git remote add origin <server>
```

Similarly, you can pull any changes that was pushed to the hosted repository:

```
git pull
```

When doing a push/pull, a number of conflicts can arise. Commonly, we can forget to pull before committing, or commits can be pushed to the remote while we are working.

Git tries to auto-resolve most conflicts that happen in these scenarios. If this is not possible (same file has been modified twice), it asks the user to merge the modification manually and perform a final commit.\
If the conflict arises during a push, the user needs to pull the updated repository and then resolve the conflicts. Before pulling, you can also inspect the content of the remote repository:

```
git remote show origin
```

To unstage a file that has been staged (but keep the modifications in the working directory):

```
git restore --staged <file>
```

Or you can simply delete any modification and restore the previous commit:

```
git restore
```

restore can be dangerous: anything committed in Git can be recovered in one way or another, but restoring a file will delete the modifications forever.

\
