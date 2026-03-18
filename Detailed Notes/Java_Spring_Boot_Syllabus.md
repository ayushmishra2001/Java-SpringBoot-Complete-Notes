# Java + Spring Boot Training Programme

> **Complete Syllabus** — 23 Modules · Full-Stack Java Backend Development

---

## Table of Contents

- [Module 1 — Development Environment Setup](#module-1-development-environment-setup)
- [Module 2 — Maven Essentials](#module-2-maven-essentials)
- [Module 3 — Java Programming Fundamentals](#module-3-java-programming-fundamentals)
- [Module 4 — Object-Oriented Programming](#module-4-object-oriented-programming)
- [Module 5 — Core Java APIs](#module-5-core-java-apis)
- [Module 6 — Git and Version Control](#module-6-git-and-version-control)
- [Module 7 — SQL Fundamentals](#module-7-sql-fundamentals)
- [Module 8 — JDBC — Java Database Connectivity](#module-8-jdbc-java-database-connectivity)
- [Module 9 — HTTP Protocol, Servlets, and JSP](#module-9-http-protocol-servlets-and-jsp)
- [Module 10 — Hibernate and JPA (ORM)](#module-10-hibernate-and-jpa-orm)
- [Module 11 — Spring Core — IoC, DI, and AOP](#module-11-spring-core-ioc-di-and-aop)
- [Module 12 — Spring MVC](#module-12-spring-mvc)
- [Module 13 — Spring JDBC and Data Access](#module-13-spring-jdbc-and-data-access)
- [Module 14 — Spring Boot and REST API Development](#module-14-spring-boot-and-rest-api-development)
- [Module 15 — REST API Best Practices](#module-15-rest-api-best-practices)
- [Module 16 — Spring Security](#module-16-spring-security)
- [Module 17 — Testing — JUnit, Mockito, and Spring Boot](#module-17-testing-junit-mockito-and-spring-boot)
- [Module 18 — Logging and Monitoring](#module-18-logging-and-monitoring)
- [Module 19 — Design Patterns](#module-19-design-patterns)
- [Module 20 — Clean Code and Project Architecture](#module-20-clean-code-and-project-architecture)
- [Module 21 — Build, Deployment, and CI/CD](#module-21-build-deployment-and-cicd)
- [Module 22 — Docker and Containerisation](#module-22-docker-and-containerisation)
- [Module 23 — Real-World Project Practices](#module-23-real-world-project-practices)

---

## Module 1 — Development Environment Setup

### 1.1 Java Development Kit (JDK)

- Download and install JDK 17 or JDK 21 (LTS) from Oracle or OpenJDK

- Setting JAVA_HOME environment variable

- Adding JDK bin directory to system PATH

- Verifying installation: java -version and javac -version

- Difference between JVM, JRE, and JDK

### 1.2 Spring Tool Suite (STS) / Eclipse IDE Setup

#### Installation

- Downloading STS from spring.io or installing STS plugin inside Eclipse

- Installing additional plugins via Eclipse Marketplace: JSON Editor, Maven Helper, YAML Editor

#### Workspace Configuration

- Workspace folder naming conventions and best practices

- Global encoding: set to UTF-8

- Line endings: Unix LF for cross-platform consistency

- Code formatter and save actions: auto-format, auto-organize imports on save

### 1.3 Maven Integration

- Auto-build Maven projects on save

- Downloading dependencies automatically on pom.xml changes

- Project → Clean to rebuild workspace

- Fixing corrupt Maven cache: clear .m2/repository and re-run Maven update

- Alt+F5 shortcut: Update Maven Project after pom.xml edit

### 1.4 Creating the First Spring Boot Project

- File → New → Spring Starter Project inside STS

- Selecting Java version, packaging (JAR), build tool (Maven)

- Adding initial dependencies: Spring Web, Spring Data JPA, MySQL Driver, Lombok

- Understanding generated pom.xml: parent, dependencies, spring-boot-maven-plugin

- Generated main application class and @SpringBootApplication annotation

- Importing existing Maven projects: File → Import → Maven → Existing Maven Project

### 1.5 STS Productivity Features

- @Autowired hover: shows injected bean and source location

- REST endpoint hover: preview URL and method

- Boot Dashboard: start/stop apps, view actuator endpoints, tail logs inside IDE

- Spring DevTools for automatic restart on classpath changes

- Opening all request mappings from the Boot Dashboard

### 1.6 Lombok Setup

- Install Lombok for IDE annotation processing: run lombok.jar installer pointing to STS/Eclipse executable

- Add Lombok dependency to pom.xml

- Verify: generated getters and setters appear without explicit code

- Common install issue: lombok.jar not found — re-run installer after IDE update

### 1.7 Keyboard Shortcuts

- Ctrl+Shift+R — Open resource (any file)

- Ctrl+Shift+T — Open type (any class)

- Alt+Shift+R — Rename with full refactor

- Ctrl+1 — Quick fix: auto-import, create method, assign to field

- Ctrl+Shift+O — Organize imports

- Ctrl+Space — Smart content assist

- F3 — Go to declaration

- Alt+Shift+M — Extract method

- Alt+Shift+L — Extract local variable

- Ctrl+E — Switch between open editors

### 1.8 Debugging

- Set breakpoint: click gutter next to line number

- Debug As → Spring Boot App

- Step Over (F6), Step Into (F5), Step Return (F7), Resume (F8)

- Variables view and Expressions view for inspecting state

- Conditional breakpoints: right-click breakpoint → Breakpoint Properties

- Inspecting HTTP request/response in controller breakpoints

### 1.9 Common IDE Problems and Fixes

- Port already in use: kill process or set server.port in application.properties

- IDE out-of-memory: increase heap in eclipse.ini (-Xmx2g)

- Lombok not working: re-run lombok.jar installer, clean project, restart IDE

- Red markers after Maven import: Project → Clean, then Maven → Update Project

---

## Module 2 — Maven Essentials

### 2.1 What Maven Does

- Dependency management: declares libraries in pom.xml, Maven downloads them from Maven Central

- Build automation: compiles, tests, packages, installs in a repeatable way

- Standard project structure: src/main/java, src/main/resources, src/test/java, src/test/resources

- Convention over configuration: works without custom config when you follow conventions

### 2.2 pom.xml Structure

- GAV coordinates: groupId (organisation), artifactId (project name), version

- packaging: jar (default for Spring Boot) or war

- parent element: spring-boot-starter-parent provides dependency management and plugin defaults

- properties: java.version, encoding, custom version variables

- dependencies section: each dependency has groupId, artifactId, version, and optional scope

- dependencyManagement section: centralise version control without pulling the dependency in

- build/plugins section: configure Maven plugins

### 2.3 Build Lifecycle

- Default lifecycle: validate → compile → test → package → verify → install → deploy

- clean lifecycle phase: removes the target/ directory

- mvn clean install — clean, compile, test, package, install JAR to local ~/.m2 repository

- mvn clean package — produce JAR/WAR without installing to local repository

- mvn clean package -DskipTests — skip test execution during build

- mvn spring-boot:run — run Spring Boot application directly via Maven plugin

- mvn dependency:tree — show full dependency graph including transitive dependencies

### 2.4 Dependency Scopes

- compile — on classpath everywhere, bundled in JAR (default scope)

- test — only available in test code; not bundled (JUnit, Mockito, H2 test database)

- provided — compile-time classpath, not bundled; container provides it at runtime (Servlet API)

- runtime — not needed to compile, needed at runtime; bundled (MySQL JDBC driver)

- Transitive dependencies: when you depend on A, Maven also brings in A\'s dependencies

- Excluding transitive dependencies: <exclusions><exclusion> to remove an unwanted transitive dependency

### 2.5 Key Plugins

- maven-compiler-plugin: sets source and target Java version

- spring-boot-maven-plugin: repackages JAR into fat/uber JAR with embedded Tomcat

- maven-surefire-plugin: executes unit tests during the test phase

- Running a Spring Boot fat JAR: java -jar target/app-0.0.1-SNAPSHOT.jar

### 2.6 Repositories

- Local repository: ~/.m2/repository — Maven caches downloaded artifacts here

- Maven Central: default remote repository at https://repo1.maven.org/maven2

- Custom repository declaration in pom.xml for company-internal Nexus or Artifactory

- Maven settings.xml: proxy configuration, mirror settings, server credentials

---

## Module 3 — Java Programming Fundamentals

### 3.1 Java Platform Overview

- History: created by James Gosling at Sun Microsystems, released 1995

- JVM (Java Virtual Machine): executes compiled bytecode (.class files)

- JRE (Java Runtime Environment): JVM plus standard libraries

- JDK (Java Development Kit): JRE plus compiler (javac) and tools

- Compile once, run anywhere: javac compiles .java to .class bytecode; any JVM can run it

- LTS versions: 8, 11, 17, 21 — prefer 17 or 21 for new projects

- Key evolution milestones: generics (5), lambdas and streams (8), modules (9), records (16), sealed classes (17), virtual threads (21)

### 3.2 Basic Syntax

#### Program Structure

- Package declaration, imports, class declaration, main method

- public class name must match the filename exactly

- public static void main(String[] args) — entry point of any Java application

- Compilation: javac FileName.java → Execution: java ClassName

#### Naming Conventions

- Classes and interfaces: PascalCase — StudentService, UserRepository

- Methods and variables: camelCase — getUserById, firstName

- Constants (static final): UPPER_SNAKE_CASE — MAX_RETRY_COUNT

- Packages: all lowercase, reverse domain — tech.csm.service

#### Comments

- Single-line: // comment

- Multi-line: /* comment */

- Javadoc: /** @param, @return, @throws, @author */

### 3.3 Primitive Data Types

- Integer types: byte (1 byte), short (2 bytes), int (4 bytes), long (8 bytes, suffix L)

- Floating-point: float (4 bytes, suffix f), double (8 bytes, default for decimals)

- char (2 bytes, Unicode), boolean (true/false)

- Wrapper classes: Integer, Long, Double, Float, Character, Boolean, Byte, Short

- Autoboxing: int ↔ Integer automatic conversion

- Default values: int 0, double 0.0, boolean false, Object null

- var keyword (Java 10+): type inferred from initialiser — var name = \"Ayush\";

- Use BigDecimal for monetary values — double has precision errors

### 3.4 Operators

- Arithmetic: + - * / % (pre/post ++ --)

- Integer division: 7/2 = 3 (truncates); 7.0/2 = 3.5

- Relational: == != > < >= <= — use .equals() for object content comparison, not ==

- Logical: && || ! — short-circuit: right side not evaluated if result already determined

- Bitwise: & | ^ ~ << >> >>>

- Compound assignment: += -= *= /= %=

- Ternary: condition ? valueIfTrue : valueIfFalse

- instanceof with pattern matching (Java 14+): if (obj instanceof String s) { s.length(); }

### 3.5 Control Flow

#### Conditionals

- if / if-else / if-else-if ladder

- switch statement — traditional with break, fall-through pitfall

- switch expression (Java 14+): uses -> arrow, no fall-through, can return value

- yield keyword in switch blocks to produce a value

#### Loops

- for: for (int i = 0; i < n; i++)

- enhanced for-each: for (String item : list) — no index access, no modification

- while: condition checked before each iteration

- do-while: body executes at least once

#### Jump Statements

- break — exits innermost loop or switch

- break with label — exits named outer loop

- continue — skips current iteration, proceeds to next

- return — exits current method, optionally returns a value

- Guard clauses: early return to reduce nesting

### 3.6 Enums

#### Enum Basics

- public enum Status { ACTIVE, INACTIVE, PENDING }

- Enum constants are implicitly public, static, final instances of the enum class

- values() — returns all constants as array

- valueOf(String) — returns constant matching the string name

- ordinal() — zero-based position; name() — constant name as String

#### Enums with Fields and Methods

- Enums can have fields, constructors (always private), and methods

- Example: enum Priority { HIGH(3), MEDIUM(2), LOW(1); private final int level; }

- Abstract methods: each constant overrides them individually

#### Enums in Practice

- switch expressions with enums: compiler checks exhaustiveness

- EnumSet and EnumMap: most efficient collection types for enum keys

- @Enumerated(EnumType.STRING) in JPA — always use STRING, not ORDINAL

- Risk of ORDINAL: inserting a constant in the middle corrupts existing persisted data

- Enum-based Singleton: guaranteed thread-safe, serialization-safe, concise

- Common uses: roles, order status, event type, HTTP methods, day of week

### 3.7 Type Casting and Conversion

- Widening (implicit): byte → short → int → long → float → double

- Narrowing (explicit cast): (int) 3.7 — may lose precision or data

- String to primitive: Integer.parseInt(), Double.parseDouble(), Boolean.parseBoolean()

- Primitive to String: String.valueOf(value) or value + \"\"

---

## Module 4 — Object-Oriented Programming

### 4.1 Classes and Objects

- Class: blueprint — fields (state) + methods (behaviour) + constructors

- Object: instance created with new; reference on stack, object on heap

- Default constructor: provided by compiler only if no constructor is written

- Constructor overloading: multiple constructors with different parameter lists

- Constructor chaining with this(): must be the first statement

- this keyword: current object reference; differentiates fields from parameters

### 4.2 Methods

- Method overloading: same name, different parameter types or count; return type alone is not enough

- Java is pass-by-value: for objects, the reference is passed by value

- Varargs: void log(String... messages) — zero or more arguments

- Method signature: name + parameter types (return type excluded)

### 4.3 Access Modifiers and Encapsulation

- private — same class only

- default (package-private) — same package

- protected — same package + subclasses

- public — accessible everywhere

- Encapsulation: private fields + public getters/setters with validation in setters

- Immutable objects: final class, all fields private final, no setters, defensive copying in constructor and getters

- Benefits of immutability: thread-safe by design, safe for caching, predictable

### 4.4 Inheritance

- extends keyword: one class inherits fields, methods, constructors of another

- IS-A relationship: a Dog IS-A Animal — use inheritance only when this holds

- Java supports single inheritance for classes

- @Override annotation: compiler validates the override, catches typos

- Override rules: same signature, same or covariant return type, no more restrictive access

- super keyword: access superclass methods (super.method()) or constructor (super(args))

- super() must be first statement in constructor

- Object class: root of all Java classes; provides toString(), equals(), hashCode(), getClass()

- equals() and hashCode() contract: if a.equals(b) then a.hashCode() == b.hashCode()

- HashMap and HashSet rely on both equals() and hashCode() being correctly implemented

- copy constructors / builders: preferred over Object.clone() which is broken

### 4.5 Polymorphism

- Compile-time (static): method overloading resolved at compile time

- Runtime (dynamic): method overriding; actual method resolved at runtime based on object type

- Dynamic dispatch: Animal a = new Dog(); a.speak(); calls Dog.speak()

- Upcasting: Animal a = new Dog() — implicit, always safe

- Downcasting: Dog d = (Dog) a — explicit; always check with instanceof first

- Pattern matching instanceof (Java 14+): if (a instanceof Dog d) { d.fetch(); }

### 4.6 Abstract Classes and Interfaces

#### Abstract Classes

- abstract class: cannot be instantiated; can have abstract and concrete methods

- abstract method: declared without body; subclass must override or also be abstract

- Use when sharing common state (fields) and partial implementation

#### Interfaces

- interface: pure contract — all fields are public static final, methods public abstract by default

- implements keyword; a class can implement multiple interfaces

- default methods (Java 8): provide implementation in interface for backwards compatibility

- static methods in interfaces (Java 8): utility methods on the interface type

- private methods in interfaces (Java 9): shared helpers between default methods

- Functional interface: exactly one abstract method; @FunctionalInterface annotation

- Built-in functional interfaces: Predicate<T>, Function<T,R>, Consumer<T>, Supplier<T>

- Use interfaces for type: prefer programming to an interface (List not ArrayList)

### 4.7 Composition, Static Members, Nested Classes

- Composition (HAS-A): prefer over inheritance for flexibility and loose coupling

- final variable: cannot be reassigned; final method: cannot be overridden; final class: cannot be subclassed

- static variable: one copy per class, shared by all instances

- static method: called on class; no access to instance variables

- static block: runs once at class load time for static initialisation

- Inner class: non-static nested class; has implicit reference to outer instance

- Static nested class: no outer instance reference; used for grouping

- Anonymous class: unnamed class defined and instantiated inline — replaced by lambdas in modern code

### 4.8 Modern Java OOP

#### Records (Java 16+)

- Concise immutable data carriers: public record Point(int x, int y) {}

- Auto-generates: canonical constructor, getters (x(), y()), equals(), hashCode(), toString()

- Compact constructor for validation: public Point { if (x < 0) throw new IllegalArgumentException(); }

- Use for DTOs — do not use for JPA entities (JPA needs mutable classes with no-arg constructor)

#### Sealed Classes (Java 17+)

- Restricts which classes may extend or implement: sealed class Shape permits Circle, Rectangle

- Permitted classes must be final, sealed, or non-sealed

- Enables exhaustiveness checking in pattern matching switch

### 4.9 SOLID Principles

- S — Single Responsibility: a class has one reason to change; one concern per class

- O — Open/Closed: open for extension (new subclass, new interface impl), closed for modification of existing code

- L — Liskov Substitution: a subclass must work correctly wherever its parent is expected

- I — Interface Segregation: many small specific interfaces better than one large one

- D — Dependency Inversion: high-level modules depend on abstractions; abstractions do not depend on details

- Supporting principle — Law of Demeter: a method should talk only to its immediate collaborators

---

## Module 5 — Core Java APIs

### 5.1 String Handling

- String immutability: every modification creates a new object in memory

- String pool: string literals are interned; new String() bypasses pool

- Length and access: length(), charAt(i), toCharArray()

- Comparison: equals(), equalsIgnoreCase(), compareTo() — never use == for content comparison

- Search: indexOf(), lastIndexOf(), contains(), startsWith(), endsWith()

- Extraction: substring(start), substring(start, end)

- Modification: replace(), replaceAll(regex), toLowerCase(), toUpperCase(), trim(), strip()

- Split and join: split(regex), String.join(delimiter, elements)

- isEmpty() vs isBlank() (Java 11): isEmpty checks length zero; isBlank includes whitespace-only

- StringBuilder: mutable, not thread-safe — use in single-threaded string building and loops

- StringBuffer: mutable, thread-safe (synchronized) — use in multi-threaded contexts

- append(), insert(), delete(), deleteCharAt(), reverse() on both

- String.format(), System.out.printf(), formatted() (Java 15+)

- Text Blocks (Java 15+): multi-line strings with triple-double-quote delimiter \"\"\"

### 5.2 Collections Framework

#### Collection Hierarchy

- Iterable → Collection → List, Set, Queue

- Map is separate from Collection hierarchy

#### List Implementations

- ArrayList: dynamic array — O(1) random access, O(n) insert/remove at middle; default choice

- LinkedList: doubly-linked list — O(1) at ends; O(n) by index; also implements Deque

#### Set Implementations

- HashSet: O(1) add/contains/remove, no ordering guarantee

- LinkedHashSet: preserves insertion order, O(1) operations

- TreeSet: sorted (natural or Comparator), O(log n) operations

#### Map Implementations

- HashMap: O(1) get/put, no ordering guarantee — most commonly used map

- LinkedHashMap: preserves insertion order — useful for LRU cache

- TreeMap: sorted by key, O(log n) — useful for range queries

- EnumMap: highly efficient map for enum keys — backed by array

#### Queue and Deque

- PriorityQueue: min-heap, elements ordered by priority, O(log n) operations

- ArrayDeque: resizable double-ended queue — prefer over Stack and LinkedList for queue/stack use

#### Collections Utility Class

- Collections.sort(), binarySearch(), unmodifiableList(), synchronizedList()

- Collections.frequency(), disjoint(), nCopies()

#### Modern Collection APIs

- Immutable factory methods (Java 9+): List.of(), Set.of(), Map.of(), Map.ofEntries()

- Map enhanced methods: computeIfAbsent(), getOrDefault(), putIfAbsent(), merge()

- removeIf(predicate), replaceAll(function) on lists

#### Thread-Safe Collections

- ConcurrentHashMap: segment-level locking; no full map lock

- CopyOnWriteArrayList: reads are lock-free; writes copy the array

- BlockingQueue: ArrayBlockingQueue, LinkedBlockingQueue for producer-consumer patterns

- Avoid: Vector, Hashtable — legacy synchronized collections

#### Common Pitfalls

- ConcurrentModificationException: modifying list while iterating with for-each

- Safe removal during iteration: use Iterator.remove() or removeIf()

- EnumSet and EnumMap: always prefer over HashSet/HashMap for enum keys/values

### 5.3 Exception Handling

- Throwable → Error (JVM, do not catch) | Exception

- Checked exceptions: IOException, SQLException — must declare with throws or catch

- Unchecked (RuntimeException): NullPointerException, IllegalArgumentException — no declaration needed

- try-catch-finally: finally always executes; use for cleanup

- Multi-catch (Java 7+): catch (IOException | SQLException e)

- try-with-resources (Java 7+): auto-closes AutoCloseable; no finally needed for close

- throw: throw new IllegalArgumentException(\"message\")

- throws: declares checked exceptions a method may throw

- Custom exceptions: extend RuntimeException for unchecked; Exception for checked

- Exception translation: catch low-level exception, throw meaningful domain exception with original as cause

- Always pass original exception as cause: new ServiceException(\"msg\", e)

- Never use exceptions for control flow — expensive to construct and slow

### 5.4 Java 8+ Functional Features

#### Lambda Expressions

- (params) -> expression or (params) -> { body; }

- Used wherever a functional interface is expected

- Captures: lambdas can access effectively final local variables only

#### Method References

- Static: Integer::parseInt

- Instance of specific object: System.out::println

- Instance of arbitrary object: String::toLowerCase

- Constructor: ArrayList::new

#### Stream API

- Creation: collection.stream(), Arrays.stream(arr), Stream.of(...), Stream.generate()

- Intermediate (lazy): filter(), map(), flatMap(), sorted(), distinct(), limit(), skip(), peek()

- Terminal (eager): forEach(), collect(), reduce(), count(), findFirst(), anyMatch(), allMatch(), min(), max()

- Collectors: toList(), toSet(), toMap(), groupingBy(), partitioningBy(), joining(), counting()

- Primitive streams: IntStream, LongStream, DoubleStream — avoid boxing overhead

- Stream.toList() (Java 16+) — shorthand for collect(Collectors.toUnmodifiableList())

- Parallel streams: collection.parallelStream() — use only when proven beneficial with profiling

#### Optional

- Optional.of(), Optional.ofNullable(), Optional.empty()

- isPresent(), ifPresent(), orElse(), orElseGet(), orElseThrow(), map(), flatMap(), filter()

- Use Optional as return type only — not as field type or method parameter

#### Date and Time API (java.time)

- LocalDate, LocalTime, LocalDateTime — no timezone info

- ZonedDateTime — with timezone; Instant — machine timestamp

- Period: years/months/days difference; Duration: hours/minutes/seconds difference

- DateTimeFormatter: parse and format dates

#### CompletableFuture

- CompletableFuture.supplyAsync(() -> computation)

- Chaining: thenApply(), thenCompose(), thenCombine()

- Error handling: exceptionally(), handle()

- Combining multiple: CompletableFuture.allOf(), anyOf()

- Timeout: completeOnTimeout(value, 5, TimeUnit.SECONDS), orTimeout(5, TimeUnit.SECONDS)

### 5.5 Generics

- Type safety at compile time — eliminates ClassCastException at runtime

- Generic class: public class Box<T> { private T value; }

- Bounded: <T extends Comparable<T>>, multiple bounds: <T extends A & B>

- Generic method: public <T> List<T> wrap(T element)

- Wildcards: <?> unbounded, <? extends X> upper-bounded producer, <? super X> lower-bounded consumer

- PECS: Producer Extends, Consumer Super

- Type erasure: generics are compile-time only; erased to Object at runtime

### 5.6 Multithreading and Concurrency

#### Thread Basics

- Thread states: NEW → RUNNABLE → BLOCKED/WAITING/TIMED_WAITING → TERMINATED

- Creating threads: extend Thread (override run()) or implement Runnable (preferred)

- Callable<T>: like Runnable but returns result and can throw checked exception

#### Synchronisation

- Race condition: multiple threads read-modify-write shared state unsafely

- synchronized method: only one thread executes at a time on the same object

- synchronized block: finer-grained lock with explicit monitor object

- volatile: guarantees visibility across threads; no caching in thread-local memory

- Deadlock: thread A holds lock 1 and waits for lock 2; thread B holds lock 2 and waits for lock 1

#### Java Memory Model

- Visibility problem: changes by thread A may not be seen by thread B without synchronization

- Happens-before relationship: synchronization ensures ordering guarantees

- final fields: safely published to all threads after constructor completes

#### Executor Framework

- ExecutorService: submit(Runnable), submit(Callable), shutdown(), awaitTermination()

- Executors.newFixedThreadPool(n), newCachedThreadPool(), newSingleThreadExecutor()

- Future<T>: get() blocks until result available; cancel(), isDone()

- ReentrantLock: more flexible than synchronized — tryLock(), lockInterruptibly()

#### Atomic Variables

- AtomicInteger, AtomicLong, AtomicReference — lock-free thread-safe operations

- compareAndSet(expected, update) — atomic compare-and-swap

#### Coordination Utilities

- CountDownLatch: wait for N operations to complete before proceeding

- CyclicBarrier: all threads wait at a barrier point before continuing together

- Semaphore: limit concurrent access to a resource (e.g. connection pool)

- ThreadLocal<T>: per-thread storage; used in Spring for SecurityContext, request scope

#### Modern: Virtual Threads (Java 21)

- Thread.ofVirtual().start(runnable) — JVM-managed lightweight threads

- Millions of virtual threads possible vs thousands of platform threads

- Best for I/O-bound tasks; no benefit for CPU-bound work

### 5.7 Annotations and Reflection

- Built-in: @Override, @Deprecated, @SuppressWarnings, @FunctionalInterface, @SafeVarargs

- Custom annotation: @interface with @Retention (SOURCE/CLASS/RUNTIME) and @Target

- Reflection: Class.forName(), getDeclaredFields(), getDeclaredMethods(), setAccessible(true)

- method.invoke(object, args) for dynamic invocation

- Reflection cost: significantly slower than direct calls — used by frameworks, not business code

### 5.8 Memory Management

- Heap: all objects, garbage collected — Young generation (Eden + Survivor) and Old generation

- Stack: per-thread; holds method frames, local variables, references

- Metaspace: class metadata, static variables (replaced PermGen in Java 8)

- GC algorithms: G1GC (default Java 9+), ZGC (low latency), Shenandoah

- Memory leak causes: static collections growing indefinitely, unclosed streams, event listeners not removed

- Soft references: cache-friendly, cleared before OOM — WeakHashMap entries cleared at next GC

### 5.9 I/O and NIO.2

- Byte streams: InputStream, OutputStream; Character streams: Reader, Writer

- FileInputStream/FileOutputStream for raw binary; FileReader/FileWriter for text

- BufferedReader.readLine() for line-by-line text reading

- Always specify charset: new FileWriter(file, StandardCharsets.UTF_8)

- try-with-resources to guarantee stream closure

- NIO.2 (Java 7+): Path, Paths, Files classes — prefer over legacy File class

- Files.readAllLines(), Files.writeString(), Files.readString(), Files.copy(), Files.move()

- Serialization: Serializable marker interface; ObjectInputStream/ObjectOutputStream; transient keyword

### 5.10 Basic Unit Testing with JUnit 5

- Add JUnit 5 (jupiter) dependency with test scope in pom.xml

- @Test on test methods

- Assertions: assertEquals(), assertNotNull(), assertTrue(), assertFalse(), assertThrows()

- @BeforeEach, @AfterEach for per-test setup and teardown

- @BeforeAll, @AfterAll for class-level setup (must be static)

- @DisplayName for human-readable test names

- @ParameterizedTest with @ValueSource, @CsvSource, @MethodSource for data-driven tests

- Arrange-Act-Assert pattern in every test

- Test naming convention: methodName_scenario_expectedResult

- Spring Boot integration testing is covered in Module 17

---

## Module 6 — Git and Version Control

### 6.1 Git Fundamentals

- Distributed version control: every developer has a full copy of the repository

- Repository, working tree, staging area (index), commits

- Three states: modified (working tree), staged (index), committed (repo)

- git init — initialise a new repository

- git clone <url> — clone a remote repository locally

### 6.2 Core Workflow

- git status — show working tree state

- git add <file> / git add . — stage changes

- git commit -m \"message\" — create snapshot in local repo

- git log / git log --oneline --graph — view commit history

- git diff — show unstaged changes; git diff --staged — show staged changes

- git show <commit> — show changes in a specific commit

### 6.3 Branching and Merging

- git branch — list branches; git branch <name> — create branch

- git checkout <branch> / git switch <branch> — switch branches

- git checkout -b <name> / git switch -c <name> — create and switch

- git merge <branch> — merge target branch into current branch

- Fast-forward merge vs three-way merge

- Merge conflicts: manually edit conflicting files, then git add and git commit

- git branch -d <name> — delete merged branch; -D to force delete

### 6.4 Remote Repositories

- git remote add origin <url> — link local repo to remote

- git push origin <branch> — push commits to remote

- git pull — fetch and merge remote changes

- git fetch — download remote changes without merging

- git push -u origin main — set upstream and push

- Fork and pull request workflow on GitHub/GitLab

### 6.5 Rewriting History and Advanced Operations

- git rebase <branch>: reapply commits on top of another branch — cleaner linear history

- Interactive rebase: git rebase -i HEAD~n — squash, edit, reorder, drop commits

- Squash commits before merging: combine multiple WIP commits into one meaningful commit

- git cherry-pick <commit> — apply a specific commit to current branch

- git stash — save uncommitted work temporarily; git stash pop — restore

- git stash list, git stash apply stash@{n}

- git reset --soft HEAD~1 — undo last commit, keep changes staged

- git reset --mixed HEAD~1 — undo last commit, keep changes unstaged (default)

- git reset --hard HEAD~1 — undo last commit and discard changes (destructive)

- git revert <commit> — create new commit that undoes a previous commit (safe for shared branches)

- Never force-push to shared branches (main, develop)

### 6.6 Git Configuration and Tooling

- git config --global user.name and user.email

- git config --global core.editor and core.autocrlf

- .gitignore file: patterns for files Git should not track

- Standard Java/Spring Boot .gitignore patterns:

  - target/ — Maven build output

  - *.class — compiled bytecode

  - .idea/ *.iml .settings/ .classpath .project — IDE config files

  - application-prod.properties — never commit production credentials

  - *.log — log files

- git tag <name> — mark a release; git tag -a v1.0 -m \"message\" — annotated tag

- git blame <file> — show who last modified each line

- git bisect: binary search through commits to find the commit that introduced a bug

### 6.7 Branching Strategies for Teams

#### GitFlow Model

- main branch: always deployable, tagged with release versions

- develop branch: integration branch; features merged here

- feature/* branches: created from develop, merged back to develop via PR

- release/* branches: created from develop for final testing; merged to main and develop

- hotfix/* branches: created from main for urgent production fixes; merged to main and develop

#### Trunk-Based Development

- All developers commit directly to main or to very short-lived feature branches (< 2 days)

- Feature flags used to hide incomplete features in production

- Requires strong CI/CD pipeline and automated testing

- Preferred in high-velocity teams with good test coverage

#### Pull Request / Code Review Workflow

- Open PR from feature branch to main or develop

- Reviewer approves, CI checks pass, then merge

- Conventional commit messages: feat:, fix:, refactor:, docs:, test:, chore:

---

## Module 7 — SQL Fundamentals

### 7.1 Relational Database Concepts

- Relational model: data stored in tables (relations) with rows and columns

- RDBMS systems: MySQL, PostgreSQL, Oracle, SQL Server — this module uses MySQL

- Primary key: uniquely identifies each row in a table

- Foreign key: column referencing the primary key of another table — enforces referential integrity

- Schema: logical grouping of tables, views, indexes within a database

- MySQL setup: install MySQL Server, connect via command line or MySQL Workbench

- SHOW DATABASES; USE dbname; SHOW TABLES; DESCRIBE tablename;

### 7.2 DDL — Data Definition Language

- CREATE TABLE: define columns, types, and constraints

- Common data types: INT, BIGINT, VARCHAR(n), TEXT, DECIMAL(p,s), DATE, DATETIME, TIMESTAMP, BOOLEAN

- Constraints: PRIMARY KEY, FOREIGN KEY, UNIQUE, NOT NULL, CHECK, DEFAULT

- AUTO_INCREMENT for integer primary keys in MySQL

- ALTER TABLE: ADD COLUMN, DROP COLUMN, MODIFY COLUMN, RENAME COLUMN, ADD CONSTRAINT

- DROP TABLE: removes table and all data — irreversible

- TRUNCATE TABLE: removes all rows quickly, resets auto_increment — no WHERE clause

- CREATE INDEX indexname ON table(column);

- DROP INDEX, CREATE UNIQUE INDEX

### 7.3 DML — Data Manipulation Language

#### INSERT

- INSERT INTO table (col1, col2) VALUES (val1, val2);

- Multi-row insert: INSERT INTO table (c1,c2) VALUES (v1,v2), (v3,v4);

#### SELECT

- SELECT col1, col2 FROM table WHERE condition ORDER BY col ASC/DESC LIMIT n OFFSET m;

- SELECT * — avoid in production; select only needed columns

- WHERE clause operators: =, !=, <, >, BETWEEN, LIKE (\'%pattern%\'), IN (...), IS NULL, IS NOT NULL

- ORDER BY multiple columns: ORDER BY last_name ASC, first_name ASC

- LIMIT and OFFSET for pagination: LIMIT 10 OFFSET 20

#### UPDATE and DELETE

- UPDATE table SET col = val WHERE condition; — always include WHERE or all rows update

- DELETE FROM table WHERE condition; — always include WHERE or all rows delete

- Soft delete pattern: add a deleted_at TIMESTAMP column; never actually DELETE rows

### 7.4 Aggregate Functions and Grouping

- COUNT(*), COUNT(col) — count rows; COUNT ignores NULLs for column count

- SUM(col), AVG(col), MIN(col), MAX(col)

- GROUP BY: group rows by column value before aggregating

- HAVING: filter groups after GROUP BY — like WHERE but for groups

- WHERE filters rows before grouping; HAVING filters groups after aggregation

- NULL handling: COALESCE(col, default), IFNULL(col, default), IS NULL, IS NOT NULL

- CASE WHEN condition THEN value ELSE default END — inline conditional logic

### 7.5 JOINs

- INNER JOIN: rows with matching values in both tables

- LEFT JOIN (LEFT OUTER JOIN): all rows from left table; NULLs for unmatched right

- RIGHT JOIN (RIGHT OUTER JOIN): all rows from right table; NULLs for unmatched left

- FULL OUTER JOIN: all rows from both tables; NULLs for unmatched sides

- CROSS JOIN: every row of left with every row of right (Cartesian product)

- Self JOIN: join a table to itself using aliases — for hierarchical data

- Table aliases: SELECT e.name, d.dept_name FROM employee e JOIN department d ON e.dept_id = d.id

- Multi-table JOINs: chain multiple JOINs in one query

- Subqueries in WHERE: SELECT * FROM orders WHERE customer_id IN (SELECT id FROM customers WHERE city=\'Delhi\')

- Correlated subquery: inner query references outer query — executes per row of outer query

- EXISTS: returns true if subquery returns any rows

### 7.6 Indexes and Query Performance

- Index: data structure that allows database to find rows without full table scan

- B-tree index: balanced tree structure — most common index type; supports range queries

- Primary key is automatically indexed; UNIQUE constraint creates an index

- Composite index: index on multiple columns — column order matters

- Leftmost prefix rule: composite index on (a, b, c) helps queries filtering on a, or a+b, or a+b+c

- Covering index: index contains all columns the query needs — no table row lookup required

- EXPLAIN SELECT ...: shows query execution plan — check type, key, rows columns

- EXPLAIN ANALYZE SELECT ...: actually executes and shows real execution stats

- type column in EXPLAIN: ALL=full scan, range=index range, ref=index lookup, const=single row

- When not to index: small tables, write-heavy tables, low-cardinality columns (boolean, enum with 2 values)

- Index maintenance overhead: each INSERT/UPDATE/DELETE must update all indexes on the table

### 7.7 Normalisation

- 1NF: each column holds atomic (single) values; no repeating groups; each row uniquely identifiable

- 2NF: in 1NF + every non-key column fully depends on the entire primary key (no partial dependency)

- 3NF: in 2NF + no transitive dependency (non-key column depends only on key, not another non-key)

- BCNF (Boyce-Codd NF): stricter 3NF — every determinant is a candidate key

- Denormalisation: intentional violation for performance — reduces joins at the cost of redundancy

- When to denormalise: reporting databases, heavily read with rare writes, known query patterns

### 7.8 Transactions and Isolation

- Transaction: a unit of work that is all-or-nothing — atomicity

- ACID properties: Atomicity, Consistency, Isolation, Durability

- START TRANSACTION; / BEGIN; — begin a transaction

- COMMIT; — permanently save all changes in the transaction

- ROLLBACK; — undo all changes since the last COMMIT

- SAVEPOINT name; — mark a point within a transaction

- ROLLBACK TO SAVEPOINT name; — partial rollback to the savepoint

#### Isolation Levels

- READ UNCOMMITTED: can read uncommitted changes of other transactions (dirty reads possible)

- READ COMMITTED: only see committed data; dirty reads prevented; non-repeatable reads possible

- REPEATABLE READ: same row reads same value throughout transaction; MySQL InnoDB default

- SERIALIZABLE: full isolation; transactions execute as if sequential; highest consistency, lowest concurrency

#### Concurrency Issues

- Dirty read: reading uncommitted data from another transaction

- Non-repeatable read: reading same row twice gives different values within one transaction

- Phantom read: same query returns different set of rows due to another transaction inserting/deleting

### 7.9 Functions and Stored Procedures (Overview)

- String functions: CONCAT(), LENGTH(), UPPER(), LOWER(), SUBSTRING(), TRIM(), REPLACE()

- Numeric functions: ROUND(), CEIL(), FLOOR(), ABS(), MOD()

- Date functions: NOW(), CURDATE(), DATE_ADD(), DATE_SUB(), DATEDIFF(), DATE_FORMAT()

- Stored procedures: encapsulate SQL logic on server side — CREATE PROCEDURE / CALL

- Views: virtual tables based on a SELECT query — CREATE VIEW

- Understanding these is useful for legacy systems and complex reporting queries

---

## Module 8 — JDBC — Java Database Connectivity

### 8.1 JDBC Overview

- JDBC: standard Java API for relational database access

- Driver types: Type 1 (JDBC-ODBC), Type 2 (Native API), Type 3 (Network), Type 4 (Pure Java) — use Type 4

- MySQL Connector/J: Type 4 pure-Java driver — add to pom.xml with runtime scope

- DriverManager: traditional connection factory for learning; not used in production

- DataSource: production-grade connection factory; supports pooling and JNDI

- HikariCP DataSource: default in Spring Boot; fastest JDBC connection pool available

- DataSource advantage over DriverManager: connection pooling, no re-connecting on every query

### 8.2 Connection Management

- Connection object: represents a physical connection to the database

- Class.forName(\"com.mysql.cj.jdbc.Driver\") — load driver (auto-loaded in JDBC 4.0+)

- DriverManager.getConnection(url, user, password)

- JDBC URL format: jdbc:mysql://localhost:3306/dbname?useSSL=false&serverTimezone=UTC

- Always close Connection, Statement, ResultSet in reverse order of opening

- Use try-with-resources for automatic closing of Connection, Statement, ResultSet

- Connection pool configuration: minimum idle, maximum pool size, connection timeout

### 8.3 Executing Queries

#### Statement

- Statement: for queries without parameters

- executeQuery(sql) — returns ResultSet for SELECT

- executeUpdate(sql) — returns rows affected for INSERT/UPDATE/DELETE

- execute(sql) — returns boolean; true if first result is ResultSet

#### PreparedStatement

- Precompiled query with ? placeholders — never use Statement for user input

- PreparedStatement prevents SQL injection attacks completely

- setInt(1, value), setString(2, value), setDate(3, value)

- Reuse PreparedStatement for repeated execution — compiled only once

#### CallableStatement

- Calls stored procedures: {call procedure_name(?, ?)}

- registerOutParameter() for OUT parameters

#### Batch Processing

- addBatch(sql) or addBatch() for PreparedStatement

- executeBatch() — sends all batched statements in one round trip

- Batch processing dramatically reduces round-trips for bulk inserts

### 8.4 Processing Results

- ResultSet: cursor-based — initially before first row

- rs.next() — move to next row; returns false when no more rows

- rs.getString(\"column\"), rs.getInt(\"column\"), rs.getDate(\"column\")

- rs.getString(1), rs.getInt(2) — column index (1-based)

- rs.getObject(\"column\") — generic retrieval

- Scrollable ResultSet: TYPE_SCROLL_INSENSITIVE — allows rs.previous(), rs.absolute(n)

- ResultSetMetaData: getColumnCount(), getColumnName(), getColumnType()

### 8.5 Transaction Management in JDBC

- Auto-commit is true by default — every statement is its own transaction

- conn.setAutoCommit(false) to begin a manual transaction

- conn.commit() — commit; conn.rollback() — rollback on exception

- Savepoints: conn.setSavepoint(), conn.rollback(savepoint), conn.releaseSavepoint(savepoint)

- Transaction isolation: conn.setTransactionIsolation(Connection.TRANSACTION_READ_COMMITTED)

- Always rollback in catch and close in finally (or use try-with-resources)

### 8.6 Layered Application Architecture with JDBC

Package structure follows tech.csm.* convention:

- tech.csm.entity — Plain Java objects matching database table structure

- tech.csm.dao — Data Access Objects containing all JDBC SQL operations

- tech.csm.service — Business logic; calls DAO methods; handles transactions

- tech.csm.util — Utility classes: DBConnection helper using DataSource or DriverManager

- tech.csm.driver — Main class / test runner to demonstrate the application

- DAO interface defines the contract; DAOImpl provides the JDBC implementation

- Service layer maps between entity objects and database operations

- No business logic in DAO; no SQL in Service — strict layer separation

### 8.7 Metadata and Advanced JDBC

- DatabaseMetaData: driver version, supported features, table information

- ParameterMetaData: parameter types in PreparedStatement

- Large objects: Clob (character), Blob (binary) — getClob(), getBlob()

- Generated keys: Statement.RETURN_GENERATED_KEYS — retrieve auto-increment ID after insert

- Connection validation: conn.isValid(timeout) — check if connection is still alive

---

## Module 9 — HTTP Protocol, Servlets, and JSP

### 9.0 HTTP Protocol Fundamentals

- HTTP (HyperText Transfer Protocol): stateless request-response protocol

- Request structure: request line (method + URL + HTTP version), headers, blank line, body

- Response structure: status line (version + code + phrase), headers, blank line, body

#### HTTP Methods

- GET: retrieve a resource — safe and idempotent; no request body

- POST: submit data to create a resource — not idempotent; has request body

- PUT: replace entire resource at URI — idempotent; full resource in body

- PATCH: partial update of a resource — not necessarily idempotent

- DELETE: remove a resource — idempotent

- Idempotent: calling the same operation multiple times has the same effect as calling once

- Safe method: does not modify the resource (GET, HEAD, OPTIONS)

#### Status Code Families

- 1xx Informational: 100 Continue

- 2xx Success: 200 OK, 201 Created, 204 No Content

- 3xx Redirection: 301 Moved Permanently, 302 Found, 304 Not Modified

- 4xx Client Error: 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 409 Conflict, 422 Unprocessable Entity, 429 Too Many Requests

- 5xx Server Error: 500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable

#### Key Headers

- Request: Content-Type, Accept, Authorization, Cookie, Cache-Control, X-Request-ID

- Response: Content-Type, Location (for 201/301), Set-Cookie, ETag, Cache-Control

- Content-Type values: application/json, application/x-www-form-urlencoded, multipart/form-data, text/html

#### URL Structure

- protocol://host:port/path?query=string#fragment

- Path parameters vs query parameters — path for identity, query for filtering/sorting/paging

#### Statelessness and State Management

- HTTP is stateless: server retains no memory between requests

- Session management options: cookies (Set-Cookie/Cookie headers), URL rewriting, hidden form fields, tokens (JWT)

#### HTTPS and TLS

- HTTPS = HTTP over TLS (Transport Layer Security)

- TLS handshake: server sends certificate, client verifies, symmetric key negotiated, encrypted channel established

- HTTP/2: multiplexing (multiple requests over one connection), header compression, server push

### 9.1 Servlet Architecture

- Servlet: Java class that handles HTTP requests on the server side

- Servlet container (Tomcat, Jetty): manages servlet lifecycle and I/O

- HttpServlet class: extend it to write servlets

- DispatcherServlet (Spring MVC) is a servlet — understanding servlets explains Spring MVC internals

- Servlet lifecycle: init() → service() → doGet()/doPost() → destroy()

- init(ServletConfig config): called once on first request or at startup

- service(HttpServletRequest, HttpServletResponse): dispatches to doGet/doPost/doPut/doDelete

- destroy(): called before servlet is removed from service

### 9.2 HttpServletRequest and HttpServletResponse

#### HttpServletRequest

- getMethod() — GET, POST, etc.

- getRequestURL(), getRequestURI(), getContextPath(), getServletPath()

- getParameter(\"name\") — single query/form parameter

- getParameterValues(\"name\") — multiple values for same parameter (checkboxes)

- getHeader(\"name\"), getHeaderNames()

- getReader() / getInputStream() — read request body

- getSession(true/false) — get or create session

- setAttribute(), getAttribute() — request-scoped data sharing

#### HttpServletResponse

- setStatus(int statusCode) / sendError(code, message)

- setContentType(\"application/json\")

- getWriter() — write text response

- getOutputStream() — write binary response

- setHeader(\"name\", \"value\"), addHeader()

- sendRedirect(url) — sends 302 redirect to client

### 9.3 Session Management

- HttpSession: server-side object identified by session ID in cookie or URL

- request.getSession() — returns existing session or creates new one

- session.setAttribute(\"key\", value), session.getAttribute(\"key\")

- session.invalidate() — destroy session on logout

- Session timeout configuration in web.xml or application.properties

- Cookie-based session: JSESSIONID cookie sent to browser, returned on every request

### 9.4 Filters and Listeners

- Filter: intercept and transform requests/responses — used for logging, authentication, encoding

- Implement javax.servlet.Filter: doFilter(request, response, chain), init(), destroy()

- chain.doFilter(request, response) — passes request to next filter or servlet

- @WebFilter(urlPatterns = {\"/*\"}) — apply filter to URL pattern

- Filter chain: multiple filters in configured order

- Listener types: ServletContextListener, HttpSessionListener, ServletRequestListener

- ServletContextListener: contextInitialized() and contextDestroyed() — application startup/shutdown hooks

### 9.5 JavaServer Pages (JSP)

- JSP: HTML-like template with embedded Java — compiled to a servlet by the container

- JSP is the view layer in MVC — responsible for display, not logic

- Scripting elements: scriptlets (<% %>), expressions (<%= %>), declarations (<%! %>) — avoid in modern code

- Note: JSP scriptlets mix Java and HTML — unmaintainable; they are a historical anti-pattern

- Modern practice: JSTL tags and EL (Expression Language) — no Java code in JSP

#### Expression Language (EL)

- Access scoped attributes: ${attribute}, ${requestScope.attribute}, ${sessionScope.attribute}

- Access bean properties: ${user.firstName} calls getFirstName()

- Operators: arithmetic, relational, logical in EL expressions

#### JSTL (JSP Standard Tag Library)

- Core tags: <c:if>, <c:choose>, <c:forEach>, <c:out>, <c:set>, <c:redirect>, <c:url>

- Format tags: <fmt:formatDate>, <fmt:formatNumber>

- <%@ taglib uri=\"...\" prefix=\"c\" %> to import JSTL taglib

### 9.6 Deployment Descriptor and Web Application Structure

- web.xml: deployment descriptor — servlet mappings, filter mappings, session config, welcome files

- Standard WAR structure: WEB-INF/web.xml, WEB-INF/classes/, WEB-INF/lib/, WEB-INF/views/

- @WebServlet annotation: declares servlet without web.xml entry

- Servlet mapping: URL pattern to servlet class mapping

- Welcome file list: default page served when no path specified

- RequestDispatcher: forward(req, res) — server-side forward; include(req, res) — include output

---

## Module 10 — Hibernate and JPA (ORM)

### 10.1 ORM Concepts

- ORM (Object-Relational Mapping): maps Java objects to database tables automatically

- Eliminates boilerplate JDBC code for CRUD operations

- JPA (Jakarta Persistence API): standard specification — defines annotations and interfaces

- Hibernate: most popular JPA implementation

- Entity: Java class mapped to a database table

- Persistence context: first-level cache managed by EntityManager — tracks all managed entities

### 10.2 JPA Annotations

#### Entity Mapping

- @Entity — marks class as a JPA entity (mapped to a table)

- @Table(name = \"table_name\") — specify table name if different from class name

- @Id — marks primary key field

- @GeneratedValue(strategy = GenerationType.IDENTITY) — auto-increment

- @Column(name, nullable, length, unique) — column mapping and constraints

- @Transient — field is not persisted

- @Enumerated(EnumType.STRING) — persist enum as string value in database

- @Lob — large object (CLOB or BLOB)

- @CreationTimestamp, @UpdateTimestamp (Hibernate) — auto-set on insert/update

#### Relationship Mapping

- @OneToOne — one entity to one other entity

- @OneToMany(mappedBy = \"field\") — one entity to many; mappedBy on the non-owning side

- @ManyToOne — many entities to one; foreign key column on this side

- @ManyToMany with @JoinTable — join table for many-to-many

- @JoinColumn(name = \"fk_column\") — specify foreign key column name

- Owning side: the side that holds the foreign key; controls relationship in DB

- Bidirectional mapping: both sides annotated; mappedBy on non-owning side

#### Inheritance Mapping

- SINGLE_TABLE: all subclasses in one table — @DiscriminatorColumn for type

- TABLE_PER_CLASS: each concrete class has its own table

- JOINED: one table per class in hierarchy; joined at query time

### 10.3 EntityManager and EntityManagerFactory

- EntityManagerFactory: heavyweight, thread-safe — one per application (from persistence.xml or Spring)

- EntityManager: lightweight, not thread-safe — one per operation or transaction

- persist(entity) — insert new entity

- find(Entity.class, id) — find by primary key

- merge(entity) — update detached entity

- remove(entity) — delete entity (must be managed)

- createQuery(jpql) — create JPQL query

- createNativeQuery(sql) — create native SQL query

- flush() — synchronise persistence context to database

- clear() — clear persistence context (detach all entities)

### 10.4 JPQL — Jakarta Persistence Query Language

- Object-oriented query language — operates on entities, not tables

- Basic: SELECT e FROM Employee e WHERE e.salary > 50000

- Named parameters: WHERE e.name = :name — setParameter(\"name\", value)

- Positional parameters: WHERE e.name = ?1 — setParameter(1, value)

- JOIN FETCH: eagerly fetch association in one query — prevents N+1 problem

- Aggregate: SELECT COUNT(e), AVG(e.salary) FROM Employee e

- Named queries: @NamedQuery on entity class — compiled at startup

- @Query in Spring Data JPA: write JPQL or native SQL on repository method

### 10.5 Fetch Strategies and N+1 Problem

- FetchType.LAZY: association loaded on demand when first accessed — default for collections

- FetchType.EAGER: association loaded immediately with parent — default for @ManyToOne, @OneToOne

- N+1 problem: loading 1 parent + N SQL queries for N children; cause: LAZY with no JOIN FETCH

- Example: SELECT * FROM order — then for each order: SELECT * FROM order_items WHERE order_id=N

- Enable SQL logging to see N+1: spring.jpa.show-sql=true, spring.jpa.properties.hibernate.format_sql=true

- Solution 1: JOIN FETCH in JPQL — SELECT o FROM Order o JOIN FETCH o.items

- Solution 2: @EntityGraph(attributePaths = {\"items\"}) on repository method

- Solution 3: @BatchSize(size = 20) — Hibernate fetches N associations in one IN query

- LazyInitializationException: accessing lazy collection outside persistence context — fix with JOIN FETCH or @Transactional

### 10.6 Caching

- First-level cache: persistence context (EntityManager scope) — automatic, always on

- Second-level cache: shared across EntityManagers (EhCache, Redis) — configure per-entity with @Cache

- Query cache: cache query results — enable with hibernate.cache.use_query_cache=true

- Eviction: @Cache with CacheConcurrencyStrategy.READ_WRITE for frequently changing data

### 10.7 Optimistic and Pessimistic Locking

#### Optimistic Locking

- Use when: low contention on records; reads far outnumber writes

- @Version on an integer or timestamp field: Hibernate adds WHERE version=N to UPDATE

- If version mismatch: throws OptimisticLockException — another transaction modified the row

- Handle OptimisticLockException: retry the operation with fresh data

#### Pessimistic Locking

- Use when: high contention; financial transactions; inventory deduction where last-write-wins is unacceptable

- LockModeType.PESSIMISTIC_WRITE: SELECT ... FOR UPDATE at database level

- @Lock(LockModeType.PESSIMISTIC_WRITE) on Spring Data JPA repository method

- Risk: deadlock if two transactions lock rows in opposite order — use consistent lock ordering

- Lock timeout: jakarta.persistence.lock.timeout property in query hints

### 10.8 Hibernate Configuration with Spring Boot

- spring.datasource.url, username, password, driver-class-name in application.properties

- spring.jpa.hibernate.ddl-auto: none (prod), validate, update, create, create-drop (test)

- spring.jpa.show-sql=true — log generated SQL statements

- spring.jpa.properties.hibernate.format_sql=true — pretty-print SQL logs

- spring.jpa.properties.hibernate.dialect — set MySQL8Dialect or let Hibernate auto-detect

- @EnableTransactionManagement — enable Spring transaction management (auto-enabled in Boot)

- @Transactional on service methods — Spring AOP manages transaction begin/commit/rollback

---

## Module 11 — Spring Core — IoC, DI, and AOP

### 11.1 Spring Framework Overview

- Spring: comprehensive Java application framework for enterprise development

- Core principle: Inversion of Control (IoC) — framework controls object creation, not the code

- Dependency Injection: dependencies are injected by the container, not created by the class

- Spring modules: Core, Beans, Context, AOP, JDBC, ORM, MVC, Security, Boot

- ApplicationContext: main Spring container — holds all beans and manages their lifecycle

### 11.2 IoC Container and Bean Lifecycle

- Bean: any object managed by the Spring container

- Bean lifecycle: instantiate → populate properties → BeanNameAware → BeanFactoryAware → ApplicationContextAware → @PostConstruct → afterPropertiesSet() → ready → @PreDestroy → destroy()

- @PostConstruct: method runs after DI is complete — use for initialisation

- @PreDestroy: method runs before bean is removed — use for cleanup

- Bean scopes: singleton (default), prototype, request, session, application

- Singleton: one instance per ApplicationContext — shared across application

- Prototype: new instance created every time the bean is requested

- @Scope(\"prototype\") — change default scope

### 11.3 Java-Based Configuration

- @Configuration — marks class as source of bean definitions

- @Bean — factory method that creates and configures a bean

- @ComponentScan(basePackages = \"tech.csm\") — tells Spring where to scan for components

- @Import — import another @Configuration class

- Condition-based beans: @ConditionalOnProperty(name=\"feature.enabled\", havingValue=\"true\")

- @ConditionalOnBean — create bean only if another specific bean is present

- @ConditionalOnMissingBean — create bean only if no other bean of that type exists

- These conditionals explain how Spring Boot auto-configuration works under the hood

### 11.4 Stereotype Annotations

- @Component — generic Spring-managed component

- @Service — service-layer bean; semantic marker, behaves like @Component

- @Repository — data-access layer bean; also enables PersistenceExceptionTranslation

- @Controller — web-layer bean; used with Spring MVC

- @RestController — @Controller + @ResponseBody; used with REST APIs

### 11.5 Dependency Injection Types

#### Constructor Injection (Recommended)

- All required dependencies declared as constructor parameters

- Spring injects them automatically; no @Autowired needed when only one constructor

- Advantages: makes dependencies explicit, supports immutability, easy to test

#### Setter Injection

- @Autowired on setter methods — useful for optional dependencies

- Allows changing dependency after construction

#### Field Injection

- @Autowired directly on fields — discouraged in production code

- Makes unit testing harder because Spring container is required to inject

#### Qualifier and Primary

- @Qualifier(\"beanName\") — disambiguate when multiple beans of same type exist

- @Primary — default bean to inject when no qualifier specified

- @Lazy — create bean only when first requested

### 11.6 Spring AOP (Aspect-Oriented Programming)

#### What AOP Solves

- Cross-cutting concerns: logging, security, transactions, caching, performance monitoring

- Without AOP: the same cross-cutting code scattered across many classes (code tangling)

- With AOP: separate the concern into one Aspect class

#### AOP Vocabulary

- Aspect: class containing cross-cutting logic — annotated with @Aspect

- Advice: the action to take — @Before, @After, @AfterReturning, @AfterThrowing, @Around

- Pointcut: expression defining which method executions to intercept

- JoinPoint: a specific moment in program execution (Spring AOP supports only method execution)

- Weaving: applying aspects to target objects — Spring AOP uses proxies (runtime weaving)

#### Advice Types

- @Before: runs before the matched method; cannot prevent method execution

- @After: runs after the method (always, like finally)

- @AfterReturning: runs after normal return; can access return value

- @AfterThrowing: runs when method throws exception; can access exception

- @Around: most powerful; wraps method; proceed() calls the real method; can change args and return value

#### Pointcut Expressions

- execution: matches method signatures — most common

- execution(* tech.csm.service.*.*(..)) — any method in any service class

- execution(public * *(..)) — any public method anywhere

- @annotation(tech.csm.annotation.Audited) — methods annotated with @Audited

- within(tech.csm.service.*) — methods inside classes in service package

- bean(userService) — methods on bean named userService

#### Practical Examples

- Method execution time logging with @Around

- Audit trail: log who called which method with what arguments with @Before

- @Transactional uses AOP internally — begin/commit/rollback wrapped around service methods

- Spring Security method-level security (@PreAuthorize) uses AOP

#### AOP Limitations

- Only works on Spring-managed beans — plain new Object() bypasses AOP

- Self-invocation does not trigger advice: if methodA() calls methodB() in same class, advice on methodB is skipped

- Fix for self-invocation: inject self reference or use AopContext.currentProxy()

- Cannot intercept static methods or private methods

### 11.7 Spring Events

- ApplicationEventPublisher: publish custom application events

- Implement ApplicationEvent or use plain POJO as event object (Spring 4.2+)

- @EventListener: annotate method to handle specific event type

- @TransactionalEventListener: handle event after transaction commits

- Decouples publisher from listener — no direct method call needed

- Useful for: sending email on registration, audit logging, cache invalidation

### 11.8 Spring XML Configuration (Legacy Reference)

- ClassPathXmlApplicationContext: loads beans from XML file

- <bean id=\"\" class=\"\" /> — XML bean definition

- <property name=\"\" value=\"\" /> — setter injection in XML

- <constructor-arg value=\"\" /> — constructor injection in XML

- Understanding XML config is useful for maintaining legacy Spring MVC applications

- Modern Spring Boot uses annotation and Java config exclusively — no XML needed

---

## Module 12 — Spring MVC

### 12.1 Spring MVC Architecture

- Front Controller pattern: all requests go through DispatcherServlet first

- DispatcherServlet: central servlet — routes to correct controller, resolves view

- Flow: Client → DispatcherServlet → HandlerMapping → Controller → ModelAndView → ViewResolver → JSP → Response

- HandlerMapping: determines which controller handles the request based on URL

- ViewResolver: maps view name string to actual view file (JSP, Thymeleaf template)

### 12.2 Controller Layer

- @Controller — marks class as controller

- @RequestMapping(value = \"/path\", method = RequestMethod.GET) — map URL to method

- Shorthand mappings: @GetMapping, @PostMapping, @PutMapping, @DeleteMapping, @PatchMapping

- @RequestParam(\"name\") — extract query parameter from URL

- @PathVariable(\"id\") — extract path segment: /users/{id}

- @ModelAttribute — bind form fields to a model object

- @SessionAttribute — access session-scoped attribute

- Model, ModelMap, ModelAndView — carry data to the view

- RedirectAttributes: add flash attributes for redirect-and-render pattern (POST-Redirect-GET)

### 12.3 Views and Templates

- InternalResourceViewResolver: maps view name to WEB-INF/views/name.jsp

- prefix: /WEB-INF/views/ suffix: .jsp — controller returns view name string only

- @RequestBody — deserialise request body to Java object (JSON → POJO)

- @ResponseBody — serialise return value to response body (POJO → JSON)

- ModelAndView: carries both model data and view name

### 12.4 Form Handling and Validation

- Spring form tag library: <form:form>, <form:input>, <form:errors>

- @ModelAttribute on method parameter: Spring binds request parameters to the object

- @Valid or @Validated: trigger Bean Validation on the model attribute

- BindingResult: holds validation errors; always immediately after @Valid parameter

- Displaying errors in JSP: <form:errors path=\"fieldName\" />

- Validator interface: implement validate() for custom server-side validation

- @InitBinder: customise data binding (e.g. date format parsing)

### 12.5 Exception Handling

- @ExceptionHandler(ExceptionType.class): handle specific exception in a controller

- @ControllerAdvice: global exception handler across all controllers

- @ExceptionHandler inside @ControllerAdvice: handle exception for entire application

- HandlerExceptionResolver interface for programmatic exception resolution

### 12.6 Spring MVC Configuration

- XML-based: dispatcher-servlet.xml with component-scan, annotation-driven, view resolver beans

- Java-based: @EnableWebMvc on @Configuration class; extend WebMvcConfigurer

- Static resources: <mvc:resources mapping=\"/static/**\" location=\"/static/\"/>

- Interceptors: implement HandlerInterceptor; preHandle(), postHandle(), afterCompletion()

- Interceptor use cases: authentication check, request logging, locale setting

- Locale support: LocaleChangeInterceptor, LocaleResolver for internationalisation

### 12.7 Cascading Dropdowns (Practical Pattern)

- Requirement: selecting country populates state dropdown dynamically

- Server-side approach: @GetMapping returns states for given country as JSON or as page redirect

- Client-side approach: JavaScript onchange event calls AJAX to /api/states?country=IN

- Controller returns List<State> with @ResponseBody for AJAX calls

- Populate dropdown in JSP with returned JSON or model attribute

---

## Module 13 — Spring JDBC and Data Access

### 13.1 Spring JDBC Template

- JdbcTemplate: simplifies JDBC by handling connection, statement creation, and exception translation

- No more try-catch-finally boilerplate — Spring handles it

- Constructor injection: JdbcTemplate jdbcTemplate = new JdbcTemplate(dataSource)

- Or inject via @Autowired in Spring Boot — auto-configured when DataSource is present

#### Query Methods

- jdbcTemplate.queryForObject(sql, Integer.class) — single value

- jdbcTemplate.queryForObject(sql, new BeanPropertyRowMapper<>(User.class), args) — single object

- jdbcTemplate.query(sql, new BeanPropertyRowMapper<>(User.class), args) — list of objects

- BeanPropertyRowMapper: maps column names to bean property names (snake_case → camelCase)

- Custom RowMapper: implement RowMapper<T> for precise mapping control

#### Update Methods

- jdbcTemplate.update(sql, arg1, arg2) — INSERT, UPDATE, DELETE; returns rows affected

- KeyHolder for retrieving generated key after INSERT

### 13.2 NamedParameterJdbcTemplate

- Uses named parameters (:name) instead of positional ? — more readable

- MapSqlParameterSource: map parameter names to values

- SqlParameterSource from a bean: BeanPropertySqlParameterSource — maps bean fields to named params

- Prevents confusion with many parameters — named params are self-documenting

### 13.3 Spring Transaction Management

- @Transactional on service class or method — Spring AOP wraps it in a transaction

- Propagation behaviours:

  - REQUIRED (default): use existing transaction or create one if none exists

  - REQUIRES_NEW: always create a new transaction; suspend current if one exists

  - SUPPORTS: use existing transaction if present; proceed without if none

  - MANDATORY: must run in existing transaction; throw exception if none

  - NEVER: must not run in a transaction; throw exception if one exists

  - NOT_SUPPORTED: suspend existing transaction and run without

- Isolation levels on @Transactional: DEFAULT, READ_UNCOMMITTED, READ_COMMITTED, REPEATABLE_READ, SERIALIZABLE

- rollbackFor: @Transactional(rollbackFor = Exception.class) — rollback on checked exception too

- noRollbackFor: do not rollback for specific exception types

- readOnly = true: hint to ORM to skip dirty checking; improves read performance

- timeout: @Transactional(timeout = 30) — rollback if transaction exceeds 30 seconds

- Self-invocation: @Transactional does not work when a method calls another @Transactional method in same class — AOP proxy is bypassed

### 13.4 Spring Data JPA

#### Repository Pattern

- JpaRepository<Entity, ID>: extends CrudRepository and PagingAndSortingRepository

- CRUD methods: save(), findById(), findAll(), deleteById(), existsById(), count()

- No implementation needed: Spring generates proxy implementation at startup

#### Derived Query Methods

- Method name defines the query: findByEmailAndStatus(String email, Status status)

- Keywords: findBy, countBy, deleteBy, existsBy

- Conditions: And, Or, Not, Between, LessThan, GreaterThan, Like, Containing, StartingWith, EndingWith, IsNull, IsNotNull, In, OrderBy

- findByFirstNameContainingIgnoreCase(String name) — case-insensitive search

#### @Query Annotation

- @Query(\"SELECT u FROM User u WHERE u.email = :email\") — JPQL query on repository method

- @Query(value = \"SELECT * FROM users WHERE email = :email\", nativeQuery = true) — native SQL

- @Modifying + @Query + @Transactional: execute UPDATE or DELETE with @Query

#### Pagination and Sorting

- Pageable parameter: Page<User> findAll(Pageable pageable)

- PageRequest.of(page, size, Sort.by(\"lastName\").ascending()) — create Pageable

- Page<T> response: getContent(), getTotalElements(), getTotalPages(), getNumber(), hasNext(), hasPrevious()

- Slice<T>: only knows if next page exists — more efficient than Page for infinite scroll

- Return Page info in response DTO: do not expose Page<Entity> directly to API consumers

#### Auditing

- @EnableJpaAuditing on @Configuration class

- @CreatedDate, @LastModifiedDate, @CreatedBy, @LastModifiedBy on entity fields

- @EntityListeners(AuditingEntityListener.class) on entity class

- AuditorAware<String> bean to provide current user for @CreatedBy and @LastModifiedBy

---

## Module 14 — Spring Boot and REST API Development

### 14.1 Spring Boot Fundamentals

- Spring Boot: opinionated framework built on Spring; removes boilerplate configuration

- Auto-configuration: detects classpath dependencies and configures beans automatically

- @SpringBootApplication = @Configuration + @ComponentScan + @EnableAutoConfiguration

- Embedded server: Tomcat embedded by default — no external server deployment needed

- Starter dependencies: spring-boot-starter-web, spring-boot-starter-data-jpa, spring-boot-starter-security

- Fat JAR: single executable JAR with all dependencies — java -jar app.jar

- Spring Initializr (start.spring.io): generate project skeleton with chosen dependencies

### 14.2 application.properties Configuration

- All configuration in src/main/resources/application.properties

- server.port=8080 — change default port

- spring.datasource.url, .username, .password, .driver-class-name — database connection

- spring.jpa.hibernate.ddl-auto=none — use none in production; update for development

- spring.jpa.show-sql=true — log SQL statements

- logging.level.tech.csm=DEBUG — set log level for specific package

- spring.application.name=myapp — application identifier

### 14.3 Spring Profiles

- Profiles: load different configuration per environment — dev, staging, prod

- application-dev.properties, application-prod.properties, application-test.properties

- Activate in base properties: spring.profiles.active=dev

- Activate via environment variable: SPRING_PROFILES_ACTIVE=prod — used in Docker and CI/CD

- Activate via command line: java -jar app.jar --spring.profiles.active=prod

- @Profile(\"dev\") on @Bean or @Configuration: bean created only in dev profile

- @ActiveProfiles(\"test\") on test class: activate profile for that test class

- Never commit production credentials — use environment variables or secrets management

- Profile-specific logging: different log levels per environment in application-{profile}.properties

### 14.4 @Value and @ConfigurationProperties

#### @Value Annotation

- @Value(\"${property.name}\") — inject a single property into a field

- Default value: @Value(\"${timeout:5000}\") — uses 5000 if property not present

- SpEL in @Value: @Value(\"#{systemProperties[\'java.home\']}\")

#### @ConfigurationProperties

- @ConfigurationProperties(prefix = \"app\") on a @Component or @Bean class

- Binds all properties with prefix app.* to fields of the class automatically

- Supports nested objects, lists, and maps

- @EnableConfigurationProperties(AppProperties.class) — required if not using @Component

- Add spring-boot-configuration-processor to pom.xml for IDE autocompletion

- Validation: @Validated on the class + @NotNull, @Min, @Max on fields

- Prefer @ConfigurationProperties over @Value for groups of related settings

### 14.5 Lombok

- Lombok: compile-time annotation processor — generates boilerplate code at compile time, not runtime

- @Getter, @Setter — generate getters and setters for all or specific fields

- @NoArgsConstructor, @AllArgsConstructor, @RequiredArgsConstructor

- @RequiredArgsConstructor: constructor for all final fields and @NonNull fields — preferred for Spring DI

- @ToString — generate toString(); use exclude = {\"password\"} to hide sensitive fields

- @EqualsAndHashCode — generate equals() and hashCode(); use callSuper = true for inheritance

- @Data = @Getter + @Setter + @ToString + @EqualsAndHashCode + @RequiredArgsConstructor

- @Builder — generate builder pattern: User.builder().name(\"x\").email(\"y\").build()

- @Builder.Default — set default values on builder fields

- @Value — immutable class: all fields private final; @Value is Lombok\'s not Spring\'s

- @Slf4j — inject private static final Logger log = LoggerFactory.getLogger(Cls.class)

- @With — create copy with one changed field: user.withEmail(\"new@email.com\")

- WARNING: do NOT use @Data on JPA entity classes — equals/hashCode triggers lazy collection loading → LazyInitializationException

- WARNING: @Builder + inheritance requires @SuperBuilder on all classes in hierarchy

- WARNING: @EqualsAndHashCode on JPA entities — use only id field: @EqualsAndHashCode(of = \"id\")

### 14.6 Jackson and JSON Processing

- Jackson: default JSON library in Spring Boot — auto-configured by spring-boot-starter-web

- ObjectMapper: central class; serialises Java → JSON, deserialises JSON → Java

- @RestController methods use Jackson automatically for @RequestBody and @ResponseBody

#### Jackson Annotations

- @JsonProperty(\"json_key\") — use a different key name in JSON output

- @JsonIgnore — exclude field from serialisation and deserialisation

- @JsonIgnoreProperties({\"field1\",\"field2\"}) — ignore specific fields at class level

- @JsonAlias({\"username\", \"user_name\"}) — accept multiple names during deserialisation

- @JsonFormat(pattern = \"yyyy-MM-dd HH:mm:ss\") — control date format in JSON

- @JsonInclude(JsonInclude.Include.NON_NULL) — skip null fields in output

- @JsonSerialize(using = ...) and @JsonDeserialize(using = ...) — custom serializers

- @JsonCreator + @JsonProperty on constructor: custom deserialisation constructor

#### Jackson Configuration

- application.properties: spring.jackson.serialization.write-dates-as-timestamps=false

- application.properties: spring.jackson.date-format=yyyy-MM-dd HH:mm:ss

- application.properties: spring.jackson.default-property-inclusion=non_null

- Custom ObjectMapper bean in @Configuration class for advanced configuration

- DeserializationFeature.FAIL_ON_UNKNOWN_PROPERTIES: disable to ignore extra JSON fields

#### Dynamic JSON

- JsonNode: read arbitrary JSON without a class — objectMapper.readTree(json)

- ObjectNode: build JSON programmatically — objectMapper.createObjectNode()

- ArrayNode: build JSON arrays programmatically

### 14.7 REST API Development

#### REST Principles

- Resource-based URLs: nouns not verbs — /users not /getUsers

- HTTP method defines action: GET=read, POST=create, PUT=replace, PATCH=partial update, DELETE=remove

- Stateless: no server-side session; each request is self-contained

- @RestController = @Controller + @ResponseBody on every method

#### Request Mapping Annotations

- @GetMapping, @PostMapping, @PutMapping, @PatchMapping, @DeleteMapping

- @PathVariable — extract path segment: /users/{id}

- @RequestParam — query parameter: /users?page=0&size=10

- @RequestBody — deserialise JSON body to Java object

- @RequestHeader — access specific header value

#### Response Handling

- ResponseEntity<T>: full control over status code, headers, and body

- ResponseEntity.ok(body) — 200; ResponseEntity.created(uri).body(dto) — 201

- ResponseEntity.noContent().build() — 204; ResponseEntity.notFound().build() — 404

- Consistent response envelope: { success, data, message, timestamp }

### 14.8 DTO Pattern and MapStruct

#### DTO (Data Transfer Object)

- DTO: object that carries data between layers — decouples API contract from entity structure

- Request DTO: data accepted from client (e.g. CreateUserRequest)

- Response DTO: data returned to client (e.g. UserResponse) — never expose entity directly

- Avoids exposing internal fields (password, audit fields) in API response

#### MapStruct for DTO Mapping

- MapStruct: compile-time annotation processor — generates type-safe mapping code (no reflection)

- Add mapstruct + lombok-mapstruct-binding to pom.xml; order matters in annotationProcessorPaths

- @Mapper(componentModel = \"spring\") — makes mapper a Spring bean, inject with @Autowired

- @Mapping(source = \"firstName\", target = \"name\") — map different field names

- @Mapping(target = \"password\", ignore = true) — skip a field

- @Mapping(expression = \"java(entity.getFirst() + \' \' + entity.getLast())\", target = \"fullName\")

- Mapping collections: List<UserResponse> toResponseList(List<User> users)

- @InheritInverseConfiguration — reverse mapping reuses source mappings

- @BeanMapping(nullValuePropertyMappingStrategy = NullValuePropertyMappingStrategy.IGNORE) — for PATCH partial update

- Manual fallback: write custom toDTO() method when mapping is too complex for MapStruct

### 14.9 Bean Validation

- Dependency: spring-boot-starter-validation in pom.xml

- @Valid on @RequestBody parameter to trigger validation

- MethodArgumentNotValidException thrown on validation failure — handle in @ControllerAdvice

#### Validation Annotations

- @NotNull — must not be null

- @NotEmpty — not null and not empty string/collection

- @NotBlank — not null and contains at least one non-whitespace character

- @Size(min = 2, max = 50) — string length or collection size

- @Min(1), @Max(100) — numeric range

- @Positive, @PositiveOrZero — numeric sign constraints

- @Email — valid email format

- @Pattern(regexp = \"...\") — custom regex validation

- @Past, @Future, @PastOrPresent, @FutureOrPresent — date constraints

#### Advanced Validation

- @Validated vs @Valid: @Validated supports validation groups and works on @PathVariable/@RequestParam

- Validation Groups: @Validated(CreateGroup.class) — different rules for create vs update

- Custom constraint: @interface with @Constraint(validatedBy = MyValidator.class)

- ConstraintValidator<Annotation, FieldType>: implement isValid(value, context)

- Class-level constraint: for cross-field validation (e.g. password == confirmPassword)

- Extracting validation error messages in @ControllerAdvice: iterate FieldErrors from BindingResult

### 14.10 RestTemplate and WebClient

#### RestTemplate (Synchronous)

- getForObject(url, ResponseType.class, uriVars) — GET and deserialise

- getForEntity(url, ResponseType.class) — GET and return ResponseEntity with status

- postForEntity(url, requestBody, ResponseType.class) — POST

- exchange(url, method, HttpEntity, ResponseType.class) — full control with headers

- Setting headers: new HttpEntity<>(body, headers) where headers is HttpHeaders

- Setting Authorization header: headers.set(HttpHeaders.AUTHORIZATION, \"Bearer \" + token)

- Error handling: RestClientException, HttpClientErrorException (4xx), HttpServerErrorException (5xx)

- Custom error handler: implement ResponseErrorHandler interface

- Timeouts: RestTemplateBuilder.connectTimeout(Duration).readTimeout(Duration)

- Note: RestTemplate is in maintenance mode — WebClient is the Spring-recommended approach

#### WebClient (Reactive, Non-Blocking)

- Part of Spring WebFlux — can be used in Spring MVC for non-blocking HTTP calls

- WebClient.builder().baseUrl(url).defaultHeader(name, value).build()

- get().uri(\"/users/{id}\", id).retrieve().bodyToMono(User.class).block() — sync

- post().bodyValue(request).retrieve().bodyToMono(Response.class) — POST

- Retry: .retryWhen(Retry.backoff(3, Duration.ofSeconds(1)))

- Prefer WebClient for new code — supports both sync (block()) and async (subscribe())

### 14.11 Spring Boot Actuator

- spring-boot-starter-actuator dependency: exposes operational endpoints

- management.endpoints.web.exposure.include=health,info,metrics,env in application.properties

- /actuator/health — application health status

- /actuator/info — custom application metadata

- /actuator/metrics — JVM, HTTP, datasource metrics

- /actuator/env — environment properties

- Custom health indicator: implement HealthIndicator interface

- Secure actuator endpoints — never expose all endpoints publicly in production

---

## Module 15 — REST API Best Practices

### 15.1 URL Design and Naming

- Use nouns (resources) not verbs: GET /users not GET /getUsers

- Plural nouns for collections: /users, /orders, /products

- Hierarchical structure: /users/{id}/orders/{orderId}

- Use lowercase and hyphens: /user-profiles not /UserProfiles or /user_profiles

- Avoid deep nesting beyond 2--3 levels — prefer flat with filters: /orders?userId={id}

- Query parameters for filtering, sorting, pagination — not path variables

### 15.2 HTTP Method Semantics

- GET /resources — list all; GET /resources/{id} — get one

- POST /resources — create new resource; return 201 Created with Location header

- PUT /resources/{id} — full replacement; return 200 or 204

- PATCH /resources/{id} — partial update; return 200 with updated resource

- DELETE /resources/{id} — delete; return 204 No Content

- Idempotency in design: PUT and DELETE should produce same result regardless of how many times called

### 15.3 Response Structure

- Consistent envelope: { \"success\": true, \"data\": {...}, \"message\": \"User found\", \"timestamp\": \"...\" }

- Error response: { \"success\": false, \"error\": { \"code\": \"USER_NOT_FOUND\", \"message\": \"...\", \"details\": [...] } }

- Do not return raw entity objects — always use DTOs

- Include HATEOAS links for self-documenting APIs (optional but recommended for public APIs)

- Avoid including null fields in response — use @JsonInclude(NON_NULL)

### 15.4 Versioning

- URL versioning: /api/v1/users — simplest, widely used, visible in logs

- Header versioning: Accept: application/vnd.company.v1+json — cleaner URLs, harder to test in browser

- Query param versioning: /users?version=1 — not recommended

- Never break existing consumers — add new fields rather than changing existing ones

- Deprecation: add Deprecation header and Sunset header with removal date

### 15.5 Pagination, Filtering, and Sorting

- Pagination: GET /users?page=0&size=20 — zero-indexed page number

- Sorting: GET /users?sort=lastName,asc or ?sort=createdAt,desc

- Filtering: GET /users?status=ACTIVE&city=Delhi

- Pagination response: include total, page, size, content, totalPages, first, last, hasNext, hasPrevious

- Cursor-based pagination for large datasets: more efficient than offset/limit for millions of rows

### 15.6 Error Handling Standards

- @ControllerAdvice with @ExceptionHandler for centralised global exception handling

- @RestControllerAdvice = @ControllerAdvice + @ResponseBody

- Map exception types to HTTP status codes consistently:

  - ResourceNotFoundException → 404

  - ValidationException / MethodArgumentNotValidException → 422 or 400

  - DuplicateResourceException → 409

  - AccessDeniedException → 403

  - AuthenticationException → 401

  - RuntimeException (generic) → 500

- Error codes: use application-specific string codes (USER_NOT_FOUND) not just HTTP status text

- Include request ID in error response for tracing: X-Request-ID header

- Never expose stack traces or internal class names in API error responses

### 15.7 Security in REST APIs

- Always use HTTPS — never serve REST APIs over plain HTTP in production

- Rate limiting: limit requests per IP/user per time window — prevent abuse

- Input validation: validate all input — see Module 14.9 Bean Validation

- CORS configuration: restrict allowed origins explicitly — do not allow * in production

- Return 401 for unauthenticated, 403 for authenticated but not authorised — never confuse them

- Never return sensitive data: mask PAN, mask SSN, never return passwords even hashed

### 15.8 API Documentation with Swagger/OpenAPI

- springdoc-openapi-starter-webmvc-ui dependency — auto-generates OpenAPI 3.0 spec

- /swagger-ui.html or /swagger-ui/index.html — interactive API explorer

- /v3/api-docs — machine-readable OpenAPI JSON spec

- @Operation(summary = \"...\", description = \"...\") on controller methods

- @Parameter(description = \"...\") on method parameters

- @ApiResponse(responseCode = \"200\", description = \"...\") for documenting responses

- @Schema(description = \"...\") on DTO fields

- Group endpoints by controller using @Tag on controller class

- Hide internal endpoints from Swagger: @Hidden on controller or method

### 15.9 Design Principles for Scalable APIs

- Idempotency keys: for POST operations that should not be duplicated (payment retry)

- Bulk operations: POST /users/batch for creating multiple resources in one call

- Asynchronous processing: return 202 Accepted with a job ID for long-running operations

- Health check endpoint: GET /health or use Actuator /actuator/health

- Timeout handling: set connect and read timeouts on outgoing HTTP calls

---

## Module 16 — Spring Security

### 16.1 Spring Security Architecture

- Security filter chain: DelegatingFilterProxy intercepts every request before it reaches DispatcherServlet

- SecurityContext: holds Authentication object; stored in SecurityContextHolder (ThreadLocal by default)

- Authentication: principal (who they are), credentials (password/token), authorities (what they can do)

- AuthenticationManager: delegates to one or more AuthenticationProvider instances

- AuthenticationProvider: performs actual authentication (username-password, token, OAuth)

- SecurityFilterChain bean: declare as @Bean with @Configuration — defines all security rules

- Order of filters matters: authentication must happen before authorisation

### 16.2 Password Encoding

- Never store plaintext passwords — always hash with BCrypt

- BCryptPasswordEncoder: adaptive hash with salt — use as a Spring bean

- @Bean PasswordEncoder passwordEncoder() { return new BCryptPasswordEncoder(); }

- passwordEncoder.encode(rawPassword) — hash; passwordEncoder.matches(raw, encoded) — verify

- BCrypt work factor (strength): default 10; increase to 12 for more security with acceptable latency

### 16.3 UserDetails and UserDetailsService

- UserDetails interface: getUsername(), getPassword(), getAuthorities(), isAccountNonExpired(), isAccountNonLocked(), isCredentialsNonExpired(), isEnabled()

- UserDetailsService: loadUserByUsername(String username) — load user from database

- Custom implementation: query user from DB; return UserDetails with GrantedAuthority list

- GrantedAuthority: SimpleGrantedAuthority(\"ROLE_ADMIN\"), SimpleGrantedAuthority(\"ROLE_USER\")

- ROLE_ prefix required when using hasRole(); not required for hasAuthority()

### 16.4 SecurityFilterChain Configuration

- http.csrf().disable() — disable CSRF for stateless REST APIs (not for form-based apps)

- http.sessionManagement().sessionCreationPolicy(SessionCreationPolicy.STATELESS) — no sessions for JWT

- http.authorizeHttpRequests(): define URL-level access rules

- .requestMatchers(\"/auth/**\").permitAll() — public endpoints

- .requestMatchers(\"/admin/**\").hasRole(\"ADMIN\") — role-specific

- .anyRequest().authenticated() — everything else requires authentication

- Method-level security: @EnableMethodSecurity enables @PreAuthorize, @PostAuthorize

- @PreAuthorize(\"hasRole(\'ADMIN\')\") on controller or service method

- @PreAuthorize(\"#userId == authentication.principal.id\") — dynamic ownership check

### 16.5 JWT Authentication

#### JWT Structure

- Header.Payload.Signature — three Base64URL-encoded parts separated by dots

- Header: algorithm (HS256 or RS256) and token type

- Payload (claims): sub (user id), iat (issued at), exp (expiry), and custom claims (role, email)

- Signature: HMAC of header+payload using secret key — verifies token was not tampered

- Never store sensitive data in JWT payload — it is Base64 encoded, not encrypted

#### JWT Library

- jjwt-api, jjwt-impl, jjwt-jackson in pom.xml

- Generating token: Jwts.builder().subject(userId).claim(\"role\",role).issuedAt(now).expiration(exp).signWith(key).compact()

- Parsing token: Jwts.parserBuilder().setSigningKey(key).build().parseClaimsJws(token).getBody()

- Catch ExpiredJwtException, MalformedJwtException, SignatureException — each maps to 401

#### Custom JWT Filter

- Extend OncePerRequestFilter: doFilterInternal(request, response, chain)

- Extract token from Authorization header: header.startsWith(\"Bearer \") → header.substring(7)

- Validate token: parse claims, check expiry, verify signature

- Build UsernamePasswordAuthenticationToken with UserDetails and authorities

- Set in SecurityContextHolder: SecurityContextHolder.getContext().setAuthentication(authToken)

- Register filter: http.addFilterBefore(jwtFilter, UsernamePasswordAuthenticationFilter.class)

- Dynamic claim extraction: read role from token claims; build authorities from claims — no hardcoded roles in filter

#### Auth Endpoints

- POST /auth/login: authenticate credentials → return access token + refresh token

- POST /auth/register: create user → hash password → return success

- POST /auth/refresh: validate refresh token → issue new access token

- POST /auth/logout: revoke refresh token → return 204

### 16.6 Refresh Token Implementation

- Why needed: short-lived access tokens (15 min) expire; refresh tokens (7 days) issue new access tokens without re-login

- Refresh token: opaque random token (UUID) stored in refresh_tokens table, not in JWT

- Table: id, token (UUID), user_id (FK), expiry_date, revoked (boolean), created_at

- POST /auth/refresh: accept refresh token → validate in DB → check expiry and not revoked → issue new access token

- Token rotation: each use of refresh token issues a new refresh token and revokes the old one

- POST /auth/logout: set revoked=true on the token — invalidates it for further use

- Revocation check: SELECT from DB on every token use — necessary for security

- Storage: refresh token in HttpOnly cookie (XSS-safe) or response body (mobile apps)

- Token family tracking: detect refresh token reuse — if already-used token is presented, revoke all tokens for that user

- Cleanup job: periodically delete expired and revoked tokens from DB

### 16.7 Security Exception Handlers

- AuthenticationEntryPoint: called when unauthenticated request hits a protected endpoint

- Without custom handler: Spring Security returns HTML error page — breaks REST JSON clients

- Custom AuthenticationEntryPoint: implement commence() — return JSON 401 response

- AccessDeniedHandler: called when authenticated user tries to access a resource they cannot

- Custom AccessDeniedHandler: implement handle() — return JSON 403 response

- Register: http.exceptionHandling().authenticationEntryPoint(customEntryPoint).accessDeniedHandler(customDeniedHandler)

### 16.8 OAuth2 and SSO (Overview)

- OAuth2: authorisation framework — allows third-party apps to act on behalf of a user

- Roles: Resource Owner (user), Client (app), Authorization Server (Google/GitHub), Resource Server (API)

- Flows: Authorization Code (web apps), Client Credentials (server-to-server), Device Code (IoT)

- spring-boot-starter-oauth2-resource-server: secure API with OAuth2 tokens

- spring-boot-starter-oauth2-client: login with Google/GitHub in web apps

- JWT as OAuth2 access token: resource server validates JWT without calling auth server

---

## Module 17 — Testing — JUnit, Mockito, and Spring Boot

### 17.1 Testing Strategy

- Unit tests: test one class in isolation; mock all dependencies

- Integration tests: test multiple components together; may use real DB or embedded DB

- End-to-end tests: test full HTTP request-response cycle through the whole application

- Test pyramid: many unit tests, fewer integration tests, few E2E tests

- Test coverage target: 80%+ line coverage as a minimum guideline; 100% is not always practical

### 17.2 Mockito

- Mockito: mock framework — creates fake implementations of dependencies

- @Mock — create a mock object; @InjectMocks — inject mocks into the class under test

- @ExtendWith(MockitoExtension.class) — activate Mockito in JUnit 5

- when(mock.method(args)).thenReturn(value) — stub method behaviour

- when(mock.method(args)).thenThrow(new Exception()) — stub exception throwing

- doNothing().when(mock).voidMethod() — stub void method

- verify(mock).method(args) — verify a method was called

- verify(mock, times(2)).method(args) — verify call count

- verify(mock, never()).method(args) — verify method was never called

- ArgumentCaptor<T>: capture the argument passed to a mock method for assertion

- ArgumentMatchers: any(), anyString(), anyInt(), eq(value), isNull()

- @Spy — partial mock: calls real methods unless stubbed

### 17.3 Service Layer Unit Tests

- Mock all repository and external service dependencies

- Test business logic branches: happy path, not found, validation failure, exception

- Test that correct methods are called on dependencies with correct arguments

- Test exception propagation: verify service throws expected exception type

- No Spring context, no database — pure Java test — fast execution

### 17.4 Spring Boot Integration Testing

- @SpringBootTest: loads full ApplicationContext — use for integration tests

- @SpringBootTest(webEnvironment = RANDOM_PORT): starts real server on random port

- @SpringBootTest(webEnvironment = MOCK): uses MockMvc, no real server

- TestRestTemplate: injected in @SpringBootTest(RANDOM_PORT) for full HTTP tests

- In-memory database for tests: H2 with test scope in pom.xml; auto-creates schema from entities

- @ActiveProfiles(\"test\"): activate test profile — loads application-test.properties

- @Transactional on test class: each test rolls back after completion — no data persistence across tests

### 17.5 Spring MVC Tests with MockMvc

- @WebMvcTest(UserController.class): loads only web layer; auto-mocks service layer

- MockMvc: perform HTTP requests without starting a server

- mockMvc.perform(get(\"/users/1\")).andExpect(status().isOk()).andExpect(jsonPath(\"$.id\").value(1))

- MockMvcRequestBuilders: get(), post(), put(), delete(), patch()

- content().contentType(MediaType.APPLICATION_JSON).content(jsonString)

- MockMvcResultMatchers: status(), jsonPath(), content(), header()

- jsonPath expressions: $.field, $.array[0].field, $.array.length()

- @MockBean — replace a Spring bean with a mock in Spring context

- @SpyBean — partially mock a Spring bean

### 17.6 Repository Layer Tests

- @DataJpaTest: loads only JPA components — entities, repositories, no service or controller

- Uses embedded H2 by default; auto-rollbacks after each test

- TestEntityManager: insert test data directly into persistence context

- Test derived query methods are correct — they are generated at startup but their SQL must be verified

- Test @Query methods with different data scenarios

- Test edge cases: empty result, multiple results, pagination boundaries

### 17.7 Test Best Practices

- Arrange-Act-Assert: every test follows this structure

- One assertion per test — clear failure messages

- Naming: methodName_givenScenario_expectResult

- No test interdependency — each test must work standalone in any order

- No hardcoded test data that may conflict — use random values or @Sql reset scripts

- Test data builders: reusable builder methods for test objects

- @Nested: group related tests for the same method inside a class

- @ParameterizedTest with @CsvSource or @MethodSource for data-driven edge case coverage

- @Disabled with reason: temporarily skip a test with explanation

---

## Module 18 — Logging and Monitoring

### 18.1 Logging Fundamentals

- Why structured logging: human-readable in dev; machine-parseable in prod for log aggregation tools

- Log levels: TRACE < DEBUG < INFO < WARN < ERROR — set minimum level per environment

- Dev: DEBUG; Staging: INFO; Production: WARN or INFO for critical packages

- Never use System.out.println in production code — use a Logger

- SLF4J (Simple Logging Facade for Java): API abstraction — write code against SLF4J interface

- Logback: default SLF4J implementation in Spring Boot — included via spring-boot-starter

### 18.2 Using SLF4J in Spring Boot

- With Lombok: @Slf4j on class — generates private static final Logger log

- Without Lombok: private static final Logger log = LoggerFactory.getLogger(MyClass.class)

- log.debug(\"User found: {}\", userId) — use {} placeholder, not string concatenation

- log.info(\"Order created: orderId={}, userId={}\", orderId, userId)

- log.warn(\"Slow database query: {} ms\", elapsed)

- log.error(\"Failed to process payment: {}\", e.getMessage(), e) — always include exception

- Use is*Enabled() guards for expensive log argument computation: if (log.isDebugEnabled()) {}

### 18.3 Logback Configuration

- src/main/resources/logback-spring.xml — Spring Boot supports profile-specific config

- ConsoleAppender: log to standard output — default, used in containers (Docker)

- RollingFileAppender: rotate log files by date or size

- TimeBasedRollingPolicy: logFile.%d{yyyy-MM-dd}.gz — one file per day, compressed

- Log pattern: %d{yyyy-MM-dd HH:mm:ss} [%thread] %-5level %logger{36} - %msg%n

- application.properties shorthand: logging.level.tech.csm=DEBUG

- logging.file.name=logs/app.log — write to file from application.properties

- JSON logging for production: logback-json encoder — Logstash Logback Encoder library

### 18.4 MDC — Mapped Diagnostic Context

- MDC: attach key-value data to current thread\'s log context — appears in all logs from that thread

- MDC.put(\"requestId\", UUID.randomUUID().toString()) at request start (in filter)

- MDC.clear() in finally to prevent ThreadLocal leak

- Add %X{requestId} to log pattern to include request ID in every log line

- Use MDC for: user ID, correlation ID, tenant ID — trace logs for one request across threads

- Spring Boot sets traceId and spanId automatically with Micrometer Tracing

### 18.5 Spring Boot Actuator Metrics

- spring-boot-starter-actuator + micrometer-registry-prometheus in pom.xml

- management.endpoints.web.exposure.include=health,info,metrics,prometheus

- /actuator/metrics — list available metrics

- /actuator/metrics/http.server.requests — HTTP request metrics

- /actuator/health — UP/DOWN with component health details

- Custom health indicator: implement HealthIndicator, return Health.up() or Health.down()

- Custom metric: inject MeterRegistry; meterRegistry.counter(\"orders.created\").increment()

- Gauge: meterRegistry.gauge(\"queue.size\", queue, Queue::size) — current value

### 18.6 Observability in Production

- Distributed tracing: trace a request across multiple services with trace ID and span ID

- Micrometer Tracing with Zipkin or Jaeger: correlate logs across microservices

- Centralized logging: ship logs to ELK stack (Elasticsearch + Logstash + Kibana) or Grafana Loki

- Metrics dashboards: Prometheus scrapes /actuator/prometheus; Grafana visualises

- Alerts: configure Grafana or AlertManager to alert on error rate, latency, or saturation

- Four golden signals: Latency, Traffic, Errors, Saturation (LTES model from Google SRE)

---

## Module 19 — Design Patterns

### 19.1 Introduction to Design Patterns

- Design patterns: reusable solutions to recurring design problems

- Gang of Four (GoF): 23 patterns across three categories — Creational, Structural, Behavioural

- Patterns are not code to copy — they are vocabulary for communicating design intent

- When not to use: do not force a pattern; simple problems need simple solutions

### 19.2 Creational Patterns

#### Singleton

- Ensures a class has only one instance and provides a global access point

- Double-checked locking with volatile: lazy initialisation safe for multithreading

- Enum Singleton: simplest thread-safe implementation — serialization-safe by default

- Spring beans are singletons by default — the container manages the single instance

#### Factory Method

- Define an interface for creating objects; let subclasses decide which class to instantiate

- Decouples object creation from the code that uses the object

- Spring: BeanFactory uses this pattern

#### Abstract Factory

- Creates families of related objects without specifying their concrete classes

- Example: UI factory producing Windows controls or Mac controls depending on platform

#### Builder

- Separates construction of complex objects from their representation

- Useful when many optional parameters exist — avoids telescoping constructors

- Lombok @Builder generates this automatically

- Spring Security HttpSecurity fluent API uses Builder pattern

#### Prototype

- Create new objects by cloning an existing prototype

- Use copy constructors or serialisation-based cloning — avoid Cloneable which is broken

- Spring prototype-scoped beans copy a prototype per injection

### 19.3 Structural Patterns

#### Adapter

- Convert interface of a class into another interface clients expect

- Example: wrap a third-party payment API behind your own PaymentGateway interface

- Spring HandlerAdapter adapts different controller types to a unified interface

#### Decorator

- Attach additional responsibilities to an object dynamically

- Wraps original object; adds behaviour before or after delegating to wrapped object

- BufferedInputStream decorates FileInputStream with buffering

- Spring Security filter chain is a chain of decorators

#### Proxy

- Provide a surrogate for another object to control access to it

- Spring AOP: JDK dynamic proxy (interface-based) or CGLIB proxy (class-based)

- @Transactional, @Cacheable, @PreAuthorize all work through Spring proxies

- Virtual proxy: creates expensive object only when needed (lazy loading in Hibernate)

#### Facade

- Unified high-level interface to a set of interfaces in a subsystem

- Example: OrderFacade hides orchestration of PaymentService, InventoryService, NotificationService

- Service layer in Spring Boot acts as a facade for multiple repositories and utilities

#### Composite

- Compose objects into tree structures to represent part-whole hierarchies

- Example: menu items that can contain sub-menus, which contain more items

#### Bridge

- Decouple abstraction from implementation so they can vary independently

- Example: Shape (abstraction) + Renderer (implementation) — shape does not need to know rendering details

### 19.4 Behavioural Patterns

#### Strategy

- Define a family of algorithms, encapsulate each, and make them interchangeable

- Inject the strategy via constructor — swap strategy without changing the context class

- Example: SortStrategy with BubbleSortStrategy and QuickSortStrategy implementations

- Spring Security uses strategy: PasswordEncoder, AuthenticationManager

#### Observer (Event-Driven)

- Object notifies a list of observers about state changes

- Spring ApplicationEventPublisher / @EventListener implements Observer pattern

- Decouples event publisher from event handlers — handlers added without modifying publisher

#### Template Method

- Define skeleton of algorithm in base class; subclasses override specific steps

- Spring JdbcTemplate: handles connection, statement, result — you provide the query and mapping

- Spring Security OncePerRequestFilter: calls doFilterInternal — you implement it

#### Command

- Encapsulate a request as an object — supports queuing, undo, and logging of operations

- Example: auditable user actions wrapped in Command objects

#### Iterator

- Provide sequential access to elements of a collection without exposing its structure

- Java Iterator and Iterable interfaces; for-each loop uses Iterator

#### Chain of Responsibility

- Pass request along a chain of handlers; each handler decides to process or pass on

- Spring Security filter chain is Chain of Responsibility

- Exception handler chain: @ExceptionHandler hierarchy

#### State

- Object changes behaviour when internal state changes — state object replaces conditionals

- Example: Order state machine — PENDING, CONFIRMED, SHIPPED, DELIVERED, CANCELLED

#### Null Object

- Provide a default object instead of returning null — eliminates null checks

- Example: NullUser implements User and has no-op methods — code never checks for null

### 19.5 Patterns in Spring Boot Context

- Repository Pattern: Spring Data JPA repositories

- Dependency Injection: Spring IoC container

- Template Method: JdbcTemplate, RestTemplate

- Proxy: AOP, @Transactional, Security

- Factory: BeanFactory, ApplicationContext

- Observer: ApplicationEventPublisher

- Strategy: PasswordEncoder, AuthenticationProvider

- Decorator: Spring Security filter chain, Logback appenders

- Facade: Service layer

---

## Module 20 — Clean Code and Project Architecture

### 20.1 Naming

- Reveal intent: customerCount not c; getUserById not get

- No encodings: no Hungarian notation; no strName

- Pronounceable names: customerRecord not custRcd

- Searchable names: avoid single-letter variables except in very small loops

- Method names: verbs — saveOrder(), findUser(), calculateTax()

- Class names: nouns — UserService, OrderRepository, JwtFilter

- Boolean names: isActive, hasPermission, canDelete

### 20.2 Functions and Methods

- Small: a method should do one thing — if it does more, extract a method

- One level of abstraction: business logic method should not also contain low-level JDBC

- Argument count: 0--2 parameters ideal; 3+ is a code smell — consider a parameter object

- No side effects: a method named getUser should not modify state

- Command-Query Separation: a method either returns a value or modifies state, not both

- Early return (guard clauses): validate at top, main logic at bottom — reduce nesting

### 20.3 Error Handling

- Use exceptions, not error codes or null returns

- Define custom exception hierarchy: ResourceNotFoundException, ValidationException, ServiceException

- Do not return null — return Optional or empty collection

- Do not pass null as argument — document @NonNull parameters

- Centralise error handling: @ControllerAdvice; do not scatter try-catch

### 20.4 Comments

- Prefer self-documenting code over comments

- Comments lie: code changes; comments often do not — outdated comments mislead

- Good comments: explaining WHY (not what), TODO/FIXME with ticket reference, Javadoc on public APIs

- Bad comments: restating what the code does, commented-out code

### 20.5 Layered Architecture Standards

- Controller: HTTP concerns only — no business logic, no SQL

- Service: business logic — orchestrates repositories; annotated with @Service and @Transactional

- Repository: data access only — no business rules

- Entity: database mapping only — minimal logic, no Spring annotations

- DTO: API contract — no persistence annotations

- Mapper: conversion between entity and DTO — no business logic

- Package structure: tech.csm.controller, tech.csm.service, tech.csm.repository, tech.csm.entity, tech.csm.dto, tech.csm.mapper, tech.csm.config, tech.csm.exception, tech.csm.security

### 20.6 Code Smells and Refactoring

- Long method: extract sub-methods

- Large class: split responsibilities into multiple classes

- Duplicate code: extract to a shared method or utility class

- Feature envy: method uses another class\'s data more than its own — move it

- Primitive obsession: replace with domain objects (use Money class, not double amount)

- Magic numbers: replace with named constants — MAX_RETRY_COUNT = 3

- Switch statements on type: replace with polymorphism

- God object: break into smaller focused classes

### 20.7 Project Architecture Patterns

#### Layered Architecture

- Presentation → Service → Repository → Database — strict top-down dependency

- Each layer depends only on the layer directly below it

#### Hexagonal Architecture (Ports and Adapters)

- Domain at the centre; outward dependencies only; no framework imports in domain

- Ports: interfaces defining what the domain needs

- Adapters: implementations of ports — REST adapter, JPA adapter, email adapter

#### Real-World Project Structure Reference

- tech.csm.config — Spring configuration classes, security config, Swagger config

- tech.csm.controller — REST controllers only

- tech.csm.service — business logic interfaces and implementations

- tech.csm.repository — Spring Data JPA repositories

- tech.csm.entity — JPA entity classes

- tech.csm.dto — request and response DTOs

- tech.csm.mapper — MapStruct mapper interfaces

- tech.csm.exception — custom exception classes and global exception handler

- tech.csm.security — JWT filter, UserDetails implementation, security utilities

- tech.csm.util — utility classes

---

## Module 21 — Build, Deployment, and CI/CD

### 21.1 Advanced Maven

- Multi-module Maven: parent pom.xml with modules; shared dependency management

- Maven profiles for build configuration: mvn package -Pprod

- Build lifecycle customization with plugins and execution bindings

- Maven Wrapper (mvnw): ships Maven version with project; no global Maven install required

- Release management: maven-release-plugin for tagging and versioning

- Dependency management for security: check for known vulnerabilities with OWASP Dependency Check plugin

- Enforcer plugin: fail build if Java version or dependency version constraints are violated

### 21.2 Spring Boot Fat JAR Packaging

- spring-boot-maven-plugin: repackages the jar with spring-boot-repackage goal

- Executable JAR structure: BOOT-INF/classes, BOOT-INF/lib, META-INF, org/springframework/boot/loader

- Running: java -jar target/app-0.0.1-SNAPSHOT.jar

- Passing properties: java -jar app.jar --server.port=9090 --spring.profiles.active=prod

- JVM tuning for production: -Xmx512m -XX:+UseG1GC -XX:MaxGCPauseMillis=200

- WAR packaging for external Tomcat: change packaging to war, extend SpringBootServletInitializer

### 21.3 Environment Variables and Externalised Configuration

- Spring property source priority: command-line args > environment variables > application.properties > default

- Environment variables: SPRING_DATASOURCE_URL, SPRING_DATASOURCE_PASSWORD

- Config server: Spring Cloud Config for centralised configuration across services

- Secrets management: never store secrets in code or properties files committed to git

- Use Vault, AWS Secrets Manager, Kubernetes Secrets, or environment variable injection

### 21.4 CI/CD Concepts

- Continuous Integration (CI): every commit triggers automated build, test, and static analysis

- Continuous Delivery (CD): every passing CI build is deployable to staging automatically

- Continuous Deployment: successful staging tests trigger automated production deployment

- CI/CD pipeline stages: Source → Build → Test → Security Scan → Package → Deploy

- GitHub Actions: .github/workflows/pipeline.yml defines CI/CD workflow in YAML

- Jenkins: widely used self-hosted CI/CD server; Jenkinsfile defines pipeline as code

- GitLab CI: .gitlab-ci.yml; tightly integrated with GitLab repository

- Artifact: built JAR stored in Nexus/Artifactory for deployment traceability

### 21.5 GitHub Actions Pipeline Example

- Trigger: on push to main or on pull request to main

- Jobs: checkout code, set up Java, run mvn clean verify, build Docker image, push to registry, deploy to server

- Secrets: GitHub repository secrets for DOCKER_USERNAME, DOCKER_PASSWORD, SERVER_HOST, SSH_KEY

- Matrix builds: test on multiple Java versions or OS combinations

- Caching: cache ~/.m2 directory to speed up subsequent builds

---

## Module 22 — Docker and Containerisation

### 22.1 Container Concepts

- Container: isolated process with its own filesystem, network, and resources

- Container vs VM: containers share host OS kernel; VMs include full OS — containers much lighter

- Image: read-only template for containers; built from a Dockerfile

- Container: running instance of an image

- Docker Hub: public image registry — pull official images (mysql:8, openjdk:17)

- Docker daemon: background service managing images and containers

- Docker CLI: client communicating with daemon — docker build, run, push, pull, ps, logs

### 22.2 Dockerfile for Spring Boot

- Base image: FROM openjdk:17-jdk-slim or FROM eclipse-temurin:17-jre-alpine

- WORKDIR /app — set working directory

- COPY target/app.jar app.jar — copy built JAR

- EXPOSE 8080 — document container port (does not publish it)

- ENTRYPOINT [\"java\", \"-jar\", \"app.jar\"] — command to run on container start

- Multi-stage builds: build stage with JDK, final stage with JRE — smaller production image

- Layer caching: COPY pom.xml, RUN mvn dependency:resolve before COPY src — cache deps layer

- Non-root user: RUN adduser appuser && USER appuser — run as non-root for security

- .dockerignore: exclude target/, .git/, *.log to speed up build and reduce image size

### 22.3 Docker Commands

- docker build -t myapp:1.0 . — build image from Dockerfile in current directory

- docker run -p 8080:8080 --name myapp myapp:1.0 — run container

- docker run -d — run in detached (background) mode

- docker run -e SPRING_PROFILES_ACTIVE=prod — pass environment variables

- docker run -e SPRING_DATASOURCE_PASSWORD=secret — pass secrets via env var

- docker ps — list running containers; docker ps -a — include stopped

- docker logs myapp — view container logs; docker logs -f myapp — follow logs

- docker exec -it myapp /bin/sh — open shell inside running container

- docker stop myapp; docker rm myapp — stop and remove container

- docker images — list images; docker rmi myapp:1.0 — remove image

- docker push username/myapp:1.0 — push to registry (after docker login)

### 22.4 Docker Compose

- docker-compose.yml: multi-container application definition in YAML

- Define services: app (Spring Boot), db (MySQL), redis (cache)

- Networks: containers in same network can reach each other by service name

- Volumes: persist database data outside container lifecycle

- Environment variables in compose: environment: - SPRING_DATASOURCE_URL=jdbc:mysql://db:3306/mydb

- depends_on: db — start db service before app service

- docker compose up -d — start all services detached

- docker compose down — stop and remove containers; docker compose down -v — also remove volumes

- docker compose logs -f app — tail logs for specific service

- healthcheck: configure health check for dependency readiness

### 22.5 Spring Profiles with Docker

- Pass active profile via environment variable: -e SPRING_PROFILES_ACTIVE=prod

- application-prod.properties: reads from environment variables for credentials

- spring.datasource.password=${DB_PASSWORD} in application-prod.properties

- Never bake credentials into Docker image — use env vars or Docker secrets

- Docker secrets: swarm-mode feature for sensitive values; alternative: Kubernetes Secrets

---

## Module 23 — Real-World Project Practices

### 23.1 Full-Stack Backend Project Structure

- Apply all previous modules together: Spring Boot REST + JPA + Security + Lombok + MapStruct + Validation

- Feature-based modularisation at scale: tech.csm.user.*, tech.csm.order.*

- Common shared packages: tech.csm.common.exception, tech.csm.common.dto, tech.csm.common.util

- API versioning from day one: /api/v1/**

- Database migration: Flyway or Liquibase for versioned, repeatable schema changes

- schema.sql and data.sql only for test and dev; never run DDL in production except via migration tool

### 23.2 Database Migration with Flyway

- spring-boot-starter-flyway dependency: auto-runs migrations at startup

- Migration scripts in src/main/resources/db/migration/

- Naming: V1__create_users_table.sql, V2__add_status_column.sql — V{version}__{description}.sql

- flyway_schema_history table: tracks which migrations have run

- Repeatable migrations: R__{description}.sql — re-runs if checksum changes (views, stored procs)

- Never modify a committed migration — add a new migration instead

- spring.jpa.hibernate.ddl-auto=none when using Flyway — let Flyway manage schema

### 23.3 Production-Ready REST API Checklist

- Authentication: JWT with short-lived access token + refresh token

- Authorisation: role-based and resource-based access control

- Input validation: @Valid on all request bodies

- Error handling: @ControllerAdvice with consistent JSON error format

- Logging: structured logging with request ID in every log line via MDC

- API documentation: Swagger/OpenAPI auto-generated

- Health endpoint: /actuator/health for load balancer probes

- Database connection pool: HikariCP configured with proper pool size

- No credentials in code: all secrets via environment variables or secrets manager

- HTTPS only: configure SSL certificate or terminate TLS at load balancer

### 23.4 Working on a Team Codebase

- Always pull before creating a new branch: git pull origin main

- One feature per branch; branch name matches ticket: feature/JIRA-123-add-user-search

- Write descriptive commit messages: feat(user): add email uniqueness validation

- Resolve merge conflicts locally before pushing

- Code review etiquette: review for correctness, performance, security, and readability

- Never push directly to main or develop — use pull requests

- Run tests before pushing: mvn clean verify

### 23.5 Performance and Scalability Fundamentals

- Database queries: use EXPLAIN to verify index usage; avoid SELECT *; paginate all list endpoints

- Connection pooling: right-size HikariCP pool; too many connections overwhelm DB

- Caching strategies:

  - Cache-aside: application checks cache; on miss, reads DB and populates cache

  - Write-through: write to cache and DB simultaneously

  - Read-through: cache fills itself on miss by calling data source

- Spring Cache: @EnableCaching + @Cacheable(\"users\") + @CacheEvict on update/delete

- Asynchronous processing: @EnableAsync + @Async on methods for background tasks

- N+1 prevention: review all @OneToMany and @ManyToMany with JOIN FETCH or @EntityGraph

- HTTP caching: ETag, Last-Modified, Cache-Control headers for read-heavy endpoints

### 23.6 Security Hardening

- OWASP Top 10 awareness: Injection, Broken Auth, Broken Access Control, Security Misconfiguration, IDOR

- SQL injection: use PreparedStatement or JPA — never string-concatenate SQL

- XSS prevention: encode output in HTML contexts; use Content-Security-Policy header

- CSRF: disable for stateless JWT APIs; enable for session-based form apps

- Insecure direct object reference: validate ownership before returning resource

- Rate limiting: bucket4j or custom filter to throttle requests per user/IP

- Dependency scanning: OWASP Dependency Check Maven plugin in CI pipeline

- HTTPS and HSTS: Strict-Transport-Security header to force HTTPS

- Sensitive data in logs: never log passwords, tokens, card numbers — mask before logging

### 23.7 Introduction to Microservices (Conceptual)

- Monolith vs Microservices: monolith first; extract services when clear domain boundary and scale need

- Service registry: Eureka or Consul — services register; clients discover by service name

- API Gateway: Spring Cloud Gateway — single entry point; routing, auth, rate limiting

- Inter-service communication: synchronous (REST, OpenFeign) or asynchronous (Kafka, RabbitMQ)

- Circuit breaker pattern: Resilience4j — stop calling a failing service; return fallback

- Distributed tracing: correlate logs across services with trace ID and span ID

- CAP theorem: a distributed system can have at most two of: Consistency, Availability, Partition Tolerance

- Eventual consistency: accept that distributed data may be temporarily inconsistent; design for it

- Saga pattern: managing distributed transactions across services via compensating transactions

### 23.8 Messaging with Kafka and RabbitMQ (Overview)

#### Apache Kafka

- Distributed log: messages persisted, replayable, ordered within partition

- Topic: named channel; Partition: ordered sub-sequence within topic; Consumer Group: scalable parallel consumption

- Producers write to topics; consumers read from topics — decoupled

- spring-kafka: @KafkaListener for consuming, KafkaTemplate for producing

- Use Kafka for: event streaming, audit log, real-time analytics, event sourcing

#### RabbitMQ

- Message broker: messages routed through exchanges to queues

- Exchange types: direct (routing key), fanout (broadcast), topic (wildcard pattern)

- spring-rabbit: @RabbitListener for consuming, RabbitTemplate for producing

- Use RabbitMQ for: task queues, work distribution, notifications, RPC-style async calls

#### Choosing Between Them

- Kafka: high throughput, message replay needed, event sourcing, data pipeline

- RabbitMQ: complex routing, per-message acknowledgement, flexible topology, lower throughput
