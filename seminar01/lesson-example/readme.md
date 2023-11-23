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
