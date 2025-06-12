1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql
SELECT
students.id,
students.name,
students.surname,
students.email,
degrees.name
FROM students
INNER JOIN degrees
ON degrees.id = students.degree_id
WHERE degrees.name = "Corso di Laurea in Economia"
```

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

```sql
SELECT
degrees.id,
degrees.name,
degrees.level,
departments.id,
departments.name,
departments.address
FROM degrees
INNER JOIN departments
ON departments.id = degrees.department_id
WHERE departments.name = "Dipartimento di Neuroscienze"
AND degrees.level = "magistrale"
```

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```sql
SELECT *
FROM courses
INNER JOIN course_teacher
ON course_teacher.course_id = courses.id
INNER JOIN teachers
ON course_teacher.teacher_id = teachers.id
WHERE teachers.name = "Fulvio"
AND teachers.surname = "Amato"
```

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```sql
SELECT
students.id AS student_id,
students.surname,
students.name,
degrees.id AS degree_id,
degrees.name AS degree_name,
departments.id AS departments_id,
departments.name AS department_name
FROM students
INNER JOIN degrees
ON degrees.id = students.degree_id
INNER JOIN departments
ON departments.id = degrees.department_id
ORDER BY students.surname, students.name
```

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```sql
SELECT
courses.id AS "course_id",
courses.name AS "course_name",
degrees.id AS "degree_id",
degrees.name AS "degree_name",
teachers.id AS "teacher_id",
teachers.name AS "teacher_name",
teachers.surname AS "teacher_surname"
FROM courses
INNER JOIN degrees
ON degrees.id = courses.degree_id
INNER JOIN course_teacher
ON course_teacher.course_id = courses.id
INNER JOIN teachers
ON course_teacher.teacher_id = teachers.id
```

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```sql
SELECT DISTINCT # DISTINCT elimina i duplicati
teachers.id,
teachers.name,
teachers.surname,
departments.name
FROM teachers
INNER JOIN course_teacher
ON teachers.id = course_teacher.teacher_id
INNER JOIN courses
ON courses.id = course_teacher.course_id
INNER JOIN degrees
ON degrees.id = courses.degree_id
INNER JOIN departments
ON departments.id = degrees.department_id
WHERE departments.name = "Dipartimento di Matematica"
ORDER BY teachers.name
```

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

```sql
SELECT
students.id AS "student_id",
students.name,
students.surname,
exams.course_id,
COUNT(*) AS "tentativi",
MAX(vote) AS "voto_massimo"
FROM students
INNER JOIN exam_student
ON students.id = exam_student.student_id
INNER JOIN exams
ON exams.id = exam_student.exam_id
WHERE vote >= 18
GROUP BY
students.id,
students.name,
students.surname,
exams.course_id
HAVING voto_massimo >= 18
```
