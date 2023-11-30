# Урок 3. Continuous delivery и continuous deployment (непрерывная доставка и развертывание)

1. Добавить 2 окружения "preprod" и "production"

2. Добавить отдельные deploy job для каждой среды

3. Добавить переменную "$MyLogin" внутри .gitlab-ci.yml, которая будет меняться в зависимости от среды.

```yml
deploy to preprod:
  stage: deploy
  variables:
    TARGET_ENV: preprod
  script:
    - echo "Do you deploy here to ${TARGET_ENV}"
    - echo ${MyLogin}
  only:
    - main
  environment:
    name: preprod
    auto_stop_in: 1 day
```

```yml
deploy to production:
  stage: deploy
  variables:
    TARGET_ENV: production
  script:
    - echo "Do you deploy here to ${TARGET_ENV}"
    - echo ${MyLogin}
  only:
    - main
  when: manual
  environment:
    name: production
```

4. Добавить переменную "$MyPassword" не используя .gitlab-ci.yml, которая так же будет меняться в зависимости от среды.

- (\*) Добавить скрипт в .gitlab-ci.yml, который найдёт все запущенные pipeline по названии ветки(ref) и остановит их.
