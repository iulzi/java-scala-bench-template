# Scala ↔ Java Benchmark Template

This repository is a template project for comparing Scala 3 and Java code side by side.
It comes preconfigured with:
- Maven build supporting both Java and Scala sources
- ScalaTest (Scala) and JUnit 5 (Java) testing
- JMH for microbenchmarks (fat-jar setup included)
- Plugins for bytecode inspection and dependency updates

## Project structure
```text
src/
  main/
    java/       # Java sources
    scala/      # Scala sources
  test/
    java/       # JUnit tests
    scala/      # ScalaTest suites
docs/           # extra documentation and benchmark reports
```

## Build plugins
1. `scala-maven-plugin`
2. `maven-compiler-plugin`
3. `maven-surefire-plugin`
4. `scalatest-maven-plugin`
5. `maven-shade-plugin`
6. `exec-maven-plugin`
7. `versions-maven-plugin`

More about used plugins you can find [here](docs/About-used-plugins.md)

## How to run tests
```shell
mvn test
```
- JUnit tests (Java) are executed by Surefire
- ScalaTest suites are executed by scalatest-maven-plugin

## How to run javap
Disassemble compiled classes via javap:
```shell
export JAVAP_CLASS=path.to.class.ClassName
mvn -q -DskipTests verify
```

## How to run benchmarks
Package the project and launch JMH benchmarks:
```shell
mvn clean package
java -jar target/benchmarks.jar
```
More about used plugins you can find [here](docs/About-JMH.md)

## How to check for updates
Use Versions Maven Plugin:

- Dependency updates:
```shell
mvn versions:display-dependency-updates
```

- Plugin updates:
```shell
mvn versions:display-plugin-updates
```

- Updates by property values:
```shell
mvn versions:display-property-updates
```

## Docs
Extra notes, bytecode dumps, and benchmark results can be added in docs/.
For example:
docs/diagrams/ → diagrams and charts for readme

----------------------------
With this template you can easily fork and adapt for new experiments: collections, concurrency, compiler features, or any Scala ↔ Java performance comparison.