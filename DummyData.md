# Dummy data creation notes

Superset visualizes the data available in django demo app.
To simulate the flow, let's create some dummy data.

Connect to postgres from host system 
`psql -h localhost -U debug -d demoapp`

##### Create table
````
CREATE TABLE student_enrollment_growth (
    id SERIAL PRIMARY KEY,
    audited_on date,
    no_of_students integer
)
````

````
INSERT INTO student_enrollment_growth (audited_on, no_of_students)
values 
('2014-01-01', 35),
('2014-06-01', 85),
('2015-01-01', 135),
('2015-06-01', 175),
('2016-01-01', 205),
('2016-06-01', 285),
('2017-01-01', 335),
('2017-06-01', 455),

````