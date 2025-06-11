1. Selezionare tutti gli studenti nati nel 1990 (160)

```sql
SELECT COUNT(*) AS nati_nel_1990stu
FROM students
WHERE date_of_birth BETWEEN '1990-01-01' AND '1990-12-31';
```

2. Selezionare tutti i corsi che valgono più di 10 crediti (479)

```sql
SELECT COUNT(cfu) AS superiore_a_10_crediti
FROM courses
WHERE cfu >10
```

3. Selezionare tutti gli studenti che hanno più di 30 anni

```sql
SELECT COUNT(*) AS studenti_che_hanno_più_di_30_anni 
FROM students
WHERE year(curdate()) - year(date_of_birth) > 30;
```

4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)

```sql
SELECT COUNT(*) AS tutti_i_corsi_del_primo_semestre_e_primo_anno 
FROM courses
WHERE period = 'I semestre'
AND year = '1';
```

5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)

```sql
SELECT COUNT(*) AS appelli_che_avvengono_nel_pomeriggio_dopo_le_14_del_20_06_2020 
FROM exams
WHERE hour > '14:00:00'
AND date = '2020-06-20';
```

6. Selezionare tutti i corsi di laurea magistrale (38)

```sql
SELECT COUNT(*) AS tutti_i_corsi_di_laurea_magistrale 
FROM degrees
WHERE level = 'Magistrale';
```
oppure

```sql
SELECT COUNT(*) AS tutti_i_corsi_di_laurea_magistrale 
FROM degrees
WHERE name LIKE '%Magistrale%';
```

7. Da quanti dipartimenti è composta l'università? (12)

```sql
SELECT COUNT(*) AS "dipartimenti_dell'università" 
FROM departments;
```

8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

```sql
SELECT COUNT(*) AS "Insegnanti che hanno il numero di telefono" 
FROM teachers
WHERE phone
```