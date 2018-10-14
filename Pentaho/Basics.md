# Pentaho Basics
## [Udemy](https://www.udemy.com/learning-pentaho/learn/v4/overview) - Learning Pentaho - From PDI to Full 
- [**Download Pentaho**](https://sourceforge.net/projects/pentaho/)
- [**Download Mondrian**](https://sourceforge.net/projects/mondrian/)

## Setup
- **Install** a database like [PostgreSQL](https://www.postgresql.org/)
### Transformation
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