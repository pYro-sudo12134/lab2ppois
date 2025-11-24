# Variant 10, Laboratory task 2, Losik Yaroslav

# Problem

Create an application based on the MVC pattern and consider all the forms that can be used to create records for all students.

# Tables (just in case)

## Form (DDL)

```
create table father_info
(
    id                 serial
        primary key,
    father_name        varchar(20) not null,
    father_surname     varchar(20) not null,
    father_father_name varchar(20) not null,
    salary             double precision
        constraint father_info_salary_check
            check (salary >= (0)::double precision)
);
```

## Father (DDL)

```
create table form
(
    id         serial
        primary key,
    student_id integer not null
        references student_info,
    father_id  integer not null
        references father_info,
    mother_id  integer not null
        references mother_info
);
```

## Mother (DDL)

```
create table mother_info
(
    id                 serial
        primary key,
    mother_name        varchar(20) not null,
    mother_surname     varchar(20) not null,
    mother_father_name varchar(20) not null,
    salary             double precision
        constraint mother_info_salary_check
            check (salary >= (0)::double precision)
);
```

## Student (DDL)

```
create table student_info
(
    id                  serial
        primary key,
    student_name        varchar(20),
    student_surname     varchar(20),
    student_father_name varchar(20),
    num_of_sisters      integer
        constraint student_info_num_of_sisters_check
            check (num_of_sisters >= 0),
    num_of_brothers     integer
        constraint student_info_num_of_brothers_check
            check (num_of_brothers >= 0)
);
```

# Classes

- ```WindowApplication``` is the main class for launching.
- ```Action``` is used to define the action in controller.
- ```MainController``` is the main controller.
- ```DatabaseController``` is the controller for database persistence operations.
- ```DisplayController``` is the controller for the display.
- ```OptionsController``` is the controller for delegation of CRUD operations.
- ```XMLController``` is the controller for the use of XML parsers.
- ```Form``` is the entity for forms.
- ```Student``` is the entity for students.
- ```Mother``` is the entity for mothers.
- ```Father``` is the entity for fathers.
- ```FormService``` is the service for executing persistent operations.
- ```XMLParserService``` is the service for executing I/O operations with XML file.
