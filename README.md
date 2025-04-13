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
 ![рис 16](https://github.com/ysatii/teamcity/blob/main/img/img_16.jpg)

5. Для deploy будет необходимо загрузить [settings.xml](./teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.
[settings.xml](https://github.com/ysatii/teamcity/blob/main/settings.xml)

6. В pom.xml необходимо поменять ссылки на репозиторий и nexus.
[pom.xml](https://github.com/ysatii/example-teamcity/blob/master/pom.xml)

7. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.
 ![рис 17](https://github.com/ysatii/teamcity/blob/main/img/img_17.jpg)
 ![рис 18](https://github.com/ysatii/teamcity/blob/main/img/img_18.jpg)

8. Мигрируйте `build configuration` в репозиторий.
 ![рис 19](https://github.com/ysatii/teamcity/blob/main/img/img_19.jpg)
 ![рис 20](https://github.com/ysatii/teamcity/blob/main/img/img_20.jpg)
 ![рис 21](https://github.com/ysatii/teamcity/blob/main/img/img_21.jpg)
 ![рис 22](https://github.com/ysatii/teamcity/blob/main/img/img_22.jpg)


9. Создадим отдельную ветку `feature/add_reply` в репозитории.
```
git checkout -b feature/add_reply
```

10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово `hunter`.
Welcomer.java и добавим туда:

*public String hunterReply() {
    return "Only a true hunter dares to challenge the unknown!";
}*

11. Дополните тест для нового метода на поиск слова `hunter` в новой реплике.
/WelcomerTest.java и добавим:

*@Test
public void testHunterReplyContainsHunter() {
    Welcomer welcomer = new Welcomer();
    String reply = welcomer.hunterReply();
    assertTrue(reply.contains("hunter"));
}*

12. Сделаtv push всех изменений в новую ветку репозитория.
```
git add .
git commit -m "Add hunterReply() method and test"
git push origin feature/add_reply
```
13. Убедимся что сборка самостоятельно запустилась, тесты прошли успешно.
 ![рис 21](https://github.com/ysatii/teamcity/blob/main/img/img_21.jpg)
 ![рис 22](https://github.com/ysatii/teamcity/blob/main/img/img_22.jpg)

 ![рис 23](https://github.com/ysatii/teamcity/blob/main/img/img_23.jpg)
 ![рис 24](https://github.com/ysatii/teamcity/blob/main/img/img_24.jpg)

14. Внесите изменения из произвольной ветки `feature/add_reply` в `master` через `Merge`.
```
git checkout master
git merge feature/add_reply
git push origin master
```
15. Убедитесь, что нет собранного артефакта в сборке по ветке `master`.


16. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки.
 ![рис 26](https://github.com/ysatii/teamcity/blob/main/img/img_26.jpg)


17. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны.
 ![рис 27](https://github.com/ysatii/teamcity/blob/main/img/img_27.jpg)

Ошибка возникает из-за наличия Nexus Repository уже собранного файла нашей версии

 ![рис 28](https://github.com/ysatii/teamcity/blob/main/img/img_28.jpg)
 ![рис 29](https://github.com/ysatii/teamcity/blob/main/img/img_29.jpg)
 ![рис 30](https://github.com/ysatii/teamcity/blob/main/img/img_30.jpg)


18. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity.
19. В ответе пришлите ссылку на репозиторий.

---

### Как оформить решение задания
