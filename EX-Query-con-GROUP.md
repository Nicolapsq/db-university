1. Contare quanti iscritti ci sono stati ogni anno

```sql
SELECT YEAR(enrolment_date),
COUNT(YEAR(enrolment_date)) AS "numeri studenti"
FROM students
GROUP BY YEAR(enrolment_date);
```

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql
SELECT office_number,
count(*) AS "numero insegnanti"
FROM teachers
GROUP BY office_number;
```

3. Calcolare la media dei voti di ogni appello d'esame

```sql
SELECT exam_id AS "appello esame",
AVG(vote) AS media_voti
FROM exam_student
GROUP BY exam_id
ORDER BY exam_id;
```

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

```sql

```
