## Homework

Переписать test stage для тестирования docker-а. Достаточно проверить, что docker контейнер на базе нашего собранного образа в предыдущей job запускается. Прислать ссылку на gitlab_ci.yaml либо скриншот gitlab_ci.yaml test stage и скриншот успешно отработанной job-ы test.

Тесты прошли успешно

https://gitlab.com/lex08191/seminar02/-/pipelines/1085038065

pipeline

https://gitlab.com/lex08191/seminar02/-/blob/main/.gitlab-ci.yml

## Checking by docker ps command

```shell
docker ps | grep container_name
```

## Use a Docker-in-Docker container image from your Container Registry

https://docs.gitlab.com/ee/user/packages/container_registry/build_and_push_images.html#use-a-docker-in-docker-container-image-from-your-container-registry

Doc. How to test docker container from Container Registry.

```yml
test1:
  stage: test
  script:
    - docker pull $CONTAINER_TEST_IMAGE
    - docker run $CONTAINER_TEST_IMAGE /script/to/run/tests

test2:
  stage: test
  script:
    - docker pull $CONTAINER_TEST_IMAGE
    - docker run $CONTAINER_TEST_IMAGE /script/to/run/another/test
```
