# Технологии: maven
## 1. В файле конфигурации pom.xml добавили библиотеку google guava 32.1.1-jre
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