**Java + Spring Boot**

Training Programme --- Complete Syllabus

*25 Modules · Full-Stack Java Backend Development · Enterprise-Grade Curriculum*

**Technology Stack**

  ----------------- --------------------- ----------------- -----------------
  **Java 17/21**    **Spring Boot 4.x**   **MySQL / JPA**   **Maven**

  Spring Security   Hibernate/JPA         JWT / OAuth2      Git / Docker
  ----------------- --------------------- ----------------- -----------------

*Consolidated & Reviewed 2025 · Package Convention: com.org.\**

+-----------------------------------------------------------------------+
| Module 1 \| **Development Environment Setup**                         |
|                                                                       |
| *JDK, IDE, STS, Lombok, Shortcuts, Debugging*                         |
+-----------------------------------------------------------------------+

**1.1 Java Development Kit (JDK)**

-   Download and install JDK 17 or JDK 21 (LTS) from Oracle or OpenJDK

-   Set JAVA_HOME environment variable

-   Add JDK bin directory to system PATH

-   Verify: java -version and javac -version

-   Difference between JVM, JRE, and JDK

**1.2 Spring Tool Suite (STS) / Eclipse IDE**

-   Download STS from spring.io or install as Eclipse plugin

-   Install plugins via Eclipse Marketplace: JSON Editor, Maven Helper, YAML Editor

-   Workspace encoding: UTF-8 globally

-   Line endings: Unix LF for cross-platform consistency

-   Code formatter and save actions: auto-format, auto-organize imports on save

**1.3 Maven Integration**

-   Auto-build Maven projects on save

-   Download dependencies automatically on pom.xml changes

-   Project → Clean to rebuild workspace

-   Fix corrupt Maven cache: clear .m2/repository, re-run Maven update

-   Alt+F5: Update Maven Project after pom.xml edit

**1.4 Creating First Spring Boot Project**

-   File → New → Spring Starter Project inside STS

-   Select Java version, packaging (JAR), build tool (Maven)

-   Add initial dependencies: Spring Web, Spring Data JPA, MySQL Driver, Lombok

-   Understand generated pom.xml: parent, dependencies, spring-boot-maven-plugin

-   Generated main application class and \@SpringBootApplication

-   Import existing Maven projects: File → Import → Maven → Existing Maven Project

**1.5 Lombok Setup**

-   Install Lombok: run lombok.jar installer pointing to STS/Eclipse executable

-   Add Lombok dependency to pom.xml

-   Verify: generated getters and setters appear without explicit code

-   Common issue: lombok.jar not found --- re-run installer after IDE update

**1.6 STS Productivity Features**

-   \@Autowired hover: shows injected bean and source location

-   REST endpoint hover: preview URL and method

-   Boot Dashboard: start/stop apps, view actuator endpoints, tail logs

-   Spring DevTools: automatic restart on classpath changes

-   Opening all request mappings from the Boot Dashboard

**1.7 Keyboard Shortcuts**

-   Ctrl+Shift+R --- Open resource (any file)

-   Ctrl+Shift+T --- Open type (any class)

-   Alt+Shift+R --- Rename with full refactor

-   Ctrl+1 --- Quick fix: auto-import, create method, assign to field

-   Ctrl+Shift+O --- Organize imports

-   Ctrl+Space --- Smart content assist

-   F3 --- Go to declaration

-   Alt+Shift+M --- Extract method

-   Alt+Shift+L --- Extract local variable

**1.8 Debugging**

-   Set breakpoint: click gutter next to line number

-   Debug As → Spring Boot App

-   Step Over (F6), Step Into (F5), Step Return (F7), Resume (F8)

-   Variables view and Expressions view for inspecting state

-   Conditional breakpoints: right-click → Breakpoint Properties

-   Inspect HTTP request/response in controller breakpoints

**1.9 Common IDE Problems and Fixes**

-   Port already in use: kill process or change server.port in application.properties

-   IDE out-of-memory: increase heap in eclipse.ini (-Xmx2g)

-   Lombok not working: re-run installer, clean project, restart IDE

-   Red markers after Maven import: Project → Clean, then Maven → Update Project

+-----------------------------------------------------------------------+
| Module 2 \| **Maven Essentials**                                      |
|                                                                       |
| *Build automation, pom.xml, lifecycle, dependency scopes*             |
+-----------------------------------------------------------------------+

**2.1 What Maven Does**

-   Dependency management: declares libraries in pom.xml, Maven downloads from Maven Central

-   Build automation: compiles, tests, packages, installs in a repeatable way

-   Standard project structure: src/main/java, src/main/resources, src/test/java, src/test/resources

-   Convention over configuration: works without custom config when you follow conventions

**2.2 pom.xml Structure**

-   GAV coordinates: groupId, artifactId, version

-   packaging: jar (default for Spring Boot) or war

-   parent element: spring-boot-starter-parent provides dependency management defaults

-   properties: java.version, encoding, custom version variables

-   dependencies: each has groupId, artifactId, version, optional scope

-   dependencyManagement: centralise version control without pulling dependency in

-   build/plugins section: configure Maven plugins

**2.3 Build Lifecycle**

-   Default lifecycle: validate → compile → test → package → verify → install → deploy

-   clean lifecycle: removes target/ directory

-   mvn clean install --- clean, compile, test, package, install JAR to \~/.m2

-   mvn clean package --- produce JAR/WAR without installing to local repo

-   mvn clean package -DskipTests --- skip test execution during build

-   mvn spring-boot:run --- run Spring Boot app directly via Maven plugin

-   mvn dependency:tree --- show full dependency graph including transitive dependencies

**2.4 Dependency Scopes**

-   compile --- on classpath everywhere, bundled in JAR (default scope)

-   test --- only available in test code; not bundled (JUnit, Mockito, H2)

-   provided --- compile-time only, container provides at runtime (Servlet API)

-   runtime --- not needed to compile, needed at runtime; bundled (MySQL JDBC driver)

-   Transitive dependencies: Maven brings in A\'s dependencies when you depend on A

-   Excluding transitive dependencies using \<exclusions\>\<exclusion\>

**2.5 Key Plugins**

-   maven-compiler-plugin: sets source and target Java version

-   spring-boot-maven-plugin: repackages JAR into fat/uber JAR with embedded Tomcat

-   maven-surefire-plugin: executes unit tests during the test phase

-   Running a Spring Boot fat JAR: java -jar target/app-0.0.1-SNAPSHOT.jar

**2.6 Multi-Module Projects**

-   Parent POM aggregator with \<modules\> section

-   Child modules inherit dependency management from parent

-   Common use: shared-lib, service-a, service-b as separate Maven modules

-   **★ Packaging hierarchy: parent pom, child jar --- build with single mvn install at root**

+-----------------------------------------------------------------------+
| Module 3 \| **Java Programming Fundamentals**                         |
|                                                                       |
| *Syntax, data types, operators, control flow, exception handling*     |
+-----------------------------------------------------------------------+

**3.1 Java Overview**

-   JVM, JRE, JDK differences --- compilation and execution model

-   Platform independence: Write Once, Run Anywhere (bytecode → JVM)

-   Java versions: LTS releases (11, 17, 21) and relevant features per version

-   First Java program: public class, main method, System.out.println

-   Compilation process: javac → .class bytecode, java → execution

**3.2 Basic Syntax and Structure**

-   Class declaration, method definitions, code blocks and scope

-   Packages and import statements; static imports

-   Naming conventions: PascalCase (classes), camelCase (methods/variables), UPPER_CASE (constants)

-   Javadoc comments: /\*\* \*/ with \@param, \@return, \@throws tags

-   Source file structure rules: public class name must match filename

**3.3 Variables and Data Types**

-   Primitive types: byte, short, int, long, float, double, char, boolean

-   Reference types: String, arrays, objects, wrapper classes (Integer, Double, etc.)

