# Gitlab CI

## Pipeline

Это файл **.gitlab-ci.yml**.

Это конвейер, который может состоять из: джобов (jobs), описывающих что нужно выполнить; этапов (stages), указывающих когда или в какой последовательности нужно выполнить джобы.

Pipeline записывают в файле **.gitlab-ci.yml**.

Pipeline делится на stage-ы, а стейджи в свою очередь делятся на job-ы.

Примеры пайплайнов смотри в папках \*-example.

Вся последовательность действий перечислена в **.gitlab-ci.yml**., и в нем еще могут быть вызовы дочерних пайплайнов из своих .gitlab-ci.yml.

## Артефакт

Это общее название любого файла, полученного в результате сборки. Это может быть собственно результат сборки (jar или exe), отчет о тестах, сгенерированные данные и т.д.

Иначе говоря, артефакт - это нечто материальное, то что не исчезает после окончания пайплайна (в отличие от временных файлов, которые удаляются по окончании процесса)

## Runner

GitLab Runner — это агент, который собственно и занимается выполнением инструкций из pipeline (специального файла .gitlab-ci.yml).

GitLab Runner — это бинарник, который можно поставить на свой сервер и связать с гитлабом в своём аккаунте.

На самом гитлабе уже есть раннер, но он только для платных аккаунтов. Если бесплатно, то установка на сторонний сервак.
Пример для убунты.

```bash
$: curl -L "https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.deb.sh" | sudo bash
$:
$:
$: sudo apt-get update
$:
$:
$: sudo apt-get install gitlab-runner
$:
$:
$: ps aux | grep gitlab
```

См. доку
https://docs.gitlab.com/runner/install/linux-repository.html

### gitlab-runner in Docker

Также раннер можно поставить, запускать и крутить в докере. Тем более если все равно приходится крутить раннер на стороннем сервере.

См. доку
https://docs.gitlab.com/runner/install/docker.html

Docker image of gitlab-runner is on doker-hub
See https://hub.docker.com/r/gitlab/gitlab-runner/tags

## Gitlab pages

Нужно установить и запустить GitLab Pages daemon — это их собственный вебсервер. Он может быть установлен как на одном хосте с гитлабом, так и на отдельном.
Поставляется он в пакете Omnibus или отдельно.

We can publish static websites directly from a repository in GitLab.
Only html, scc, js.

Чтобы проект опубликовался на Pages, в корне должен быть файл .gitlab-ci.yaml.
В нём должна быть определена задача **pages**, в результате выполнения которой собирался артефакт из папки **public**.
Например:

```yml
image: openjdk:8

pages: # название таски
  stage: deploy
  script:
    - ./gradlew bundle
    - mkdir .public
    - cp -r src/main/web/* .public
    - cp -r build/bundle/* .public
    - mv .public public
  artifacts: # необходимый артефакт
    paths:
      - public
  only: # собирать только из ветки мастера
    - master
```

В докер контейнере openjdk выполняется скрипт, запускающий gradle и кладущий результат в папку public.

Затем создается артефакт из этой папки, который и отображается как сайт.

Всё, готово!
Чтобы понять адрес сайта, нужно зайти в репозитории в **setting → pages**.
https://your-user-name.gitlab.io/project-name

Exanple about simple html site
https://gitlab.com/pages/plain-html

see code in the folder [pages-plain-html/](../pages-plain-html/)
