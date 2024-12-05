TODO:

# Group by:

1. Contare quanti iscritti ci sono stati ogni anno
2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
3. Calcolare la media dei voti di ogni appello d'esame
4. Contare quanti corsi di laurea ci sono per ogni dipartimento

# Joins:

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

# BONUS:

7. Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

## table name:

- departments
- degrees
- courses
- teachers
- students
- exams
- course_teacher
- exams_student

---

# Group by:

1.  SELECT COUNT(id) as numero_iscritti, year(enrolment_date) as anno_accademico
    FROM students
    GROUP BY year(enrolment_date);

2.  SELECT COUNT(id) as numero_insegnanti, office_address
    FROM teachers
    GROUP BY office_address;

3.  SELECT AVG(vote) as media_voti, exam_id
    FROM exam_student
    GROUP BY exam_id;

4.  SELECT COUNT(id) as numero_corsi_laurea, department_id
    FROM degrees
    GROUP BY department_id;

# Joins:

1.  SELECT students.id, students.name, students.surname, degrees.name
    FROM students
    JOIN degrees ON students.degree_id = degrees.id
    WHERE degrees.name = 'Corso di Laurea in Economia';

2.  SELECT degrees.name, degrees.level
    FROM degrees
    JOIN departments ON degrees.department_id = departments.id
    WHERE departments.name = 'Dipartimento di Neuroscienze'
    AND degrees.level = 'magistrale';

3.  SELECT courses.name, teachers.name, teachers.surname
    FROM course_teacher
    JOIN courses ON course_teacher.teacher_id = teachers.id
    WHERE teachers.id = 44;

4.  SELECT students.id, students.name, students.surname, degrees.name, departments.name
    FROM students
    JOIN degrees ON students.degree_id = degrees.id
    JOIN departments ON degrees.department_id = departments.id
    ORDER BY students.surname, students.name;

5.  SELECT degrees.name, courses.name, teachers.name, teachers.surname
    FROM degrees
    JOIN courses ON courses.degree_id = degrees.id
    JOIN course_teacher ON course_teacher.course_id = courses.id
    JOIN teachers ON course_teacher.teacher_id = teachers.id

6.  SELECT teachers.name, teachers.surname, courses.name, departments.name
    FROM teachers
    JOIN course_teacher ON course_teacher.teacher_id = teachers.id
    JOIN courses ON course_teacher.course_id = courses.id
    JOIN degrees ON courses.degree_id = degrees.id
    JOIN departments ON degrees.department_id = departments.id
    WHERE departments.name = 'Dipartimento di Matematica';
