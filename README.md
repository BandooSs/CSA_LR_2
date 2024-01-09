# Лабораторная работа №2. Приложение с использованием Spring Framework #
## Задание № 1 ##
Модель используем **такую же** как и в первой лабораторной работе.

## Задание № 2 ##
В слой с данными был добавлен интерфейс для доступа к данным:
- **PlayerDAO**.
В нём был именован метод **getAll**.
The data layer is the same as it was before. But we have additional configuration files and modify already existing ones.

We create mvc-config.xml configuration file that 
- enables annotation-driven mode;
- specifies a base package to look for components;
- specifies rules for view files;
- defines EntityManagerFactory bean that heavily relies on persistence.xml we created before;
- defines TransactionManager.

As for persistence.xml, the only modification was related to transactions:



We also rewrote web.xml:
- included config location;
- added ContextLoaderListener;
- configured dispatcher.

## Задание № 3 ##
Our business layer is pretty much as before, but uses @Service and @Transactional annotations for each Service class.

## Задание № 4 ##

Что касается веб-уровня, то он имеет ту же логику, что и сервлеты ранее, но использование контроллеров позволило содержать логику, касающуюся игроков и команды в его контроллерах.

Мы используем следующие аннотации:

- **@Controller** для обозначения контроллера;
- **@Autowired** для предоставления экземпляра сервиса.


## Задание № 5 ##
### Demonstration and Issues###
The demonstration is the same as before. The only thing we would like to point out is that there's a problem with adding records containing Russian symbols. For example:

![изображение](https://github.com/RaisssHab/ESA2023/assets/60664914/2605c012-5588-48ac-83ef-3edbef9d8661)

![изображение](https://github.com/RaisssHab/ESA2023/assets/60664914/df792514-7dee-4d84-882d-f2c2dffe06b5)

But it wasn't the same with the previous application:

![изображение](https://github.com/RaisssHab/ESA2023/assets/60664914/8236b369-afff-4fc5-babf-8193a0d8429a)

Note that we can see Russian letters from the database correctly, but get a mess when trying to persist entries with them:

![изображение](https://github.com/RaisssHab/ESA2023/assets/60664914/c4a3d4df-f8f7-4d2b-913c-480b35ba2dcd)

A lot of attemps were taken to resolve the issue, but with no success so far.
