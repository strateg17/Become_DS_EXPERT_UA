---
description: >-
  У цьому розділі буде розглянуто як ефективно налаштувати ssh доступи до
  робочих репозиторіїв під час використання системи контролю версій з метою
  забезпечення захищеного доступу до коду
---

# Git SSH

### **Налаштування SSH**

Перш за все потрібно розпочати із налаштування безпечної роботи із репозиторіями через ssh ключі. Для налаштування ssh доступів до наших репозиторіїв можна скористатися цим гайдом: [Use SSH key authentication](https://learn.microsoft.com/en-us/azure/devops/repos/git/use-ssh-keys-to-authenticate?view=azure-devops) та ось цим [SSH: RSA-ключи и ssh-agent – управление SSH-ключами и их паролями](https://rtfm.co.ua/ru/ssh-rsa-klyuchi-i-ssh-agent-upravlenie-ssh-klyuchami-i-ix-parolyami/).

Проте у них є багато відритих питань, особливо, що стосується одночасного використання багатьох ssh ключів. Підсумовуючи все вищевикладене, я побудудував загальний алгоритм:

#### 1. Генеруюмо ssh ключ у терміналі

Виконуємо команду:

```bash
$ ssh-keygen \
>    -m PEM \
>    -t rsa \
>    -b 4096 \
>    -C "azureuser@myserver" \
>    -f ~/.ssh/<ssh_key_file_name>\
>    -N mypassphrase
```

Наведемо пояснення для складових:

* ssh-keygen = the program used to create the keys
* \-m PEM = format the key as PEM
* \-t rsa = type of key to create, in this case in the RSA format
* \-b 4096 = the number of bits in the key, in this case 4096
* \-C "azureuser@myserver" = a comment appended to the end of the public key file to easily identify it. Normally an email address is used as the comment, but use whatever works best for your infrastructure.
* \-f \~/.ssh/mykeys/myprivatekey = the filename of the private key file, if you choose not to use the default name. A corresponding public key file appended with .pub is generated in the same directory. The directory must exist.
* \-N mypassphrase = an additional passphrase used to access the private key file.

#### 2. Перевіряємо чи згенеровано ключ

```python
$ ls -al ~/.ssh
```

(бачимо файли з однаковими назвами і різними закінченнями). Кожен ключ містить два файли. Звичайний - прихований, та із закінченням ".pub" - публічний.

#### 3. Копіюємо наш згенерований ключ

```python
$ cat <ssh_key_file_name>.pub
```

копіюємо цей публічний ключ та вставляємо його у AzureDevOps SSH Pubilc Keys. Він має мати вигляд:

```bash
ssh-rsa XXXXXXXXXXc2EAAAADAXABAAABAXC5Am7+fGZ+5zXBGgXS6GUvmsXCLGc7tX7/rViXk3+eShZzaXnt75gUmT1I2f75zFn2hlAIDGKWf4g12KWcZxy81TniUOTjUsVlwPymXUXxESL/UfJKfbdstBhTOdy5EG9rYWA0K43SJmwPhH28BpoLfXXXXXG+/ilsXXXXXKgRLiJ2W19MzXHp8z3Lxw7r9wx3HaVlP4XiFv9U4hGcp8RMI1MP1nNesFlOBpG4pV2bJRBTXNXeY4l6F8WZ3C4kuf8XxOo08mXaTpvZ3T1841altmNTZCcPkXuMrBjYSJbA8npoXAXNwiivyoe3X2KMXXXXXdXXXXXXXXXXCXXXXX/ azureuser@myserver
```

#### 4. Проводимо налаштування локальних ключів

Відкриваємо файл config для ssh ключів:

```bash
$ vim ~/.ssh/config
```

У ньому прописуємо наступні налаштування (тут наводжу приклад власного файлу):

```bash
Host azure-work
  HostName vs-ssh.visualstudio.com
  AddKeysToAgent yes
  User git
  IdentityFile ~/.ssh/azure_key
  IdentitiesOnly yes
  HostkeyAlgorithms +ssh-rsa
  PubkeyAcceptedKeyTypes=ssh-rsa

Host github-personal
  HostName github.com
  AddKeysToAgent yes
  User git
  IdentityFile ~/.ssh/personal_github_ssh_key
  IdentitiesOnly yes
```

#### 5. Проводимо налаштування ssh-agent

Тепер можна додати наші ключі до ssh-agent:

```bash
$ ssh-add -K ~/.ssh/azure_key
$ ssh-add -K ~/.ssh/personal_github_ssh_key
```

Проводимо тестування чи зв'язок встановлено коректно:

```bash
$ ssh -T azure-work
$ ssh -T github-personal 
```

#### 6. Початок роботи при новому запуску АБО запуску нового терміналу

> **ВАЖЛИВО!!!** ПРИ НОВОМУ ЗАПУСКУ ТЕРМІНАЛУ ОБОВ'ЯЗКОВО АКТИВУЄМО SSH

```bash
$ eval `ssh-agent`
$ eval $(ssh-agent -s)
```

Тепер можна перевірити чи містить агент наші ключі, виконавши команду:

```bash
$ ssh-add -l
>> The agent has no identities.
```

Цілком можливо що агент буде створений пустим, тоді потрібно буде їх додати у агент і знову перевірити.

```bash
$ ssh-add -l
3072 SHA256:m418DPQvVaGmmUueYQMchznsUbpyOn5G0lzo9MhS224 alias@company.com (RSA)
256 SHA256:XtULGUkM5X3PsHTjzHXrPCVyKbqKYsNE/cStE3+rj/c name.surname@gmail.com (ED25519)
```

Та відповідно протестувати роботу:

```bash
$ ssh -T azure-work
$ ssh -T github-personal 
```

Якщо все окей, то зв'язок буде встановлено та можна працювати із репозиторіями.

#### 6. Після закінчення роботи виконуємо команди на вибір:

```bash
$ kill $SSH_AGENT_PID
$ killall ssh-agent
```
