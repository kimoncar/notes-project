# Подключение локального репозитория к GitHub по SSH

## Генерируем SSh-пару ключей

1. Проверяем наличие ранее сгенерированных ключей. Выполняем в консоли команду:
```
$ cd ~/.ssh/ && ls
```
Директория должна быть пустой. Если есть какие-то файлы, то их необходимо удалить.

2. Для генерации ключей выполняем команду:
```
$ ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"
``` 
3. Подтверждаем место хранения ключей по-умолчанию, кодовую фразу оставляем пустой. Для этого везде жмем *Enter*.
4. Проверяем наличие созданных ключей:
```
$ ls -a ~/.ssh
```

## Регистрируемся на сайте GitHub
1. Переходим на страницу регистрации [GitHub](https://github.com/signup)
2. Заполняем все поля и подтверждаем регистрацию.
3. Переходим на страницу профиля в список репозиториев (Repositories), жмем кнопку [NEW](https://github.com/new)
4. Заполняем поле **Repository name**, например, *my-project* (для удобства имя репозитория сделать таким же как имя кашего локального проекта). По желанию можно заполнить поле **Description**.
5. Жмем кнопку **Create repository**.

## Добавляем ключ SSH
1. Переходим в настройки аккаунта в подраздел [SSH and GPG keys](https://github.com/settings/keys)
2. Жмем кнопку [New SSH Key](https://github.com/settings/ssh/new)
3. Заполняем название, например, *Personal key*.
4. **Key type** - *Authentication Key*.
5. В поле *Key* вставляем сгенерированный ключ. Для этого в своей консоли копируем публичный ключ командой:
```
$ clip < ~/.ssh/id_ed25519.pub 
```
и вставляем его в поле **Key**.

6. Жмем кнопку **Add SSH Key**.
7. Для проверки ключа вводим команду в консоли:
```
$ ssh -T git@github.com
```
8. Если вы впервые используете Git, то увидите сообщение о проверке ключа. Для проверке переходим по [ссылке](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints) и сравниваем ключ SHA256 с ключом, показанным в консоли. Если совпадает то подтверждаем:
```
yes -> Enter
```
