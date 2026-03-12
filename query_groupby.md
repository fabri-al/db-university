
# Tracce

1. Contare quanti iscritti ci sono stati ogni anno
2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
3. Calcolare la media dei voti di ogni appello d'esame
4. Contare quanti corsi di laurea ci sono per ogni dipartimento


# Soluzioni

1. SELECT enrolment_date, COUNT(*) AS iscritti_per_anno
FROM university.students
GROUP BY enrolment_date

2. SELECT office_address, COUNT(*) AS insegnati_unico_palazzo
FROM university.teachers
GROUP BY office_address

3. SELECT AVG(vote) AS media_voti
FROM university.exam_student
GROUP BY vote

4. SELECT department_id, name, COUNT(*)
FROM university.degrees
GROUP BY department_id, name