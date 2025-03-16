# Домашнее задание к занятию 11 «Teamcity»

## Подготовка к выполнению

1. В Yandex Cloud создайте новый инстанс (4CPU4RAM) на основе образа `jetbrains/teamcity-server`.
2. Дождитесь запуска teamcity, выполните первоначальную настройку.
3. Создайте ещё один инстанс (2CPU4RAM) на основе образа `jetbrains/teamcity-agent`. Пропишите к нему переменную окружения `SERVER_URL: "http://<teamcity_url>:8111"`.
4. Авторизуйте агент.
5. Сделайте fork [репозитория](https://github.com/aragastmatb/example-teamcity).
6. Создайте VM (2CPU4RAM) и запустите [playbook](./infrastructure).

## Основная часть

1. Создайте новый проект в teamcity на основе fork.
2. Сделайте autodetect конфигурации.
3. Сохраните необходимые шаги, запустите первую сборку master.
4. Поменяйте условия сборки: если сборка по ветке `master`, то должен происходит `mvn clean deploy`, иначе `mvn clean test`.
   ![Image alt](https://github.com/sibrael/mnt-homeworks/blob/623379e5b8a71fa5beb6372ba3af328f0c9b6971/09-ci-05-teamcity/ts1.png) 
6. Для deploy будет необходимо загрузить [settings.xml](./teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.
7. В pom.xml необходимо поменять ссылки на репозиторий и nexus.
8. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.
     ![Image alt](https://github.com/sibrael/mnt-homeworks/blob/623379e5b8a71fa5beb6372ba3af328f0c9b6971/09-ci-05-teamcity/ts2.png)
     ![Image alt](https://github.com/sibrael/mnt-homeworks/blob/623379e5b8a71fa5beb6372ba3af328f0c9b6971/09-ci-05-teamcity/ts3.png)  
10. Мигрируйте `build configuration` в репозиторий.
11. Создайте отдельную ветку `feature/add_reply` в репозитории.
12. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово `hunter`.
      ![Image alt](https://github.com/sibrael/mnt-homeworks/blob/623379e5b8a71fa5beb6372ba3af328f0c9b6971/09-ci-05-teamcity/ts7.png) 
14. Дополните тест для нового метода на поиск слова `hunter` в новой реплике.
      ![Image alt](https://github.com/sibrael/mnt-homeworks/blob/623379e5b8a71fa5beb6372ba3af328f0c9b6971/09-ci-05-teamcity/ts8.png) 
16. Сделайте push всех изменений в новую ветку репозитория.
    ![Image alt](https://github.com/sibrael/mnt-homeworks/blob/392296ea9999b7acf0511a6c3c7bd510f40a6b67/09-ci-05-teamcity/ts9.png) 
18. Убедитесь, что сборка самостоятельно запустилась, тесты прошли успешно.
19. Внесите изменения из произвольной ветки `feature/add_reply` в `master` через `Merge`.
20. Убедитесь, что нет собранного артефакта в сборке по ветке `master`.
21. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки.
22. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны.
    ![Image alt](https://github.com/sibrael/mnt-homeworks/blob/623379e5b8a71fa5beb6372ba3af328f0c9b6971/09-ci-05-teamcity/ts6.png) 
24. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity.
    ![Image alt](https://github.com/sibrael/mnt-homeworks/blob/623379e5b8a71fa5beb6372ba3af328f0c9b6971/09-ci-05-teamcity/ts5.png)
    ![Image alt](https://github.com/sibrael/mnt-homeworks/blob/623379e5b8a71fa5beb6372ba3af328f0c9b6971/09-ci-05-teamcity/ts5.png) 
26. В ответе пришлите ссылку на репозиторий.
https://github.com/sibrael/example-teamcity#
---

