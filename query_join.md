
# Traccia

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
Neuroscienze
3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)
7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
per ogni esame, stampando anche il voto massimo. Successivamente,
filtrare i tentativi con voto minimo 18.


# Soluzioni

1. SELECT degree_id, students.name, surname
FROM students 
JOIN degrees 
ON students.degree_id = degrees.department_id 
WHERE students.degree_id = 9

2. SELECT degrees.id, degrees.name, departments.name, level
FROM degrees
JOIN departments
ON degrees.department_id = departments.id
WHERE departments.id = 7 AND level = "magistrale"

3. SELECT courses.id, courses.name, courses.period, courses.year, courses.cfu, teachers.name, teachers.surname
FROM courses
JOIN course_teacher
ON course_teacher.course_id = courses.id
JOIN teachers
ON teachers.id = course_teacher.teacher_id
WHERE teachers.name = "Fulvio"

4. SELECT students.id, students.name, students.surname, degrees.name corso_di_laurea, departments.name dipartimenti
FROM students
JOIN degrees
ON students.degree_id = degrees.id
JOIN departments
ON degrees.department_id = departments.id
ORDER BY students.name, students.surname

5. SELECT degrees.id, degrees.name, courses.name, teachers.name, teachers.surname
FROM degrees
JOIN courses
ON courses.degree_id = degrees.id
JOIN course_teacher
ON courses.id = course_teacher.course_id
JOIN teachers
ON course_teacher.teacher_id = teachers.id

6. SELECT DISTINCT teachers.id, teachers.name, teachers.surname
FROM departments
JOIN degrees
ON departments.id = degrees.department_id
JOIN courses
ON courses.degree_id = degrees.id
JOIN course_teacher
ON courses.id = course_teacher.course_id
JOIN teachers
ON course_teacher.teacher_id = teachers.id

WHERE departments.id = 5

ORDER BY teachers.id