---
layout: post
title:  "PySpark development environment with debugger; leveraging PyCharm on mac"
author: dev
categories: [spark, pyspark, pycharm, bigdata, python, tech]
image: https://www.isdi.education/sites/default/files/styles/noticia_basico/public/noticias/big-data.png?itok=KjsLse-P
featured: true
hidden: true

---


**Note:** This turorial only focus on Spark Version 2.2.0 or later.

There are a lot of tutorials present on the web regarding this topic but none of them actually use pip to speed up the process.

With the release of spark version 2.2.0, spark added support for pip installer for pyspark. The Jira issue for the same can be tracked here - [SPARK-1267](https://issues.apache.org/jira/browse/SPARK-1267).

To simplify the process of creating a development environment, we will install pyspark using pip package manager in PyCharm.

### Follow the steps:  

- Download [Pycharm](https://www.jetbrains.com/pycharm/download/#section=mac)
- Create a new project in pycharm
- Select *Pure Python* as the type of project
- Under project Interpreter select *New Virtual Environment* and select python version 3 or later in base interpreter section.
- Note: spark is only compatible for python3 and not python2

![screenshot 2018-12-26 at 1 07 06 am](https://user-images.githubusercontent.com/15700993/50426056-c2f7e800-08aa-11e9-80f4-6f526b88e785.png){: .shadow}

- Click on *create* button for further steps
- Go to Preferences section in settings (shortcut: `command + ,`)
- In Preferences go to Project section
- Select *Project Interpreter* and select `+` to add the packages.

![screenshot 2018-12-26 at 1 16 16 am](https://user-images.githubusercontent.com/15700993/50426127-4cf48080-08ac-11e9-889d-08f3bfe4d315.png){: .shadow}

- Search for `pyspark` and install the spark version of your choice.
- Click on Apply and OK.
- You have successfully installed pyspark on your pycharm environment.
- Now In your project create a new python file and add the following code in the file.

```python
from pyspark import SparkContext

if __name__ == "__main__":
    sc = SparkContext(appName="python-helloworld")
    print("hello world", sc.startTime, sc.appName)
```

- Execute the pyspark executor using `Run` button or using shortcut `control + R`
- If the file executes successfully and you get some output like `hello world 1545767710074 python-helloworld`; You have finished the tutorial successfully.

### What is PyCharm?
PyCharm is an integrated development environment (IDE) used in computer programming, specifically for the Python language. It is developed by the Czech company **JetBrains** (also developed Intellij Idea Java IDE, Kotlin programming language). It provides code analysis, a graphical debugger, an integrated unit tester, integration with version control systems (VCSes), and supports web development with Django.

### Using Debugger In PyCharm
Jetbrains has a great documentation of Pycharm debugging.

- General introduction for debugging features like `breakpoint` can be found [here](https://www.jetbrains.com/help/pycharm/debugging-code.html).
- Debugging session along with detailed example can be found [here](https://www.jetbrains.com/help/pycharm/part-1-debugging-python-code.html).

