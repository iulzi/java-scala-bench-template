# Maven plugins overview

## scala-maven-plugin
What it does: adds Scala 3 support to Maven.
Why: compiles both src/main/scala and src/test/scala alongside Java sources, so you can mix Java and Scala in one project.
Key features:
- integrates Scala compiler into the Maven lifecycle (compile, test-compile);
- lets you pass compiler flags (e.g. -Xprint:inline);
- works well for cross-language projects (Java + Scala);
- [official docs](https://davidb.github.io/scala-maven-plugin/).

## scalatest-maven-plugin
What it does: provides direct integration of ScalaTest with Maven.
Why: makes it easier to run ScalaTest suites alongside other tests, especially if you want richer ScalaTest reporting.
Key features:
- goal scalatest:test runs ScalaTest suites;
- supports Scala-specific options (-oD for detailed output, tags, parallelism);
- plays nicely with IDEs and CI setups when you need explicit ScalaTest runs;
- [GitHub repo](https://github.com/scalatest/scalatest-maven-plugin).

## maven-compiler-plugin
What it does: standard Java compiler plugin.
Why: compiles Java sources and enables annotation processing.
Key features:
- configured for Java 21;
- runs the JMH annotation processor (jmh-generator-annprocess) to generate benchmark metadata;
- [official docs](https://maven.apache.org/plugins/maven-compiler-plugin/).

## maven-surefire-plugin
What it does: the default test runner plugin for Maven.
Why: it runs all unit tests in src/test/java during the test phase.
Key features:
- supports JUnit 4/5, TestNG;
- integrates into the standard Maven lifecycle (mvn test, mvn verify);
- can be configured for parallel test execution, system properties, includes/excludes patterns;
- [official docs](https://maven.apache.org/surefire/maven-surefire-plugin/)

## maven-shade-plugin
What it does: builds a fat-jar with all dependencies included.
Why: JMH benchmarks are typically run as a standalone java -jar target/benchmarks.jar.
Key features:
- sets org.openjdk.jmh.Main as the entrypoint;
- bundles service files (META-INF/services/*) needed by JMH;
- ensures you can run `java -jar benchmarks.jar` without extra setup;
- [official docs](https://maven.apache.org/plugins/maven-shade-plugin/).

## exec-maven-plugin
What it does: runs external programs via Maven.
Why: handy for invoking javap or other tooling from the Maven build.
Key features:
- profile javap lets you disassemble bytecode;
- makes it easier to script experiments and include bytecode dumps in docs;
- [official docs](https://www.mojohaus.org/exec-maven-plugin/usage.html).

## versions-maven-plugin
What it does: checks for newer versions of dependencies and plugins.
Why: helps keep your stack up to date.
Key features: 
- shows newer library versions;
- shows newer plugin versions;
- [official docs](https://www.mojohaus.org/versions/versions-maven-plugin/index.html).