-   Variable declaration, initialization, type inference with var (Java 10+)

-   Variable scope: local, instance, class (static), parameter variables

-   Autoboxing and unboxing: automatic primitive-wrapper conversion

-   Type casting: widening (implicit), narrowing (explicit), String conversion

-   Common pitfalls: floating-point precision, integer overflow, NullPointerException

**3.4 Operators**

-   Arithmetic: +, -, \*, /, % --- integer division vs floating-point division

-   Increment/decrement: prefix (++x) vs postfix (x++)

-   Relational: ==, !=, \>, \<, \>=, \<= --- null-safe comparison

-   Logical: &&, \|\|, ! --- short-circuit evaluation

-   Bitwise: &, \|, \^, \~, \<\<, \>\>, \>\>\>

-   Ternary: condition ? value1 : value2

-   instanceof and pattern matching with instanceof (Java 14+)

-   Operator precedence and associativity table

**3.5 Control Flow**

-   if, if-else, if-else-if ladder; nested if

-   switch statement (traditional and enhanced, Java 14+) with switch expressions and yield

-   for loop, enhanced for-each loop, while, do-while; nested loops

-   break (with/without label), continue (with/without label), return

-   Avoid deep nesting: early returns and guard clauses

-   Control flow in try-catch-finally blocks

**3.6 Exception Handling**

-   Checked vs unchecked exceptions --- when to use each

-   try-catch-finally block; try-with-resources (AutoCloseable)

-   throw and throws keywords; re-throwing exceptions

-   Custom exception classes: extending Exception vs RuntimeException

-   Multi-catch blocks: catch (IOException \| SQLException e)

