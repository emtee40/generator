
[Official document](https://baomidou.com)

[Mybatis-Plus](https://gitee.com/baomidou/mybatis-plus)

[Advanced features of Enterprise edition Mybatis-Mate](https://gitee.com/baomidou/mybatis-mate-examples )

### Install

``` xml
<dependency>
 <groupId>com.baomidou</groupId>
 <artifactId>mybatis-plus-generator</artifactId>
 <version>Latest Version</version>
</dependency>
```

[generator version query](https://search.maven.org/search?q=a:mybatis-plus-generator )

### Use (the following tutorial is only applicable to versions above 3.5.1, which are not compatible with historical versions)

#### Quick generation

```java
FastAutoGenerator.create("url", "username", "password")
.globalConfig(builder -> {
builder.author ("baomidou")

//Set the author
.enableSwagger()

//Turn on swagger mode
.outputDir("D://");

//Specify the output directory
})
.packageConfig(builder -> {
builder.parent("com.baomidou.mybatisplus.samples.generator")

//Set the parent package name
.moduleName ("system")

//Set the name of the parent package module
 .pathInfo(Collections.singletonMap(OutputFile.xml, "D://"));

//Set the mapperXml generation path
})
.strategyConfig(builder -> {
builder.addInclude("t_simple")

//Set the table name to be generated
.addTablePrefix ("t_", "c_");

//Set the filter table prefix
})
.TemplateEngine(new FreemarkerTemplateEngine())

//Use the Freemarker engine template, the default is the Velocity engine template
.execute();
```

#### Interactive generation

```java
FastAutoGenerator.create("url", "username", "password")

//Global configuration
 .globalConfig((scanner, builder) -> builder.author(scanner.apply ("Please enter the author's name?")))

//Package configuration
 .packageConfig((scanner, builder) -> builder.parent(scanner.apply ("Please enter the package name?")))

//Policy configuration
 .strategyConfig(builder -> builder.addInclude("t_simple"))

/*
 Template engine configuration, default Velocity optional template engine Beetl or Freemarker or Enjoy
 .templateEngine(new BeetlTemplateEngine())
 .templateEngine(new FreemarkerTemplateEngine())
 .templateEngine(new EnjoyTemplateEngine())
*/
 .execute();
```

*`For more examples, please check the samples below the test package`

* [H2CodeGeneratorTest](https://github.com/baomidou/generator/blob/develop/mybatis-plus-generator/src/test/java/com/baomidou/mybatisplus/generator/samples/H2CodeGeneratorTest.java)
* [MySQLGeneratorTest](https://github.com/baomidou/generator/blob/develop/mybatis-plus-generator/src/test/java/com/baomidou/mybatisplus/generator/samples/MySQLGeneratorTest.java)
*
