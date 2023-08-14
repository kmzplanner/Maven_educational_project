# Технологии: maven
## 1. В файле конфигурации pom.xml добавили библиотеку google guava 32.1.1-jre и обновили до 32.1.2-jre
 1. Вбили в google guava maven
 2. Выбрали нужную версию из Guava: Google Core Libraries For Java
 3. Скопировали с сайта
```
<!-- https://mvnrepository.com/artifact/com.google.guava/guava -->
<dependency>
<groupId>com.google.guava</groupId>
<artifactId>guava</artifactId>
<version>32.1.1-jre</version>
</dependency> 
```

 4. Вставили в ```<dependencies> </dependencies>``` pom.xml
 5. Внесли версию guava в ```<properties>
   <version.guava>32.1.1-jre</version.guava>
   </properties>```,и в ```<dependency>
   <version>${version.guava}</version>
   </dependency>``` соответственно.
 6. Сменили версию guava с 32.1.1 на 32.1.2 в ```</properties> </properties>```
## 2. Добавили новый модуль submaven.
1. Познакомилсь с pom.xml submaven, в которм есть ссылка на родительский pom.xml`<parent>
   <artifactId>Maven_educational_project</artifactId>
   <groupId>ru.netology</groupId>
   <version>1.0-SNAPSHOT</version>
   </parent>` благодаря чему доступны как настройки, так и зависимости родительского pom.xml
2. В родительском pom.xml появился `<modules>
   <module>submaven</module>
   </modules>`, который указывет на модули, которые наследуются от текущего parent-a
## 3. Познакомились с жизненным циклом сборки Maven
1. Три трека Default, Clean, Site.
* Default (что должен пройти проект, чтобы собраться).
Содержит фазы: validate, compile, test, package, integration
-test, verify, install, deploy
* Clean очистка кеша, очщает директооию, которая появляется на фазе компиляции
* Site отвечает за формирование документации к нашему проекту
2. Clean и Site можно запускать паралельно с другими фазами
и самостоятельно
3. Родительский модуль Maven_educational_projec получил
плашку (root), значит, что сборка данного проекта приведет
к автоматической сборке его подмодулей.
4. При нажатии на фазу Clean. Пропадает папка Target
5. Каждый следующя фаза трека Default запускает предыдущий
6. Одновременно запустили Clean и фазу package из трека Default
ввели команду mvn clean package в командной строке (Terminal вуладка внизу IDEA)
7. Запустили одновременно трек Clean и фазу package чрерз терминал Inalaje
командой mvn clean package
8. Тег  `<scope>` область видимости, позвляющая сборщику
указывать когда и зачем нужна нужеа данная зависимоить 
` <dependencies>
   <dependency>
   <groupId>org.junit.jupiter</groupId>
   <artifactId>junit-jupiter-engine</artifactId>
   <version>5.3.1</version>
   <scope>test</scope> использовать данную библиотеку в фазе test
   </dependency>
   </dependencies>`
У skope 6 областей видимости compile, provided, runtime, test,
system, import