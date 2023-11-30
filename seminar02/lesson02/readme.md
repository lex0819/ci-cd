# docker in gitlab

## Gitlab Registry

В GitLab есть возможность хранить докер-образы (docker image) и
собранные пакеты в Container Registry и Package Registry соответственно.

Чтобы собрать и отправить docker image, нужно сначала написать dockerfile.

## Авторизация в GitLab Registry

Использовать GitLab Deploy Token и сохранить данные авторизациии в переменные.

### Deploy Token

Создать GitLab deploy token можно в Settings → Repository
→ Deploy Token.

Add token

Enter name which we came up with usself.
Teacher wrote GITLAB_CI_USER. It was name for variable of token.

Check three points

- read_repository
- read_registry
- write_registry

It provides login and password and we need to copy the information quicly!
Password appears only one time!!!

### CI/CD variables

Now we must keep it in Variables.

Settings -> CI/CD -> Variables

Add variable

There are Key and Value for each variable.

Key is name which we came up with usself.
And value is value which we got from Deploy token generator.

They are two variables - login and password.
Names for them we write in the .gitlab-ci.yml

In my case
Deploy tokens

gitlab+deploy-token-3675374

4gXsa9HYyjS_X8ESdCSS
