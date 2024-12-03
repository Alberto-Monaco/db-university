Testo esercizio:
Modellare la struttura di un database per memorizzare tutti i dati riguardanti una università:
sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
ogni Corso può essere tenuto da diversi Insegnanti;
ogni Corso prevede più appelli d'Esame;
ogni Studente è iscritto ad un solo Corso di Laurea;
ogni Studente può iscriversi a più appelli di Esame;
per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.
Utilizzare https://www.drawio.com/ per la creazione dello schema come visto in classe ed esportare quindi il diagramma in png caricandolo nella repo come fatto nel live coding questa mattina

## table name:

- dipartimenti
- corsi_laurea
- materie
- insegnanti
- studenti
- appelli

## table dipartimenti:

- id | BIGINT | PRIMARY KEY | AUTO_INCREMENT
- nome | VARCHAR(50)

## table corsi_laurea:

- id | BIGINT | PRIMARY KEY | AUTO_INCREMENT
- nome | VARCHAR(50)
- dipartimento_id | BIGINT | FOREIGN KEY

## table materie:

- id | BIGINT | PRIMARY KEY | AUTO_INCREMENT
- nome | VARCHAR(50)
- corsi_laurea_id | BIGINT | FOREIGN KEY

## table insegnanti:

- id | BIGINT | PRIMARY KEY | AUTO_INCREMENT
- nome | VARCHAR(50)
- cognome | VARCHAR(50)
- materie_id | BIGINT | FOREIGN KEY

## table studenti:

- id | BIGINT | PRIMARY KEY | AUTO_INCREMENT
- nome | VARCHAR(50)
- cognome | VARCHAR(50)
- corsi_laurea_id | BIGINT | FOREIGN KEY

## table appelli :

- id | BIGINT | PRIMARY KEY | AUTO_INCREMENT
- data | DATE
- materie_id | BIGINT | FOREIGN KEY

## table appello_studente (associazione tra appello e studente many to many):

- id | BIGINT | PRIMARY KEY | AUTO_INCREMENT
- appelli_id | BIGINT | FOREIGN KEY
- studenti_id | BIGINT | FOREIGN KEY
- voto | TINYINT
