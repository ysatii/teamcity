# Домашнее задание к занятию 11 «Teamcity» - Мельник Юрий Александрович

## Подготовка к выполнению

1. В Yandex Cloud создайте новый инстанс (4CPU4RAM) на основе образа `jetbrains/teamcity-server`.
2. Дождитесь запуска teamcity, выполните первоначальную настройку.
3. Создайте ещё один инстанс (2CPU4RAM) на основе образа `jetbrains/teamcity-agent`. Пропишите к нему переменную окружения `SERVER_URL: "http://<teamcity_url>:8111"`.
4. Авторизуйте агент.
5. Сделайте fork [репозитория](https://github.com/aragastmatb/example-teamcity).
6. Создайте VM (2CPU4RAM) и запустите [playbook](./infrastructure).

## Выполнение подготовки 
1. Подготовим машину jetbrains/teamcity-server
 ![рис 6](https://github.com/ysatii/teamcity/blob/main/img/img_6.jpg)

2. Произведем настройку jetbrains-teamcity-server
 ![рис 1](https://github.com/ysatii/teamcity/blob/main/img/img_1.jpg)
 ![рис 2](https://github.com/ysatii/teamcity/blob/main/img/img_2.jpg)
 ![рис 3](https://github.com/ysatii/teamcity/blob/main/img/img_3.jpg)
 ![рис 4](https://github.com/ysatii/teamcity/blob/main/img/img_4.jpg)
 ![рис 5](https://github.com/ysatii/teamcity/blob/main/img/img_5.jpg)

3. Создадим ещё один инстанс (2CPU4RAM) на основе образа `jetbrains/teamcity-agent`. Пропишим к ему переменную окружения `SERVER_URL: "http://<teamcity_url>:8111"`.
 ![рис 7](https://github.com/ysatii/teamcity/blob/main/img/img_7.jpg)

4. Авторизируем агент
 ![рис 8](https://github.com/ysatii/teamcity/blob/main/img/img_8.jpg)

5. Сделаем fork [репозитория](https://github.com/aragastmatb/example-teamcity).
 ![рис 9](https://github.com/ysatii/teamcity/blob/main/img/img_9.jpg)

 новый репозиторий [forked from aragastmatb/example-teamcity](https://github.com/ysatii/example-teamcity)
 


 ![рис 10](https://github.com/ysatii/teamcity/blob/main/img/img_10.jpg)
 ![рис 11](https://github.com/ysatii/teamcity/blob/main/img/img_11.jpg)



## Основная часть

1. Создайте новый проект в teamcity на основе fork.
 новый репозиторий [forked from aragastmatb/example-teamcity](https://github.com/ysatii/example-teamcity)
 ![рис 12](https://github.com/ysatii/teamcity/blob/main/img/img_12.jpg)
 ![рис 13](https://github.com/ysatii/teamcity/blob/main/img/img_13.jpg)
2. Сделайте autodetect конфигурации.
 

3. Сохраните необходимые шаги, запустите первую сборку master.
 ![рис 14](https://github.com/ysatii/teamcity/blob/main/img/img_14.jpg)
 ![рис 15](https://github.com/ysatii/teamcity/blob/main/img/img_15.jpg)

4. Поменяйте условия сборки: если сборка по ветке `master`, то должен происходит `mvn clean deploy`, иначе `mvn clean test`.
5. Для deploy будет необходимо загрузить [settings.xml](./teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.
6. В pom.xml необходимо поменять ссылки на репозиторий и nexus.
7. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.
8. Мигрируйте `build configuration` в репозиторий.
9. Создайте отдельную ветку `feature/add_reply` в репозитории.
10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово `hunter`.
11. Дополните тест для нового метода на поиск слова `hunter` в новой реплике.
12. Сделайте push всех изменений в новую ветку репозитория.
13. Убедитесь, что сборка самостоятельно запустилась, тесты прошли успешно.
14. Внесите изменения из произвольной ветки `feature/add_reply` в `master` через `Merge`.
15. Убедитесь, что нет собранного артефакта в сборке по ветке `master`.
16. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки.
17. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны.
18. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity.
19. В ответе пришлите ссылку на репозиторий.

---

### Как оформить решение задания
