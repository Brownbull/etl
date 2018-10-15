# Pentaho Basics
## [Udemy](https://www.udemy.com/learning-pentaho/learn/v4/overview) - Learning Pentaho - From PDI to Full 
- [**Download Pentaho**](https://sourceforge.net/projects/pentaho/)
- [**Download Mondrian**](https://sourceforge.net/projects/mondrian/)

## Setup
- **Install** a database like [PostgreSQL](https://www.postgresql.org/)
### Load
- **Connect** Pentaho to the database:
  - Open Spoon.bat
  - Create new transformation
  - Go to View and create a new database connection
  ![1](../images/p1.png)
- **Create Input**: 
  - Go to Design Tab
  - Go to input
  - Click and drag you format to the canvas
  - Double click on it and configure it.
    - Load File
    - Put delimiter
    - Get columns
    - Check columns format
    - Check everything ok with **Preview**
- **Connect**: Shift+Click then go click output
- **Create Output**: 
  - Go to Design Tab
  - Go to Output
  - Click and drag you format to the canvas
  - Double click on it and configure it.
    - select table on database
    - go to Database fields and press Get fields then SQL
  ![2](../images/p2.png)
    - You can Execute that code  
  ![3](../images/p3.png)
- **Run**: click play button, then click run
- **Check Reults**
  - On Spoon Log
![4](../images/p4.png)
  - On DB
  ![5](../images/p5.png)

## ETL with STAGES
(all uppercase values can be found in search bar on Spoon)
- add a START
- add a **Stage** TRANSFORMATION
  - add INPUT
  - add SELECT VALUES
    - setup values to remain or delete
  - add SORT ROWS to have unique order id
  - add TABLE OUTPUT
    - setup this with the table to write
- select the TRANSFORMATION
- add a **Dimension** TRANSFORMATION
  - add TABLE INPUT
    - click on Get SQL select statement
    - modify SQL to format or apply rules
  - add DIMENSION LOOKUP/UPDATE
    - change table name
    - on Keys tab put primary key of row
    - on Fields the rest
    - put a name to Technical Key like *PK_ORDER*
    - click on SQL and Execute
  - then run
  **FACT TABLE**
  - **First**: add a *VALUES* TRANSFORMATION like an **Stage** one
    - add INPUT
    - add SELECT VALUES
      - remain al quantitatve values
    - add TABLE OUTPUT
  - **Second**: create a TRANSFORMATION for *PRE_FACT*
    - add TABLE INPUT
      - select TABLE created on previous step
    - add DATABASE LOOKUP
      - give it a name like DIM_ORDERS
      - setup compare fields
![6](../images/p6.png)
    - add SELECT VALUES
      - just select the foreign codes and values. from this
![7](../images/p7.png)
      - to this:
  ![8](../images/p8.png)
    - add OUTPUT TABLE
      - name it PRE_FACT
      - click on specify fields and create table
    - RUN
  - **Third**: add to ETL
    - add *VALUES* TRANSFORMATION from 1st step, after last STG
    - add *PRE_FACT* TRANSFORMATIONfrom 2st step, after last DIM
  - **Forth**: create the FACT TABLE on new TRANSFORMATION
    - add TABLE INPUT
      - select PRE_FACT table
    - add TABLE OUTPUT
      - put FACT_TABLE name
    - RUN
  - **Fifth**: create the CLEAR CACHE on new TRANSFORMATION
    - add GENERATE ROWS
      - add a rstring with name filename and valueas 
      http://localhost:8080/pentaho/api/system/refresh/mondrianSchemaCache
      http://localhost:8080/pentaho/plugin/cda/api/clearCache
    - add HTTP CLIENT
      - check acept url from field
      - put filename as field name
    - RUN
  - **Six**: add clears on ETL
    - After PRE FACT add FACT TABLE
    - then CLEARs
- add connect SUCCESS

## Schedule
https://www.udemy.com/learning-pentaho/learn/v4/t/lecture/7275356?start=0

