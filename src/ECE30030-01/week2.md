# Week 2


## Relation Algebra
 - Select σ
 - Project Π
 - Cartesian product ⨉
 - Join ⋈
 - Rename ρ
 - Union ⋃
 - Set-intersection ⋂
 - Set-difference −

 - Operands: variables or values from which new values can be constructed
 - Operators: symbols denoting procedures that construct new values from given operands


 - What is relation algebra?
    - A procedural language consisting of a set of operations that take 1 or 2 relations as input and produce a new relation as their output

### Select Operation
 - The select operation selects tuples that satisfy a given predicate
 - Notation: $\sigma_{\rho}(r)$
    -    is called the selection predicate
 - Example:
    - "select those tuples of the instructor relation where the instructor is in the *Comp. Sci* department"
        - Query: $\sigma_{dept\_name="Comp. Sci."}(instructor)$
    - Comparison using $=, \ne, >, \ge, <, \le $ are allowed in the selection predicates
    - Combine several predicates into a larger predicate by using the connectives: $\land$(and), $\lor$(or), $\lnot$(not)

## Project Operation
 - A *unary* operation that returns its argument relation, with certain attributes left out
 - Notation $\Pi_{A_1,A_2,A_3,...,A_k}(r)$
    - $A_1,A_2,A_3,...,A_k$ are attribute names and $r$ is a relation name
 - The result is defined as a relation with k columns
    - Columns that are not listed among $A_1,A_2,A_3,...,A_k$ are also removed in the result
    - **Duplicate rows are removed** from the result (because the resulting relations are sets)
 - Example
    - "Show only the *name* and *salary* of instructor"
    - Query
        - $\Pi_{name, salary}(instructor)$

## Compositoin of relational operations
 - relational-algebra operations can be composed together into relational-algebra expression
    - recall that the result of a relational-algebra is a relation
    - Instead of giving the name of a relation as the argument of the projection operation, one can give an expression that evaluates to a relation
 - Consider the query
    - "Find the names of all instructors in the Comp. Sci. deparment"
    - Query
        - $\Pi_{name}\Bigl( \sigma_{dept\_name="Comp. Sci."}(instructor)\Bigr)$

## Cartesian-Product Operation
 - The Cartesian-product operation (denoted by $\times$) combines information from any 2 relations
    - Construct a relation of the result out of each possible pair of tuples
    - Binary operator
 - Example
    - "The Cartesian product of the relations *instructor* and *teaches*"
    - Query
        - $instructor \times teaches$
 - The Cartesian-Product associates every tuple of *instructor* with every tuple of *teaches*
    - most of the resulting rows have information not very meaningful
    - Example
        - "Get only those tuples of *instructor $\times$ teaches* that pertain to the courses that the instructor taught"
        - Query
            - $\sigma_{instructor.id=teaches.id}(instructor \times teaches)$

## Join Operation
 - The join operation combines a **select** operaiton and a **Cartesian-Product** operation into a single operation
    - Consider relations $r(R)$ and $s(S)$
        - Let $\theta$ be a predicate on attributes in the schema $R \cup S$
        - The join operation $r \bowtie_{\theta}s$ is defined as follows:
            - $r\bowtie_{\theta}s = \sigma_{\theta}(r\times s)$
    - Example
        - $\sigma_{instructor.id=teaches.id}(instructor\times teaches)$ is equivalent to $instructor\bowtie_{instructor.id=teaches.id}teaches$

- 나중에 SQL을 사용하면 아래와 같이 다양한 JOIN operation을 배우게 될 것이다
    - INNER JOIN
    - LEFT JOIN
    - RIGHT JOIN
    - OUTER JOIN

## Union Operation
 - The union operation combines 2 relations as a superset of both
    - Notation: $r\cup s$
 - For $r\cup s$ to be valid,
    1. $r, s$ must have the same number of attributes (same **arity**)
    2. The attribute domains must be compatible
 - Example
    - "Find all coursese taught in the Fall 2017 semester, or in the Spring 2018 semester, or both"
    - Query
        - $\Pi_{corse\_id}\Bigl(\sigma_{semester="Fall"\land year=2017}(teaches)\Bigr) \cup \\\Pi_{corse\_id}\Bigl(\sigma_{semester="Spring"\land year=2018}(teaches)\Bigr)
    $
 - **Duplicates are removed!**

## Set-Intersection Operation
 - The set-intersection operation finds tupes that are in both the input relations
    - Notation: $r\cap s$
    - Assumptions:
        - $r, s$ have the same **arity**
        - Attributes of $r$ and $s$ are **compatible**
 - Example
    - "Find the set of all courses taught in both the 2017-Fall and 2018-Spring semesters"
    - Query
        - $\Pi_{course\_id}\Bigl(\sigma_{semester="Fall"\, \land \, year=2017}(section)\Bigr)\cap \\ \Pi_{course\_id}\Bigl(\sigma_{semester="Spring"\, \land \, year=2017}(section)\Bigr)$

## Set-Difference Operation
 - The set-difference operation finds tuples that are in one relation but are not in another
    - Notation: $r-s$
    - Assumptions
        - same arity
        - compatibility

## The Assignment Operation 
 - It is convenient at times to write a relational-algebra expression by assigning parts of it to temporary relation variables
    - Notation: $\leftarrow$
    - An assignment works like the assignments in a programming language
 - Example
    - Find all instructor in the Physics and Music departments
    - Query
        - $Physics \leftarrow \sigma_{dept\_name="Physics"(instructor)}$
        $Music \leftarrow \sigma_{dept\_name="Music"(instructor)}$
        $Physics \cup Music$
 - 프로그램 코드와 같이 위에서 아래로 읽는다 -> sequential code를 짤 수 있다
 - With the assignment operation, a query can be written as a sequential program
    - A sequential program consists of a series of assignments followed by an expression whose value is displayed as the result of the query

## Rename Operation
 - The results of relational-algebra expressions do not have a name that one can use to refer to them
 - The rename operator, $\rho$, sets names to relational-algebra expressions
    - Notation: $\rho_x(E)$
    - Returns the result of expression $E$ under the name $x$
 - $E$ can be specific attribute of a relation

## Equivalent Queries
 - There is more than one way to write a query in relational algebra
 - Example
    - "Find information about courses taught by instructors in the Comp. Sci. department with salary greater than 50,000"
    - Query 1
        - $\sigma_{dept\_name="Comp.Sci"\, \land \, salary>50,000}(instructor)$
        - $\sigma_{dept\_name="Comp.Sci"}\Bigl( \sigma_{salary>50,000}(instructor)\Bigr)$
        - \\( \sigma_{salary>50,000}\Bigl( \sigma_{dept\_name="Comp.Sci"}(instructor)\Bigr) \\)
    - The 3 queries are **not identical**; they are, however, **equivalent** -- they give the same result on **any** database

 - 쿼리를 어떻게 짜느냐에 따라서 실행 속도가 달라진다
    - 예를들어 위에 예시에서 1번보다 2번이 더 빠를 것을 예상할 수 있다. 더 적은 comparison을 사용하기 때문에
    - 요즘 DBMS는 SQL 쿼리를 받은 그대로 실행하지 않고 **Query Optimization**을 한다


 --- 

 - 프로젝트 할 때 Query Optimization이 필요할 수 있다