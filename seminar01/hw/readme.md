# ДЗ семинар 1

## Зарегистрироваться на gitlab.com

Зарегистрировалась на сервисе.

![create-new-blank-pr.png](./img/create-new-blank-pr.png)

Аккаунт получилось сделать через гитхаб и только с триал периодом на 30 дней.

https://gitlab.com/lex08191

## Создать pipeline и runner.

См. простейший пайплан для простейшего сайта в файле [/testpages/.gitlab-ci.yml](./testpages/.gitlab-ci.yml)

Пайплайн ничего особо не делает, просто выполняет задачу pages, где указано, что артефакты лежат в папке public.

## Попробовать сохранить артефакт одной из стадий + исключить из папки с артефактами любой файл.

https://gitlab.com/lex08191/seminar01

## Попробовать сделать любую gitlab pages.

Сделала тестовый проект

![run-pipeline-test-pages.png](./img/run-pipeline-test-pages.png)

https://gitlab.com/lex08191/testpages

код проекта см. в папке [testpages/](./testpages/)

Сайт проекта доступен по адресу

![access-pages-url.png](./img/access-pages-url.png)

https://testpages-lex08191-5c8b378b5ef14b9e8f4bbf4048f72aa113a2708e3420.gitlab.io/

Пример джоба в пайплайне для гитлаб пейджес:

```bash
pages:
  stage: deploy
  script:
    - mkdir -p public
    - cp house.txt public/index.html
  artifacts:
    paths:
      - public
    only:
      - main
```
