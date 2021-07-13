# General info
This is the repository for the course of Java Spring with Platzi, here you will see what I consider to be the most used topics and some examples.

## Table of contents
* [General info](#general-info)
* [Technologies](#technologies)
* [Setup](#setup)
* [Summary](#summary)
> * [Pure_Function](#pure_function)
> * [Integration](#integration)
> * [Functinoal](#functional)
> * [End_to_end](#end_to_end)
> * [Stress](#stress)

Project is created with:
* IntelliJ IDEA
> * With openJDK 11.0.11
> * With the module of Junit

	
## Setup
Install [IntelliJ](https://www.jetbrains.com/es-es/idea/download/#section=windows) in your computer.

Then in the extensions tab search for **Java Extension Pack** and install it.

Enter in the [Spring_initializr](https://start.spring.io/) to prepare the files that will be open with intellij
* Select Gradle Proyect
* Spring boot 2.5.2 (the most stable at the moment this repository was created)
* Group: com.platzi
* Artifact: Platzi-market
* Description: Proyecto para crear una API con Spring
* Packaging Jar
* Java: 11
* Dependencies: Spring Web

## Summary
In this course talk about all what can be done and some benefits from using Test it is recommended to use automated test rather than manual testing, there are severals kinds of thest the [Unitary](#unitary), [Integration](#integration), [Functinoal](#functional), [End_to_end](#end_to_end) and [Stress](#stress) test next I will talk more about them. Some benefits that have doing testing are for example, checking that we really complete the requirements, it helps with the documentation, improves our confidence and well its a tool that adds value as a developer.

### Pure_Functino
Its when you have a predictable result, the result always be the same by receiving the same parameters.
```java
sum(5,3);
```
### Inpure_Function
Integration test are for example when in a class your are trying to connect to a Data Base or an API you are testing that integration. or maybe when you are testing how they connect with diferent modules in your app.
```java

```
### Lambda
Its a anonymous function,its a function that have a unique use behaviour, it could be a rule that only is required in a single place, or a extremly simple funciton.

### Immutability
It could be a varible or class and this propertie is very helpful this are some pros and cons about using inmutability
Pros: 
* Once created it cannot be altered
* Make easier to create pure functions
* It make it easier to use threads or concurrency

Cons:
* If you need to modify or alter the data you will need to instanciate for each time you want to modify it.
* It require a special atention to design

Example
By using Final you make it read-only kind of variable or class 
```java
final myVar = new ArrayList<String>();
myVar = Collections.emptyList(); 
```
### SAM
This is Single Abstract Method
```java
public class Ageutils {
    public static void main(String[] args) {
        Function<Integer,String> addCeros = x -> x<10 ? "0" + x : String.valueOf(x);
        TriFunction<Integer,Integer,Integer, LocalDate> parseDate =
                (day,month,year) -> LocalDate.parse(year + "-" + month +"-" + day);

        TriFunction<Integer,Integer,Integer,Integer> calculateAge =
                (day,month,year) -> Period.between(
                        parseDate.apply(day,month,year),LocalDate.now()
                ).getDays();

        System.out.println(calculateAge.apply(10,10,1992));
    }

    @FunctionalInterface
    interface TriFunction<T,U,V,R>{
        R apply(T t,U u, V v);
    }
}
```
### Inference
In this case is when java of what kind of result is specting.. a object a String, Integer etc.
here is an example
```java
public class Inferencia {
    public static void main(String[] args) {
        Function<Integer,String> funcionConvertidora =
                x -> "Al doble: " + (x*2);

        List<String> alumnos = NombresUtils.getList("Hugo","Paco","Luis");
        alumnos.forEach((String name) -> System.out.println(name));
        alumnos.forEach(name -> System.out.println(name));
        alumnos.forEach(System.out::println);
    }
}
```
### Special_interfces
In functinoal java there are some commonly used interfaces:
* Consumer<T>: receibe a data of type T and did not generate any result
* Function<T,R>: this take one data of type T and generate a result of type R
* Predicate<T>: Take one data of type T and evaluate if the data acomplish the condition.
* Supplier<T>: it does not receive any data, but generate data of type T each time it is call
* UnaryOperator<T>: recibe one data of type T and generate a data of type T