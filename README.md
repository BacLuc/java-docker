Docker container to run java desktop applications

Example alias:
```
alias java11='docker run --rm -it -v "$PWD":/home/app/app \
	-v ~/.m2:/home/app/.m2 \
	-p 5900:5900 --rm \
	bacluc/java:11'
```

usage:
start java in your project:

```
java11 javac main/java/MyClass.java
java11 java main.java.MyClass
java11 mvn install exec:java
java11 ant clean-all
```