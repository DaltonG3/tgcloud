# tgcloud
Backup data on telegram with linux Docker/VM WSL
Based on pip module "telethon"

# Italiano

# REQUISITI<br>
<br>python3-pip unrar sqlite3 dos2unix rar;<br>
<br>python3 -m pip install telethon;<br>


PRIMA DI ESEGUIRE IL BACKUP OCCORRE RECUPERARE I DATI DEL PROPRIO ACCOUNT<br>
<br>Recuperare quindi api_id e api_hash e aggiungerli al file di configurazione "config.txt";<br>
 <br> per fare questo seguire questa guida: https://docs.telethon.dev/en/latest/basic/signing-in.html<br>
  
  <br>Inserire anche il chatid: eseguire ids.py (python3 ids.py), dopo essersi registrati con il numero di cellulare es. +393335553355 verranno visualizzate tutte le chat di Telegram<br>
  <br> Oppure apprite telegram desktop e recuperare l'id dall'URL<br>
  <br> Oppure Usare un bot da telegram per smartphone<br>
  <br>Copiare quindi il chatid dentro a config.txt<br>
  <br>UNA VOLTA EFFETTUATO IL BACKUP NON VARIARE I PARAMETRI DI "max_size" e "rar_size" QUESTO COMPORTEREBBE DEI PROBLEMI NEL RIPRISTINO DEI DATI COMPRESSI .RAR


# COME FUNZIONA

Eseguire ./backup.sh per eseguire un backup<br>
Eseguire ./restore.sh per eseguire il ripristino dei dati

NOTE

 - Attenzione alla cartella temporanea "dirar" poichè in base ai pormessi potrebbe essere necessario crearla manualmente
 - I caratteri speciali apice e punto esclamativo verranno rimossi dal nome di file e cartelle
 - I file di testo devo contenere almento un carattere, telethon non elabora file vuoti
 - I file maggiori di due GB non possono essere caricati su telegram, per questo è necessario settare una dimensione inferiore ai 2GB alla variabile max_size in B in config.txt
 - I file di dimensione maggiore di $max_size verranno compressi in file di dimensione $rarsize in KB
 - Il programma è stato pensato per effettuare backup di file singoli, se lo stesso file è presente in percorsi diversi verrà caricato un solo file quello con percorso più lungo o con ordine alfabetico più vicino alla Z
 - Il programma si basa sul codice hash MD5 generato da un File, quindi modificando il nome o il percorso non verrebbe caricato, ma viene comunque aggiornato a DB la variazione
 - Ripristinando un database "vecchio" vengono ripristinati i file allo stato in cui erano nel momento del backup, non vengono intaccati i file aggiunti successivamente
 - Per il momento il programma funziona bene come "disaster recovery", successivamente verrà aggiunta la funzionalità di ripristino del file singolo, ora è più da intendersi come "o tutto o niente"
 - Non garantisto la sicurezza e l'integrità dei file backuppati, non mi assumo quindi nessuna responsabilità per eventuali "falle del programma" e per perdita di dati, testate bene il programma prima di usarlo con dati importanti (consiglio di non usarlo per dati importanti CAUTELA!)