-   Exception chaining: new RuntimeException(\"msg\", cause)

-   **★ Best practices: never swallow exceptions silently, log and rethrow or handle meaningfully**

-   **★ Exception hierarchy: Throwable → Error / Exception → RuntimeException**

+-----------------------------------------------------------------------+
| Module 4 \| **Object-Oriented Programming**                           |
|                                                                       |
| *Classes, OOP pillars, SOLID principles, design patterns*             |
+-----------------------------------------------------------------------+

**4.1 Classes and Objects**

-   Class declaration: fields, methods, constructors

-   Creating objects with new keyword; memory allocation

-   Default constructor, parameterized constructor, constructor overloading

-   Constructor chaining with this(); super() call

-   The this keyword: current object reference, disambiguation

**4.2 Encapsulation**

-   Access modifiers: private, default (package-private), protected, public

-   Getters and setters; validation in setters; read-only and write-only properties

-   Java Beans convention: properties naming, default constructor, Serializable

-   Immutable classes: final fields, defensive copying, no setters

**4.3 Inheritance**

-   extends keyword; IS-A relationship; superclass and subclass

-   Method overriding: \@Override annotation, covariant return types, access widening

-   super keyword: accessing superclass methods and constructors

-   Types: single, multilevel, hierarchical; multiple inheritance via interfaces

-   Object class: toString(), equals(), hashCode() --- equals/hashCode contract

**4.4 Polymorphism**

-   Compile-time: method overloading

-   Runtime: method overriding, dynamic method dispatch, virtual method invocation

-   Reference variables and object types; upcasting and downcasting

-   instanceof operator and pattern matching (Java 14+)

**4.5 Abstraction**

-   Abstract classes: abstract keyword, abstract methods, concrete methods

-   Interfaces: constant declarations, method declarations, implements keyword

-   Interface evolution: default methods (Java 8), static methods (Java 8), private methods (Java 9)

-   Functional interfaces and \@FunctionalInterface annotation

-   Sealed classes and interfaces (Java 17+): sealed, non-sealed, permits

**4.6 Advanced OOP**

-   Composition vs Inheritance --- HAS-A relationship; prefer composition over inheritance

-   final: variables (constants), methods (cannot override), classes (cannot extend)

-   static members: class variables, static methods, static blocks, static nested classes

-   Nested classes: static nested, inner, local, anonymous

-   Records (Java 16+): data carrier classes with auto-generated methods

**4.7 SOLID Principles**

-   Single Responsibility Principle (SRP): one class, one reason to change

-   Open/Closed Principle (OCP): open for extension, closed for modification

-   Liskov Substitution Principle (LSP): subtypes must be substitutable for their base types

-   Interface Segregation Principle (ISP): no client should depend on unused methods

-   Dependency Inversion Principle (DIP): depend on abstractions, not concretions

**4.8 Object Creation Patterns**

-   Factory method and static factory patterns

-   Singleton pattern: thread-safe implementation with enum or double-checked locking

-   Builder pattern for complex objects

-   **★ Anti-patterns: God classes, circular dependencies, anemic domain model**

+-----------------------------------------------------------------------+
| Module 5 \| **Core Java APIs**                                        |
|                                                                       |
| *Strings, Collections, Generics, I/O, Multithreading, Reflection*     |
+-----------------------------------------------------------------------+

**5.1 String Handling**

-   String immutability; String pool and interning

-   Common methods: length(), charAt(), equals(), compareTo(), indexOf(), substring(), replace(), split(), join()

-   StringBuilder and StringBuffer: append(), insert(), delete(), reverse()

-   String.format() and System.out.printf()

-   Text Blocks (Java 15+) for multi-line strings

-   String comparison pitfall: == vs equals()

**5.2 Collections Framework**

-   Collection hierarchy: Collection, List, Set, Queue, Deque, Map

-   List: ArrayList, LinkedList, Vector, Stack

-   Set: HashSet, LinkedHashSet, TreeSet

-   Queue / Deque: PriorityQueue, ArrayDeque

-   Map: HashMap, LinkedHashMap, TreeMap, Hashtable

-   Collections utility class: sort(), binarySearch(), synchronizedList(), unmodifiableList()

-   Factory methods (Java 9+): List.of(), Set.of(), Map.of(), Map.ofEntries()

-   Enhanced methods (Java 8+): removeIf(), computeIfAbsent(), merge(), getOrDefault()

**5.3 Generics**

-   Type safety; compile-time type checking; eliminating casts

-   Generic classes, interfaces, and methods

-   Bounded type parameters: \<T extends Comparable\<T\>\>

-   Wildcards: \<?\>, \<? extends Type\>, \<? super Type\>

-   Type erasure: bridge methods and limitations

**5.4 I/O and NIO.2**

-   Byte streams: FileInputStream, FileOutputStream

-   Character streams: FileReader, FileWriter, BufferedReader, BufferedWriter

-   Object serialization: Serializable interface, ObjectInputStream, ObjectOutputStream

-   NIO.2 Path API: Paths.get(), Files.readAllLines(), Files.write()

-   try-with-resources pattern for guaranteed resource cleanup

**5.5 Multithreading and Concurrency**

-   Process vs Thread; Thread states and lifecycle

-   Creating threads: Thread subclass, Runnable, Callable

-   synchronized keyword: methods and blocks; volatile keyword

-   Executor framework: ExecutorService, ThreadPoolExecutor

-   Future and CompletableFuture (Java 8+)

-   Concurrent collections: ConcurrentHashMap, CopyOnWriteArrayList, BlockingQueue

-   Deadlock, livelock, starvation --- detection and prevention

-   **★ Virtual Threads (Project Loom, Java 21+): Thread.ofVirtual() for high-concurrency**

**5.6 Annotations and Reflection**

-   Built-in annotations: \@Override, \@Deprecated, \@SuppressWarnings, \@FunctionalInterface

-   Custom annotations: declaration, retention policies, target elements

-   Reflection API: Class, getDeclaredFields(), getDeclaredMethods(), dynamic invocation

-   Dynamic Proxy creation and usage

+-----------------------------------------------------------------------------------+
| Module 6 \| **Java 8+ Functional Features**                                       |
|                                                                                   |
| *Lambdas, Streams, Optional, Functional Interfaces --- essential for Spring Boot* |
+-----------------------------------------------------------------------------------+

**6.1 Lambda Expressions**

-   Syntax: (parameters) -\> expression and (parameters) -\> { body }

-   Effectively final variables in lambda scope

-   Method references: Class::method, instance::method, Class::new

-   Lambda vs anonymous inner class: when to use which

**6.2 Functional Interfaces**

-   Function\<T,R\>: apply()

-   Consumer\<T\>: accept()

-   Supplier\<T\>: get()

-   Predicate\<T\>: test(), and(), or(), negate()

-   BiFunction\<T,U,R\>, BiConsumer, BiPredicate

-   UnaryOperator\<T\>, BinaryOperator\<T\>

-   Composing functions: andThen(), compose()

-   **★ Custom functional interfaces: \@FunctionalInterface with single abstract method**

**6.3 Stream API**

-   Stream creation: collection.stream(), Stream.of(), Stream.generate(), Stream.iterate()

-   Intermediate operations: filter(), map(), flatMap(), distinct(), sorted(), limit(), skip(), peek()

-   Terminal operations: collect(), forEach(), count(), findFirst(), anyMatch(), allMatch(), noneMatch(), reduce()

-   Collectors: toList(), toSet(), joining(), groupingBy(), partitioningBy(), counting(), summarizingInt()

-   Parallel streams: parallelStream() --- when to use and when to avoid

-   Stream vs Collection: lazy evaluation, single-use nature

-   **★ Stream.toList() (Java 16+) vs Collectors.toList() --- immutability difference**

**6.4 Optional**

-   Creating: Optional.of(), Optional.ofNullable(), Optional.empty()

-   Checking: isPresent(), isEmpty() (Java 11+), ifPresent()

-   Extracting: get(), orElse(), orElseGet(), orElseThrow()

-   Transforming: map(), flatMap(), filter()

-   **★ Optional as return type only --- do not use as parameter or field type**

-   **★ Anti-pattern: Optional.get() without isPresent() check**

**6.5 Date and Time API (Java 8+)**

-   Problems with legacy Date and Calendar

-   LocalDate, LocalTime, LocalDateTime --- immutable date/time objects

-   ZonedDateTime and ZoneId for timezone-aware data

-   DateTimeFormatter: format() and parse()

-   Period (date difference) and Duration (time difference)

-   Instant for machine timestamps; converting to/from legacy Date

-   **★ Why always store UTC in database, convert to local timezone at display layer**

+-----------------------------------------------------------------------+
| Module 7 \| **Git and Version Control**                               |
|                                                                       |
| *Core Git operations, branching, GitHub, team workflows*              |
+-----------------------------------------------------------------------+

**7.1 Git Fundamentals**

-   What is Version Control? Centralized vs Distributed VCS

-   Installing Git; initial configuration: user.name, user.email

-   Repository basics: local and remote

-   Working directory → Staging area → Repository model

**7.2 Core Git Operations**

-   git init; git clone

-   git add, git commit, git status, git log

-   Viewing diffs: git diff, git show

-   Undoing changes: git reset, git restore, git revert

**7.3 Branching and Merging**

-   Creating and switching branches: git branch, git checkout, git switch

-   Fast-forward vs non-fast-forward merges

-   Merge conflicts: detection and resolution

-   git rebase --- linearizing history; when to use vs merge

-   Branch deletion: local and remote

**7.4 GitHub and Remote Repositories**

-   Adding remotes: git remote add origin

-   git push, git pull, git fetch

-   SSH vs HTTPS authentication

-   Fork and clone workflow

-   Pull Requests and code review process

**7.5 Team Workflows and Best Practices**

-   Git Flow: main, develop, feature/\*, hotfix/\*

-   Trunk-based development: short-lived feature branches

-   Commit message conventions: feat(scope): description

-   .gitignore: excluding target/, \*.class, .env

-   Protected branches and required PR approvals

-   **★ Semantic versioning: MAJOR.MINOR.PATCH --- when to bump each**

+---------------------------------------------------------------------------+
| Module 8 \| **SQL and MySQL Fundamentals**                                |
|                                                                           |
| *Relational model, DDL/DML, joins, indexing, normalization, transactions* |
+---------------------------------------------------------------------------+

**8.1 Relational Database Concepts**

-   Tables, rows (records), columns (attributes)

-   Primary key, foreign key, unique constraint, not null constraint

-   Candidate key, composite key, surrogate vs natural key

-   Entity-Relationship (ER) diagrams and schema design

**8.2 DDL --- Data Definition Language**

-   CREATE TABLE with data types: INT, VARCHAR, TEXT, DATE, DATETIME, DECIMAL, BOOLEAN

-   ALTER TABLE: add/drop/modify columns

-   DROP TABLE, TRUNCATE TABLE vs DELETE

-   Constraints: PRIMARY KEY, FOREIGN KEY, UNIQUE, NOT NULL, DEFAULT, CHECK

-   AUTO_INCREMENT for surrogate primary keys

**8.3 DML --- Data Manipulation Language**

-   INSERT INTO: single and multi-row inserts

-   SELECT: columns, WHERE, ORDER BY, GROUP BY, HAVING, LIMIT

-   UPDATE with WHERE clause --- always include WHERE to avoid full-table update

-   DELETE with WHERE clause

-   Aggregate functions: COUNT(), SUM(), AVG(), MIN(), MAX()

**8.4 Joins**

-   INNER JOIN: only matching rows from both tables

-   LEFT JOIN: all rows from left, matched rows from right

-   RIGHT JOIN: all rows from right, matched rows from left

-   CROSS JOIN: Cartesian product

-   Self-join: joining a table to itself

-   Multi-table joins: chaining JOIN ON conditions

**8.5 Subqueries and Advanced Queries**

-   Scalar subquery in SELECT and WHERE

-   IN, NOT IN, EXISTS, NOT EXISTS

-   Correlated subqueries

-   UNION vs UNION ALL

-   **★ Common Table Expressions (CTEs): WITH clause for readable complex queries**

**8.6 Indexes**

-   What is an index and why it speeds up queries

-   B-Tree index: default index type in MySQL

-   CREATE INDEX, DROP INDEX; composite indexes

-   EXPLAIN: reading query execution plan

-   When not to index: low-cardinality columns, heavily updated tables

**8.7 Normalization**

-   1NF: atomic values, no repeating groups

-   2NF: no partial dependency on composite primary key

-   3NF: no transitive dependency on non-key column

-   When to denormalize for performance

**8.8 Transactions**

-   ACID properties: Atomicity, Consistency, Isolation, Durability

-   BEGIN, COMMIT, ROLLBACK

-   Isolation levels: READ UNCOMMITTED, READ COMMITTED, REPEATABLE READ, SERIALIZABLE

-   Dirty read, non-repeatable read, phantom read --- what each isolation level prevents

**8.9 Stored Procedures, Views, and Triggers**

-   Views: CREATE VIEW for reusable query logic

-   Stored procedures: CREATE PROCEDURE, IN/OUT parameters, CALL

-   Triggers: BEFORE/AFTER INSERT/UPDATE/DELETE

-   **★ When to use stored procedures vs application-layer logic**

+-------------------------------------------------------------------------------+
| Module 9 \| **JDBC --- Java Database Connectivity**                           |
|                                                                               |
| *JDBC architecture, CRUD, transactions, batch operations, connection pooling* |
+-------------------------------------------------------------------------------+

**9.1 JDBC Architecture**

-   JDBC driver types; DriverManager

-   Connection, Statement, PreparedStatement, CallableStatement

-   ResultSet: navigation, types (scrollable, updatable)

-   ResultSetMetaData and DatabaseMetaData

**9.2 CRUD with JDBC**

-   Establishing connection: DriverManager.getConnection(url, user, pass)

-   Executing queries: executeQuery() vs executeUpdate()

-   Preventing SQL injection with PreparedStatement --- always use parameterized queries

-   Reading ResultSet: rs.next(), rs.getInt(), rs.getString()

-   Insert, update, delete operations with PreparedStatement

**9.3 Advanced JDBC**

-   Batch operations: addBatch(), executeBatch() for bulk inserts

-   Scrollable and updatable ResultSet

-   CallableStatement for stored procedures

-   Retrieving generated keys after INSERT

**9.4 Transactions and Savepoints**

-   Manual transaction control: conn.setAutoCommit(false)

-   commit() and rollback()

-   Savepoints for nested transaction control

-   Isolation levels via conn.setTransactionIsolation()

**9.5 Connection Pooling with HikariCP**

-   Why pooling: cost of establishing a new connection

-   HikariCP: fastest Java connection pool

-   Configuration: maximumPoolSize, minimumIdle, connectionTimeout, idleTimeout

-   Leak detection: leakDetectionThreshold

-   **★ Sizing the pool: too large overwhelms DB, too small causes wait queues**

**9.6 Project Structure Convention**

-   Package layout: entity, dao, service, util, driver (com.org.\*)

-   DAO interface + implementation separation

-   Service layer orchestrates business logic over DAO

-   Utility class for connection management (singleton DataSource)

+-----------------------------------------------------------------------+
| Module 10 \| **HTTP Protocol, Servlets, and JSP**                     |
|                                                                       |
| *HTTP lifecycle, Servlet API, session management, JSP, filters*       |
+-----------------------------------------------------------------------+

**10.1 HTTP Protocol**

-   Request/response model; stateless nature of HTTP

-   HTTP methods: GET, POST, PUT, DELETE, PATCH, OPTIONS, HEAD

-   Status codes: 2xx success, 3xx redirect, 4xx client error, 5xx server error

-   Request headers: Content-Type, Accept, Authorization, Cookie

-   Response headers: Content-Type, Location, Set-Cookie, Cache-Control

-   HTTP/1.1 vs HTTP/2: persistent connections, multiplexing

**10.2 Servlet Fundamentals**

-   What is a Servlet? javax.servlet.http.HttpServlet

-   Servlet lifecycle: init(), service(), destroy()

-   HttpServletRequest: getMethod(), getParameter(), getHeader(), getRequestURI()

-   HttpServletResponse: setStatus(), setContentType(), getWriter()

-   doGet() and doPost() method overrides

-   Servlet configuration: web.xml vs \@WebServlet annotation

**10.3 Session Management**

-   Cookies: creating, reading, expiry

-   HttpSession: getAttribute(), setAttribute(), invalidate()

-   URL rewriting for session tracking

-   Request attributes vs Session attributes vs Application attributes

**10.4 Request Dispatching**

-   RequestDispatcher: forward() vs include()

-   Redirect: response.sendRedirect() --- client-side vs server-side redirect

**10.5 Filters and Listeners**

-   Filter chain and filter ordering

-   doFilter() method and FilterChain.doFilter()

-   Use cases: logging, authentication, CORS, encoding

-   ServletContextListener, HttpSessionListener

**10.6 JSP Fundamentals**

-   JSP lifecycle: translation to servlet, compilation, execution

-   Implicit objects: request, response, session, application, out

-   Expression Language (EL): \${expression} syntax

-   JSTL core tags: c:if, c:forEach, c:set, c:out

-   Avoiding scriptlets: use EL and JSTL instead

+--------------------------------------------------------------------------------+
| Module 11 \| **Hibernate and JPA (ORM)**                                       |
|                                                                                |
| *Entity mapping, relationships, JPQL, caching, lazy loading, schema migration* |
+--------------------------------------------------------------------------------+

**11.1 ORM Fundamentals**

-   What is ORM? Object-Relational impedance mismatch

-   JPA (Java Persistence API) vs Hibernate: spec vs implementation

-   Entities and persistence context

-   EntityManager, EntityManagerFactory, Sessions and SessionFactory

**11.2 Entity Mapping**

-   \@Entity, \@Table(name), \@Id, \@GeneratedValue(strategy=\...)

-   Column mapping: \@Column(name, nullable, unique, length)

-   Primitive and object fields; \@Transient for non-persisted fields

-   Embedded types: \@Embeddable, \@Embedded

-   Enum mapping: \@Enumerated(EnumType.STRING)

**11.3 Relationships**

-   \@OneToOne --- foreign key placement, optional vs mandatory

-   \@OneToMany / \@ManyToOne --- mappedBy, owning side

-   \@ManyToMany --- join table, \@JoinTable

-   Cascade types: PERSIST, MERGE, REMOVE, ALL --- choose carefully

-   orphanRemoval: remove child when disassociated from parent

**11.4 Fetching Strategies**

-   LAZY loading: fetch when accessed (default for collections)

-   EAGER loading: fetch immediately with parent (default for \@ManyToOne, \@OneToOne)

-   N+1 problem: N additional queries for N parent rows

-   Solutions: JOIN FETCH in JPQL, \@EntityGraph, batch fetching

**11.5 JPQL and Criteria API**

-   JPQL: entity-oriented query language --- operates on objects not tables

-   Named queries: \@NamedQuery on entity class

-   Criteria API: type-safe programmatic query building

-   Native SQL queries: \@Query(nativeQuery=true)

**11.6 Hibernate Caching**

-   First-level cache: per-session, automatic, always enabled

-   Second-level cache: shared across sessions; requires cache provider (e.g., Ehcache)

-   Query cache: cache result sets of specific queries

**11.7 Database Migration with Flyway**

-   Why schema migrations: reproducible, version-controlled DB changes

-   Flyway: spring-boot-starter-flyway auto-runs migrations on startup

-   Migration scripts: src/main/resources/db/migration/V1\_\_description.sql

-   Naming convention: V{version}\_\_{description}.sql

-   flyway_schema_history table tracks applied migrations

-   Never modify a committed migration --- add a new one

-   spring.jpa.hibernate.ddl-auto=none when using Flyway

-   **★ Repeatable migrations: R\_\_{description}.sql --- re-runs if checksum changes (views, stored procs)**

+-----------------------------------------------------------------------------------------+
| Module 12 \| **Spring Core --- IoC, DI, and AOP**                                       |
|                                                                                         |
| *ApplicationContext, bean lifecycle, dependency injection, aspect-oriented programming* |
+-----------------------------------------------------------------------------------------+

**12.1 Spring Framework Introduction**

-   What problem Spring solves: loose coupling, testability, configuration

-   IoC (Inversion of Control) container

-   BeanFactory vs ApplicationContext

**12.2 Dependency Injection**

-   Constructor injection --- preferred: makes dependencies explicit, enables immutability

-   Setter injection --- optional dependencies

-   Field injection with \@Autowired --- convenient but hinders testability

-   \@Qualifier to resolve ambiguity when multiple beans of same type exist

-   \@Primary to designate default bean

**12.3 Bean Scope and Lifecycle**

-   Singleton (default): one instance per container

-   Prototype: new instance per request

-   Request / Session scopes for web applications

-   Bean initialization: \@PostConstruct, InitializingBean

-   Bean destruction: \@PreDestroy, DisposableBean

**12.4 Spring Configuration Styles**

-   XML-based configuration: \<bean\> declarations

-   Annotation-based: \@Component, \@Service, \@Repository, \@Controller

-   Java-based: \@Configuration, \@Bean, \@ComponentScan

-   \@PropertySource and \@Value for externalized configuration

**12.5 Spring AOP (Aspect-Oriented Programming)**

-   Cross-cutting concerns: logging, security, transactions, auditing

-   Core concepts: Aspect, Advice, Pointcut, Join Point, Weaving

-   Advice types: \@Before, \@After, \@AfterReturning, \@AfterThrowing, \@Around

-   Pointcut expressions: execution(), \@annotation(), within()

-   Spring AOP uses JDK dynamic proxy (interface) or CGLIB (class)

-   Practical example: execution time logging with \@Around

-   **★ \@Around vs \@Before/@After: \@Around has full control over method execution**

-   **★ Self-invocation bypass problem: AOP does not intercept internal method calls**

+-------------------------------------------------------------------------------+
| Module 13 \| **Spring MVC**                                                   |
|                                                                               |
| *DispatcherServlet, controllers, data binding, validation, JSP, interceptors* |
+-------------------------------------------------------------------------------+

**13.1 Spring MVC Architecture**

-   DispatcherServlet: front controller that routes all requests

-   HandlerMapping: maps URL to controller method

-   ViewResolver: resolves logical view name to template

-   Full request processing workflow

**13.2 Controllers and Request Mapping**

-   \@Controller vs \@RestController

-   \@RequestMapping, \@GetMapping, \@PostMapping, \@PutMapping, \@DeleteMapping

-   \@PathVariable, \@RequestParam, \@RequestHeader, \@RequestBody

-   Returning ModelAndView vs String view name

**13.3 Data Binding and Validation**

-   \@ModelAttribute: bind form fields to Java object

-   BindingResult: holds validation errors

-   \@Valid and \@Validated: trigger Bean Validation

-   Bean Validation (JSR-380): \@NotNull, \@NotBlank, \@Size, \@Min, \@Max, \@Email, \@Pattern

-   Displaying validation errors in JSP with spring:bind tag

**13.4 View Technologies**

-   JSP with JSTL: standard view layer for XML-configured Spring MVC

-   Thymeleaf: natural HTML templates, th:text, th:each, th:if

-   InternalResourceViewResolver configuration

**13.5 Interceptors and Exception Handling**

-   HandlerInterceptor: preHandle(), postHandle(), afterCompletion()

-   \@ControllerAdvice: global cross-controller exception handling

-   \@ExceptionHandler: handle specific exception types

-   Custom error views and status codes

**13.6 Spring MVC Project Structure**

-   XML-configured vs annotation-configured setup

-   Controller → Service → DAO layering

-   Spring JDBC Template integration in MVC context

-   **★ ModelAttribute for prepopulating form dropdowns (cascading dropdowns pattern)**

+-------------------------------------------------------------------------------------+
| Module 14 \| **Spring JDBC and Data Access**                                        |
|                                                                                     |
| *JdbcTemplate, NamedParameterJdbcTemplate, transaction management, Spring Data JPA* |
+-------------------------------------------------------------------------------------+

**14.1 Spring JDBC**

-   JdbcTemplate: eliminates boilerplate JDBC code

-   queryForObject(): single row, single value

-   query() with RowMapper: map ResultSet to object

-   update(): INSERT, UPDATE, DELETE

-   NamedParameterJdbcTemplate: named placeholders instead of ?

-   BeanPropertyRowMapper: automatic mapping when column names match field names

-   Exception translation: SQLExceptions → Spring DataAccessExceptions

**14.2 Spring Transaction Management**

-   \@Transactional: declarative transaction management

-   Propagation: REQUIRED, REQUIRES_NEW, SUPPORTS, MANDATORY, NESTED

-   Isolation levels: READ_COMMITTED, REPEATABLE_READ, SERIALIZABLE

-   Rollback rules: rollbackFor, noRollbackFor

-   \@Transactional on service layer, not DAO layer (standard practice)

-   **★ Self-invocation: \@Transactional not applied when method calls itself within same class (AOP limitation)**

**14.3 Spring Data JPA**

-   JpaRepository\<Entity, ID\>: extends CrudRepository and PagingAndSortingRepository

-   Derived query methods: findByUsername(), findByEmailAndStatus()

-   \@Query with JPQL: \@Query(\"SELECT u FROM User u WHERE u.email = :email\")

-   \@Query with nativeQuery=true for native SQL

-   \@Modifying + \@Transactional for update/delete \@Query methods

-   Pagination: Pageable, Page\<T\>, PageRequest.of(page, size, Sort)

-   Sorting: Sort.by(Direction.DESC, \"createdAt\")

+---------------------------------------------------------------------------------+
| Module 15 \| **Spring Boot and REST API Development**                           |
|                                                                                 |
| *Auto-configuration, starters, REST controllers, DTOs, ResponseEntity, Swagger* |
+---------------------------------------------------------------------------------+

**15.1 Spring Boot Fundamentals**

-   Auto-configuration: inspects classpath and configures beans automatically

-   Starters: spring-boot-starter-web, spring-boot-starter-data-jpa, etc.

-   \@SpringBootApplication: \@Configuration + \@EnableAutoConfiguration + \@ComponentScan

-   application.properties: server.port, spring.datasource.\*, spring.jpa.\*

-   Spring Profiles: application-dev.properties, application-prod.properties

-   Activating profiles: spring.profiles.active=dev

**15.2 Building REST APIs**

-   \@RestController: combines \@Controller + \@ResponseBody

-   \@RequestMapping at class level for base path

-   \@GetMapping, \@PostMapping, \@PutMapping, \@PatchMapping, \@DeleteMapping

-   \@PathVariable, \@RequestParam, \@RequestBody, \@RequestHeader

-   ResponseEntity\<T\>: control status code and headers explicitly

**15.3 Data Transfer Objects (DTOs)**

-   Why DTOs: decouple API contract from database entity

-   Request DTO: validation annotations (@NotBlank, \@Email, etc.)

-   Response DTO: expose only necessary fields

-   Manual mapping vs MapStruct: \@Mapper interface with compile-time code generation

-   **★ Never expose entity directly in REST response --- prevents over-posting and data leaks**

**15.4 Working with Data**

-   Service layer: \@Service, \@Transactional, business logic

-   Repository layer: JpaRepository, derived queries, \@Query

-   Entity → DTO → Controller flow

-   Handling Optional in service: orElseThrow() with ResourceNotFoundException

**15.5 Spring Boot Caching**

-   \@EnableCaching in main class

-   \@Cacheable(\"cacheName\"): cache method result

-   \@CacheEvict: evict on update or delete

-   \@CachePut: update cache on write

-   Cache providers: in-memory (default), Redis (production)

-   Redis integration: spring-boot-starter-data-redis

**15.6 Scheduling and Async**

-   \@EnableScheduling + \@Scheduled(cron=\"0 0 \* \* \* \*\"): cron-based scheduling

-   \@Scheduled(fixedRate=5000): fixed-rate execution

-   \@EnableAsync + \@Async: non-blocking method execution

-   **★ \@Async requires separate thread pool configuration via ThreadPoolTaskExecutor**

**15.7 API Documentation**

-   SpringDoc OpenAPI (Swagger 3): springdoc-openapi-starter-webmvc-ui

-   \@Operation, \@ApiResponse, \@Parameter for enhanced documentation

-   Swagger UI: /swagger-ui.html for interactive API testing

-   OpenAPI JSON: /v3/api-docs

**15.8 REST Clients**

-   RestTemplate (legacy): synchronous HTTP client

-   WebClient (Spring WebFlux): reactive, non-blocking HTTP client

-   **★ RestTemplate is in maintenance mode; WebClient or RestClient (Spring Boot 3+) preferred**

+---------------------------------------------------------------------------+
| Module 16 \| **REST API Best Practices**                                  |
|                                                                           |
| *Resource naming, HTTP semantics, versioning, pagination, error handling* |
+---------------------------------------------------------------------------+

**16.1 REST Architectural Constraints**

-   Uniform interface, stateless, client-server, layered system, cacheable

-   Resource-oriented design: think nouns, not verbs

-   HATEOAS: hypermedia as the engine of application state (concept)

**16.2 Resource Naming Conventions**

-   Pluralized nouns: /users, /orders, /products

-   Hierarchical resources: /users/{id}/orders/{orderId}

-   No verbs in URLs: GET /users not GET /getUsers

-   Lowercase, hyphen-separated: /user-profiles not /userProfiles

**16.3 HTTP Methods and Semantics**

-   GET: read, idempotent, no body

-   POST: create, non-idempotent

-   PUT: full replacement, idempotent

-   PATCH: partial update

-   DELETE: delete resource, idempotent

-   Correct status codes: 200 OK, 201 Created, 204 No Content, 400 Bad Request, 401, 403, 404, 409 Conflict, 422 Unprocessable Entity, 500

**16.4 Request and Response Structure**

-   Consistent JSON error format: timestamp, status, error, message, path

-   \@ControllerAdvice + \@ExceptionHandler for global error handling

-   Standard response wrapper (optional): data, message, status

-   Input validation: \@Valid on \@RequestBody; expose validation errors as structured JSON

**16.5 API Versioning**

-   URI versioning: /api/v1/users (most common)

-   Header-based versioning: Accept: application/vnd.api.v1+json

-   When to version: breaking changes in request/response contract

**16.6 Pagination and Filtering**

-   Cursor-based vs offset-based pagination

-   Query parameters: ?page=0&size=20&sort=createdAt,desc

-   Response envelope: content, totalElements, totalPages, number

-   Filter parameters: ?status=ACTIVE&role=ADMIN

**16.7 Security Best Practices**

-   Never expose internal entity models in responses --- use DTOs

-   Prevent mass assignment / over-posting

-   CORS configuration: restrict allowed origins in production

-   Input sanitization; rate limiting to prevent abuse

-   Idempotency of PUT and DELETE

**16.8 Asynchronous and Event-Driven Communication**

-   Synchronous REST vs asynchronous messaging trade-offs

-   Kafka overview: topics, partitions, consumer groups, producers, consumers

-   RabbitMQ overview: exchanges (direct, fanout, topic), queues, bindings

-   When to use REST vs messaging: response needed immediately vs fire-and-forget

-   **★ Webhook pattern: server pushes to client-registered URL on event**

+------------------------------------------------------------------------------+
| Module 17 \| **Spring Security**                                             |
|                                                                              |
| *Authentication, authorization, UserDetailsService, JWT, OAuth2, CORS, CSRF* |
+------------------------------------------------------------------------------+

**17.1 Security Fundamentals**

-   Authentication: who are you? (identity verification)

-   Authorization: what can you do? (access control)

-   Security filter chain: requests pass through ordered filter chain

-   SecurityContext and SecurityContextHolder

**17.2 Configuring Security**

-   SecurityFilterChain bean: replaces deprecated WebSecurityConfigurerAdapter

-   HttpSecurity: permitAll(), authenticated(), hasRole(), hasAuthority()

-   Securing REST endpoints by URL pattern and HTTP method

-   Form login vs HTTP Basic vs custom filter

-   Disabling CSRF for stateless REST APIs

**17.3 UserDetailsService**

-   UserDetails interface: getUsername(), getPassword(), getAuthorities()

-   Custom UserDetailsService: load user from database by username

-   PasswordEncoder: BCryptPasswordEncoder (minimum 10 rounds)

-   AuthenticationProvider: wires UserDetailsService and PasswordEncoder

**17.4 JWT Authentication**

-   JWT structure: header.payload.signature

-   Claims: sub (subject), iat, exp, custom claims (roles)

-   Access token vs Refresh token

-   Custom OncePerRequestFilter: extract and validate JWT from Authorization header

-   Setting SecurityContext after successful validation

-   Dynamic claim extraction --- no hardcoded roles in controllers

-   Token expiry handling: return 401 with clear error message

-   **★ Store JWT secret in environment variable, never in application.properties committed to Git**

**17.5 Method-Level Security**

-   \@EnableMethodSecurity (replaces \@EnableGlobalMethodSecurity)

-   \@PreAuthorize(\"hasRole(\'ADMIN\')\"): evaluated before method

-   \@PostAuthorize: evaluated after method with return value

-   \@Secured: simpler role check without SpEL

**17.6 OAuth2 and OpenID Connect**

-   OAuth2 fundamentals: authorization flows (Authorization Code, Client Credentials)

-   Resource Server vs Authorization Server

-   OpenID Connect (OIDC): identity layer on top of OAuth2

-   Spring Security OAuth2 Resource Server configuration

**17.7 CORS and CSRF**

-   CORS: browser same-origin policy; configure allowed origins, methods, headers

-   CorsConfigurationSource bean vs \@CrossOrigin annotation

-   CSRF: disabled for stateless JWT APIs; enabled for session-based form apps

**17.8 Password and Credential Security**

-   BCrypt: adaptive hashing algorithm with cost factor

-   Argon2: more memory-hard alternative

-   Never store plain-text passwords

-   Password policy enforcement in registration service

**17.9 Web Security --- OWASP Top 10**

-   Injection: SQL injection prevented by PreparedStatement / JPA

-   Broken Authentication: short-lived JWT, secure password storage

-   Broken Access Control: validate ownership, not just role

-   Security Misconfiguration: no default credentials, disable debug endpoints in production

-   Sensitive Data Exposure: HTTPS only, never log passwords or tokens

-   **★ IDOR (Insecure Direct Object Reference): check resource belongs to authenticated user**

-   **★ Rate limiting: Bucket4j or custom filter to throttle requests per IP/user**

+---------------------------------------------------------------------------+
| Module 18 \| **Testing --- JUnit, Mockito, and Spring Boot**              |
|                                                                           |
| *Unit testing, mocking, integration testing, slice tests, best practices* |
+---------------------------------------------------------------------------+

**18.1 JUnit 5 Fundamentals**

-   Test class and method annotations: \@Test, \@BeforeEach, \@AfterEach, \@BeforeAll, \@AfterAll

-   Assertions: assertEquals(), assertNotNull(), assertThrows(), assertAll()

-   Parameterized tests: \@ParameterizedTest with \@ValueSource, \@CsvSource, \@MethodSource

-   Nested tests: \@Nested for grouped related tests

-   Disabling tests: \@Disabled with reason

**18.2 Mockito**

-   \@Mock and \@InjectMocks with \@ExtendWith(MockitoExtension.class)

-   when(\...).thenReturn(\...): stub method calls

-   when(\...).thenThrow(\...): simulate exceptions

-   verify(): confirm interactions happened

-   ArgumentMatchers: any(), anyString(), eq()

-   Capturing arguments: ArgumentCaptor

**18.3 Spring Boot Test Framework**

-   \@SpringBootTest: loads full application context

-   \@WebMvcTest: slice test for controllers only

-   \@DataJpaTest: slice test for repository layer with in-memory H2

-   MockMvc: test controller endpoints without running a server

-   \@MockBean: replace a Spring bean with a Mockito mock in context

**18.4 Integration Testing**

-   Real database tests with H2 in-memory database

-   SQL scripts: \@Sql to set up and tear down test data

-   Testcontainers: spin up real MySQL container for tests

-   TestRestTemplate: test REST endpoints with real HTTP

**18.5 Best Practices**

-   Unit tests: test one unit in isolation, mock dependencies

-   Test naming: should_ReturnUser_WhenValidId_Given()

-   Arrange-Act-Assert (AAA) pattern

-   Test pyramid: many unit, some integration, few end-to-end

-   Avoid testing framework internals; test behavior not implementation

-   **★ Test coverage is a guide, not a target --- 100% coverage does not mean no bugs**

+-----------------------------------------------------------------------+
| Module 19 \| **Logging and Monitoring**                               |
|                                                                       |
| *SLF4J, Logback, structured logging, Actuator, ELK, Prometheus*       |
+-----------------------------------------------------------------------+

**19.1 Logging Fundamentals**

-   Log levels: TRACE, DEBUG, INFO, WARN, ERROR

-   SLF4J: logging facade; Logback as default implementation in Spring Boot

-   Logger declaration: private static final Logger log = LoggerFactory.getLogger(X.class)

-   \@Slf4j Lombok annotation: generates log field automatically

-   Parameterized logging: log.info(\"User {} logged in\", userId) --- avoids string concatenation

**19.2 Logback Configuration**

-   logback-spring.xml: define appenders, patterns, log levels per package

-   Console appender: human-readable output in development

-   File appender: rolling file strategy for production

-   Log pattern: timestamp, level, thread, logger, message

-   Environment-specific log levels: DEBUG in dev, INFO/WARN in prod

**19.3 Structured Logging**

-   JSON log format for machine-parseable logs

-   MDC (Mapped Diagnostic Context): per-request correlation ID

-   Adding request ID to every log line in a filter

-   Thread context propagation in async methods

**19.4 Error Logging Best Practices**

-   Always log exception with stack trace: log.error(\"msg\", e) not log.error(e.getMessage())

-   Never log passwords, tokens, or card numbers

-   Log at appropriate level: ERROR for unrecoverable, WARN for recoverable, INFO for business events

**19.5 Spring Boot Actuator**

-   spring-boot-starter-actuator dependency

-   /actuator/health: health indicators for load balancer probes

-   /actuator/info: application version and metadata

-   /actuator/metrics: Micrometer metrics

-   /actuator/loggers: change log level at runtime without restart

-   Securing actuator endpoints: restrict to admin role or internal network

**19.6 Observability in Production**

-   Metrics vs Logs vs Traces: three pillars of observability

-   Micrometer + Prometheus: expose metrics for scraping

-   Grafana: visualize Prometheus metrics with dashboards

-   ELK Stack (concept): Elasticsearch, Logstash, Kibana for centralized log analysis

-   Distributed tracing: trace ID + span ID across service calls

-   **★ Spring Boot 3 Observability: built-in Micrometer Tracing with OpenTelemetry**

+-----------------------------------------------------------------------+
| Module 20 \| **Design Patterns**                                      |
|                                                                       |
| *Creational, structural, behavioral patterns and their use in Spring* |
+-----------------------------------------------------------------------+

**20.1 Introduction**

-   What are design patterns? Reusable solutions to recurring problems

-   Categories: Creational, Structural, Behavioral

-   Patterns in context of Java and Spring framework

**20.2 Creational Patterns**

-   Singleton: static instance, enum-based (thread-safe), double-checked locking

-   Factory Method: defer object creation to subclasses

-   Abstract Factory: create families of related objects

-   Builder: construct complex objects step by step (@Builder in Lombok)

-   Prototype: clone existing objects (shallow vs deep copy)

**20.3 Structural Patterns**

-   Adapter: convert incompatible interface to expected interface

-   Facade: simplify complex subsystem with unified interface

-   Proxy: control access to object (JDK dynamic proxy, CGLIB in Spring AOP)

-   Decorator: add behavior without modifying original class

-   Composite: treat individual objects and composites uniformly

**20.4 Behavioral Patterns**

-   Strategy: define family of algorithms; swap at runtime

-   Template Method: define skeleton, defer steps to subclasses (JdbcTemplate)

-   Observer: subscribe to events; used in Spring Application Events

-   Command: encapsulate request as object

-   Chain of Responsibility: pass request along handler chain (Servlet Filters, Security Filter Chain)

**20.5 Patterns Used in Spring**

-   Dependency Injection Pattern: IoC container wires dependencies

-   MVC Pattern: DispatcherServlet, Controller, View separation

-   Template Pattern: JdbcTemplate, RestTemplate

-   Proxy Pattern: \@Transactional, \@Cacheable, Spring AOP

-   **★ Repository Pattern: Spring Data JPA repositories abstract data access layer**

-   **★ Decorator Pattern: spring-security filter chain wraps each request**

+-----------------------------------------------------------------------+
| Module 21 \| **Clean Code and Project Architecture**                  |
|                                                                       |
| *Naming, layering, DTOs, global exception handling, refactoring*      |
+-----------------------------------------------------------------------+

**21.1 Clean Code Principles**

-   Meaningful names: classes as nouns, methods as verbs

-   Small methods and classes: single responsibility

-   Avoid God classes: distribute responsibility

-   Avoid deep nesting: use early returns and guard clauses

-   No magic numbers: use named constants

-   DRY: Don\'t Repeat Yourself

**21.2 Layered Package Structure**

-   entity: JPA entities --- database representation

-   dto: request/response data objects

-   dao / repository: data access layer

-   service: business logic layer

-   controller: REST endpoint layer

-   config: Spring configuration classes

-   exception: custom exception classes and global handler

-   util: stateless utility methods

-   Package convention: com.org.{project}.{layer}

**21.3 DTO and Entity Mapping**

-   Why DTOs: decouple persistence model from API model

-   Manual mapping: toDto() / toEntity() static methods or mapper class

-   MapStruct: annotation-based compile-time mapper generation

-   \@Mapper(componentModel = \"spring\"): inject as Spring bean

**21.4 Global Exception Handling**

-   \@ControllerAdvice: apply \@ExceptionHandler globally

-   Custom exception classes: ResourceNotFoundException, ConflictException

-   Standard error response DTO: timestamp, status, error, message, path

-   Handling MethodArgumentNotValidException: extract field-level validation errors

-   **★ Always return proper HTTP status codes from exception handlers**

**21.5 Refactoring Techniques**

-   Extract method: replace repeated code with named method

-   Extract class: move related fields/methods to new class

-   Replace magic number with named constant

-   Replace conditional with polymorphism

-   Introduce parameter object: group related parameters into one DTO

+-----------------------------------------------------------------------+
| Module 22 \| **Build, Deployment, and CI/CD**                         |
|                                                                       |
| *Maven build, JAR/WAR, profiles, GitHub Actions, cloud readiness*     |
+-----------------------------------------------------------------------+

**22.1 Maven Build**

-   POM structure: parent, properties, dependencies, build plugins

-   mvn clean package: build deployable artifact

-   Maven profiles: \<profiles\> for environment-specific builds

-   Fat JAR: spring-boot-maven-plugin repackages with embedded Tomcat

-   WAR packaging for external servlet container deployment

**22.2 Environment Configuration**

-   application.properties vs application-{profile}.properties

-   Environment variable overrides: SPRING_DATASOURCE_URL=\...

-   Externalized configuration priority order in Spring Boot

-   Never commit credentials --- use environment variables or secrets manager

-   **★ \@ConfigurationProperties: bind group of related properties to typed bean**

**22.3 CI/CD Fundamentals**

-   Continuous Integration: automatically build and test on every push

-   Continuous Delivery: automatically produce deployable artifact

-   Continuous Deployment: automatically deploy to target environment

-   Typical pipeline: Build → Unit Test → Integration Test → Package → Deploy

**22.4 GitHub Actions**

-   .github/workflows/build.yml: workflow definition

-   Triggers: on: push, on: pull_request

-   Jobs and steps: actions/checkout, actions/setup-java, maven commands

-   Secrets: store DB password, JWT secret in GitHub Secrets

-   **★ Cache Maven dependencies with actions/cache to speed up builds**

**22.5 Cloud-Native Readiness**

-   12-factor app principles: codebase, config, backing services, etc.

-   Externalized configuration: no hardcoded environment-specific values in code

-   Stateless application: no local session state (use Redis or JWT)

-   Health and readiness endpoints for orchestrators

-   Secrets management: AWS Secrets Manager, HashiCorp Vault (concept)

+---------------------------------------------------------------------------+
| Module 23 \| **Docker and Containerisation**                              |
|                                                                           |
| *Images, containers, Dockerfile, Docker Compose, Spring Boot with Docker* |
+---------------------------------------------------------------------------+

**23.1 Docker Fundamentals**

-   What is a container? Isolated process with own filesystem

-   Image vs Container: image is blueprint, container is running instance

-   Docker architecture: daemon, client, registry

-   Docker installation and docker version verify

**23.2 Writing a Dockerfile for Spring Boot**

-   Base image: eclipse-temurin:21-jre or amazoncorretto:21

-   WORKDIR, COPY target/\*.jar app.jar

-   EXPOSE 8080

-   ENTRYPOINT \[\"java\", \"-jar\", \"/app.jar\"\]

-   Layer caching: COPY pom.xml + RUN mvn dependency:resolve before COPY src

-   Non-root user: RUN adduser appuser && USER appuser

-   .dockerignore: exclude target/, .git/, \*.log

**23.3 Docker Commands**

-   docker build -t myapp:1.0 . --- build from Dockerfile

-   docker run -p 8080:8080 \--name myapp myapp:1.0

-   docker run -d --- detached mode

-   docker run -e SPRING_PROFILES_ACTIVE=prod

-   docker ps, docker ps -a --- list containers

-   docker logs myapp, docker logs -f myapp --- follow logs

-   docker exec -it myapp /bin/sh --- shell inside container

-   docker stop, docker rm, docker rmi

-   docker push --- push to registry after docker login

**23.4 Docker Compose**

-   docker-compose.yml: define multi-container applications

-   Services: app (Spring Boot), db (MySQL), redis (cache)

-   Networks: containers on same network communicate by service name

-   Volumes: persist database data outside container lifecycle

-   depends_on: ensure DB starts before app

-   docker compose up -d, docker compose down, docker compose logs -f

-   healthcheck: wait for DB readiness before starting app

**23.5 Spring Profiles with Docker**

-   Pass active profile via environment variable: -e SPRING_PROFILES_ACTIVE=prod

-   application-prod.properties: reads from env vars for credentials

-   spring.datasource.password=\${DB_PASSWORD}

-   Never bake credentials into Docker image

-   **★ Docker multi-stage build: build stage (Maven) + runtime stage (JRE only) = smaller image**

+------------------------------------------------------------------------------------------+
| Module 24 \| **Microservices Fundamentals**                                              |
|                                                                                          |
| *Decomposition, service discovery, API gateway, inter-service communication, resilience* |
+------------------------------------------------------------------------------------------+

**24.1 Monolith vs Microservices**

-   Monolith: single deployable unit; simple to start, hard to scale specific parts

-   Microservices: independently deployable services around business capabilities

-   When to split: clear domain boundary, independent scaling needs, team autonomy

-   Monolith first: don\'t prematurely decompose

**24.2 Service Discovery**

-   Problem: services are dynamic --- IPs change on restart/scale

-   Eureka: Netflix service registry; services register on startup

-   Consul: alternative registry with health checking

-   Client-side vs server-side discovery

**24.3 API Gateway**

-   Spring Cloud Gateway: single entry point for all clients

-   Responsibilities: routing, authentication, rate limiting, SSL termination

-   Route configuration: predicates (path, header) and filters

**24.4 Inter-Service Communication**

-   Synchronous: REST with OpenFeign declarative client

-   Asynchronous: Kafka or RabbitMQ for decoupled event-driven communication

-   OpenFeign: \@FeignClient(name=\"user-service\") with method declarations

**24.5 Resilience Patterns**

-   Circuit Breaker (Resilience4j): stop calling failing service, return fallback

-   Retry with exponential backoff

-   Timeout: never wait indefinitely for a downstream service

-   Bulkhead: limit concurrent calls to a service

**24.6 Distributed Concepts**

-   CAP theorem: Consistency, Availability, Partition Tolerance --- pick two

-   Eventual consistency: distributed data may be temporarily inconsistent

-   Saga pattern: distributed transactions via compensating transactions

-   Distributed tracing: trace ID + span ID correlate logs across services

-   **★ Spring Cloud Sleuth / Micrometer Tracing: auto-propagate trace context**

+----------------------------------------------------------------------------------------+
| Module 25 \| **Real-World Project Practices**                                          |
|                                                                                        |
| *Production checklist, performance, security hardening, team workflow, Kafka/RabbitMQ* |
+----------------------------------------------------------------------------------------+

**25.1 Full-Stack Backend Project Structure**

-   Apply all modules: Spring Boot REST + JPA + Security + Lombok + MapStruct + Validation

-   Feature-based modularisation at scale: com.org.project.user.\*, com.org.project.order.\*

-   Common shared packages: common.exception, common.dto, common.util

-   API versioning from day one: /api/v1/\*\*

-   Database migration: Flyway for versioned schema changes

**25.2 Production-Ready REST API Checklist**

-   Authentication: JWT with short-lived access token + refresh token

-   Authorization: role-based and resource-based (ownership check)

-   Input validation: \@Valid on all request bodies

-   Error handling: \@ControllerAdvice with consistent JSON error format

-   Logging: structured logging with request ID in every log line via MDC

-   API documentation: Swagger/OpenAPI auto-generated

-   Health endpoint: /actuator/health for load balancer probes

-   Database connection pool: HikariCP with proper pool sizing

-   No credentials in code: all secrets via environment variables

-   HTTPS only: SSL certificate or TLS termination at load balancer

**25.3 Performance and Scalability**

-   Database: use EXPLAIN, verify index usage, avoid SELECT \*, paginate all list endpoints

-   Connection pooling: right-size HikariCP pool

-   Caching strategies: cache-aside, write-through, read-through

-   \@Cacheable for read-heavy endpoints; \@CacheEvict on write

-   N+1 prevention: JOIN FETCH or \@EntityGraph for all collection relationships

-   Async processing: \@Async for background tasks that don\'t need immediate response

-   **★ HTTP caching: ETag and Cache-Control headers for read-heavy public endpoints**

**25.4 Security Hardening**

-   SQL injection: PreparedStatement or JPA --- never string-concatenate SQL

-   XSS: encode output in HTML contexts; Content-Security-Policy header

-   CSRF: disabled for stateless JWT; enabled for session-based form apps

-   IDOR: validate resource ownership before returning

-   Rate limiting: Bucket4j or custom filter per IP/user

-   Dependency scanning: OWASP Dependency Check in CI pipeline

-   HTTPS + HSTS: Strict-Transport-Security header

-   Never log sensitive data: passwords, tokens, card numbers

**25.5 Team Codebase Workflow**

-   Always pull before creating branch: git pull origin main

-   One feature per branch; name matches ticket: feature/PROJ-123-add-search

-   Descriptive commit messages: feat(user): add email uniqueness validation

-   Resolve merge conflicts locally before pushing

-   Never push directly to main or develop --- use pull requests

-   Run tests before pushing: mvn clean verify

**25.6 Messaging with Kafka and RabbitMQ**

-   Kafka: distributed log --- messages persisted, replayable, ordered within partition

-   spring-kafka: \@KafkaListener for consuming, KafkaTemplate for producing

-   RabbitMQ: exchange → queue routing --- direct, fanout, topic exchange types

-   spring-rabbit: \@RabbitListener for consuming, RabbitTemplate for producing

-   Kafka: use for event streaming, audit log, real-time analytics

-   RabbitMQ: use for task queues, work distribution, notifications

**25.7 Development Workflow**

-   Build APIs in this order: Entity → Repository → Service → Controller → DTO + Validation → Exception layer

-   Use Swagger UI for manual testing during development

-   Use Boot Dashboard in STS for quick restarts

-   Write unit tests for service layer first; integration tests for repository layer

-   **★ Code review checklist: correctness, performance, security, readability, test coverage**
