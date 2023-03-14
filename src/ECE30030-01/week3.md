# Week 3

## MySQL
 - An SQL-based R-DBMS (relational database management system)
 - Free and open-source R-DBMS (under GPL)
    - Owned by Oracle
    - Commercial version of MySQL is also provided (including technical support)
    - "My" came from the name of co-founder Michael Widenius' daughter
        - C.f, MariaDB
 - Compatible with standard SQL (almost)
 - Frequently used for commercial web services
    - Enlyft라는 회사가 주기적으로 MySQL 사용량 데이터를 분석한다


 - MySQL은 시작할 때 돈은 안들지만 유지보수나 문제가 생겼을 때 많이 손해/비용이 발생한다

 - Why MySQL?
    - Popular
        - Active discussions all over the Internet
    - Versatile: runs on Linux, Windows, Mac OS X, Solaris, FreeBSD, ...
        - FreeBSD -> -> MacOS
        - Supports wide range of programming languages (C/C++, Java, Python, .Net, ...)
            - Connector가 존재한다
    - Cost starts from 0
        - 하지만 이후 유지보수 비용, 시작 비용, 관리 비용도 생각해야 한다
    - High performance (fast and reliable)

 - 다양한 DBMS
    - Disk | File System | Database System
        - Disk는 느리다..
        - DB 전체를 Memory에 올리면 안되나?
            - -> In-memory DB
            - access가 많고 적은 양의 데이타
            - **Redis**
    - **Elasticsearch**
        - Reverse Index를 만들어 준다
        - Google과 같은 검색엔진을 만들기 쉽다
        - 조직 내에서 검색엔진을 만들어야 할 때
    - **SQLite**
        - DB끼리 데이터를 옮기려면 DBMS에서 제공하는 interface를 사용해야만 한다
        - 그냥 복사->붙여넣기 한다고 해서 DBMS가 인식하지 않는다
        - 하지만 SQLite는 복사 붙여넣기 해도 된다
        - File-based
    - **Microsoft Azure SQL Database**
        - MSSQL on **Cloud**
    - **Snowflake**
        - Data warehouse를 구축할 수 있게 도와줌
        - 분석을 목적으로 한다 (Analysis)
            - Analytic <-> Transactional


 - MySQL
    - Massive: Can handle TB of data
    - Convenient: Supports high-level query language
    - Multi-user: Supports concurrent data access
    - Safe: Supports *transaction*
        - In R-DB, transaction is the *unit* of operation/task
            - *atomicity*
            - eg. (1)돈을 빼고 (2)이동하고 (3)돈을 더하고
                - 1,2,3 전부 다 실행이 되거나
                - 전부 실행이 안되거나 해야한다
    - Efficient: Can handle thousands of queries/second
        - TPS -> transactions per second
        - R-DBMS에서는 성능이 상당히 중요하다
    - Reliable: 99.99% up-time in many real-world products
        - Question: Up-time을 유지하기 위해서는 어떤 문제들이 존재하고 이를 해결하기 위해서는 어떤 기술들이 필요한가?
            - 문제: 버그 생겨서 crash


 - MySQL Versions
    - **Version 5.x** vs **Version 8.0**
    1. 5.x
        - Most popular version of MySQL
        - More stable and conventional
        - 5.x 버전일 때 Oracle이 인수했다
    2. 8.0
        - Current version 
        - Provides up-to-date DB functionalities
            - better storage engine, faster, more secure
        - 아직까지는 5.x 버전을 사용하고 있다
    - **Upgrading a DBMS is NOT easy**
        - 업그레이드 과정에서 데이터 손실은 매우 흔한 문제이다
            - why???

 - Where to get MySQL?
    - [Community Version](https://dev.mysql.com/downloads/)
    - DBMS는 기본적으로 상시 작동한다
    
    - 우리 수업에서는 Docker를 사용해서 DBMS를 실행 할 것이다
    - We have prepared a Docker image for the course
        - Consists of ubuntu Server, MySQL, example databases for course activities
    
    - DB Client Software

