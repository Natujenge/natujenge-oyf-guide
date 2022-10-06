# Database (DB) Overview 

+ **Data** - can be facts related to any object in consideration e.g. your name, height, age are some data related to you. 

+ **Database** - a systematic collection of data to help in storage and manipulation of data. 
    + You can adopt the following folder structure for system organization of data:
        + **Option 1: Tables** 
            + **students.txt** - file containing students data
                + **Column Headers:**
                    + admin_no|student_name|dob|home_county|admin_date|admin_class|class
                + **Sample records:**
                    + 1001|Rexvin Mwangi|2008-09-22|Kiambu|2020-02-05|8S
                    + 1002|Joy Kendi|2008-11-26|Tharaka|2019-03-07|8W
            + **teachers.txt** - file containing teachers data
                + **Column Headers:**
                    + staff_no|teacher_name|id_no|dob|tsc_no|home_county|join_date
                + **Sample records:**
                    + 101|John Mugendi|10010010|1975-02-05|622828|Tharaka|2016-02-05
                    + 102|Johannes Opiyo|24310010|1983-08-22|34535345|Homa Bay|2019-05-01
            + **classes.txt:** - file containing classes data
                + **Column Headers:**
                    + class|class_teacher
                + **Sample records:**
                    + 8W|102
                    + 8S|101
            
    + **Option 2: Collections**
        + **students.json** - file containing students data 

            ```yaml
            [
                {
                    "id":"1001",
                    "name": "Rexvin Mwangi",
                    "dob": "2008-09-22",
                    "county":"Kiambu",
                    "admin_date": "2020-02-05",
                    "class": "8S"
                },
                {
                    "id":"1002",
                    "name": "Joy Kendi",
                    "dob": "2008-11-26",
                    "county":"Tharaka",
                    "admin_date": "2019-03-07",
                    "class": "8W"
                }
            ]

    + **Data storage**:
        + In my experience as an engineer, all database management systems that I have come across **store data on a physical storage** -disk on a computer (HDD or SSD). 
        + **Tables** or **Collections** are represented as **files on disk**. This means that for every collection or table, you will find a corresponding file or files on disk. 
    
    
## Database Management System (DBMS)


