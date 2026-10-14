# PROGETTO_INTERMEDIO

## Descrizione del progetto
 
Questo progetto implementa in linguaggio **C++** la classe 'LidarDriver'.  
Il sensore misura distanze su un arco di 180 gradi (da 0° a 180°) con una certa risoluzione angolare. Il driver conserva le ultime 10 scansioni ricevute in un **buffer circolare**, e permette di inserire nuove scansioni, leggerle, interrogarle per angolo e svuotare il buffer.
 
Il progetto è stato sviluppato in gruppo per il corso di **Laboratorio di Programmazione** (progetto intermedio).
 
---
 
## Struttura del Progetto
 
PROGETTO_INTERMEDIO/
    ├── progetto.exe
    ├── include/
    │   ├── lidar_driver.h
    ├── src/
    │   ├── lidar_driver1.cpp
    │   ├── lidar_driver2.cpp
    │   ├── lidar_driver3.cpp
    │   ├── main.cpp
 
 
Suddivisione dei file:
 
lidar_driver.h:
Contiene la dichiarazione della classe 'LidarDriver' e dell'overloading dell'operatore '<<'.
 
lidar_driver1.cpp:
Contiene le funzioni 'get_scan' e 'get_distance'.
 
lidar_driver2.cpp:
Contiene il costruttore e le funzioni 'new_scan' e 'clear_buffer'.
 
lidar_driver3.cpp:
Contiene l'overloading dell'operatore '<<' e la funzione 'get_last'.
 
main.cpp:
Programma di prova che crea due oggetti 'LidarDriver' (con risoluzione 1 e 0.5), inserisce delle scansioni e verifica il funzionamento delle varie funzioni.
 
'progetto.exe' è l'eseguibile già compilato del programma di prova.
 
---
 
## Funzionamento
 
- **Scansioni e risoluzione:**  
  Ogni scansione è un 'vector<double>' con una distanza per ogni angolo misurato.  
  Il numero di letture per scansione dipende dalla risoluzione: con risoluzione 1 ogni scansione ha 181 letture, con risoluzione 0.5 ne ha 361.  
  Se una scansione inserita contiene meno letture del previsto, viene completata con zeri; se ne contiene di più, quelle in eccesso vengono scartate.
 
- **Buffer circolare:**  
  Le scansioni sono salvate in un 'array' di 10 posizioni. Quando il buffer è pieno, la nuova scansione sostituisce quella meno recente.  
  Lo stato del buffer è gestito con tre variabili: 'front_scan' (scansione meno recente), 'back_scan' (posizione della prossima scansione da scrivere) e 'size' (numero di scansioni presenti).
 
- **Distanza a un angolo:**  
  'get_distance' restituisce la lettura corrispondente all'angolo richiesto nella scansione più recente. Se l'angolo non coincide esattamente con una misura, restituisce la media delle due letture più vicine.
 
---
 
## Funzioni principali
 
- 'LidarDriver(double resolution)': crea il driver con la risoluzione indicata (compresa tra 0 escluso e 1 incluso).
- 'new_scan(const vector<double>& scan)': aggiunge una nuova scansione al buffer.
- 'get_scan()': restituisce la scansione più vecchia e la rimuove dal buffer.
- 'get_distance(double angle)': restituisce la distanza all'angolo indicato nella scansione più recente.
- 'get_last()': restituisce la scansione più recente senza rimuoverla.
- 'clear_buffer()': elimina tutte le scansioni salvate.
- 'operator<<': stampa a schermo la scansione più recente.
- 'empty()': indica se il buffer è vuoto.
 
---
 
## Documentazione
 
- Il codice è commentato direttamente nei file sorgente e nell'header.
 
---
 
## Autori
 
Luca Daniele Berardocco  
Tommaso  
Marco 
 
Suddivisione del lavoro:
- 'lidar_driver1.cpp': Luca Daniele Berardocco
- 'lidar_driver2.cpp': Tommaso 
- 'lidar_driver3.cpp': Marco 
- 'lidar_driver.h' e 'main.cpp': sviluppati insieme da tutti i membri del gruppo
 
Corso: Laboratorio di Programmazione  
A.A. 2024/2025
