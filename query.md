TODO:

1. Selezionare tutti gli studenti nati nel 1990 (160)
2. Selezionare tutti i corsi che valgono più di 10 crediti (479)
3. Selezionare tutti gli studenti che hanno più di 30 anni
4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)
5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)
6. Selezionare tutti i corsi di laurea magistrale (38)
7. Da quanti dipartimenti è composta l'università? (12)
8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
9. Inserire nella tabella degli studenti un nuovo record con i propri dati (per il campo degree_id, inserire un valore casuale)
10. Cambiare il numero dell’ufficio del professor Pietro Rizzo in 126
11. Eliminare dalla tabella studenti il record creato precedentemente al punto 9

table name:

- departments
- degrees
- courses
- teachers
- students
- exams
- course_teacher
- exams_student

1.  
    SELECT *
    FROM students
    WHERE YEAR(date_of_birth) = 1990;

2.  
    SELECT *
    FROM courses
    WHERE cfu > 10;

3.  
    SELECT *
    FROM students
    WHERE YEAR(NOW()) - YEAR(date_of_birth) > 30;

4.  
    SELECT *
    FROM courses
    WHERE period = 'I semestre' 
    AND year = 1;

5.  
    SELECT *
    FROM exams
    WHERE date = "2020-06-20" 
    AND hour > "14:00:00";

6.  
    SELECT *
    FROM degrees
    WHERE level = "magistrale";

7.  
    SELECT COUNT(id) AS departments_count
    FROM departments;

8.  
    SELECT COUNT(id) AS teachers_count
    FROM teachers
    WHERE phone IS NULL;


9.  
    INSERT INTO students 
    (name, surname, date_of_birth, fiscal_code, enrolment_date, registration_number, email, degree_id)
    VALUES 
    ('Giacomo', 'Poretti', '1976-05-22', 'MRGDFT76H25R089J', '2022-08-01', '12345', 'giacomo.poretti@università.it', 2);

10.  
    UPDATE teachers
    SET office_number = "126"
    WHERE id = 58;


11.  
    DELETE 
    FROM students
    WHERE id = 5002;

