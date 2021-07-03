# tgcloud
Backup data on telegram with linux Docker/VM WSL | it works with windows just slower...
Based on pip module "telethon"

# Italiano

# REQUISITI<br>
<br>python3, pip3, colorama, telethon<br>
<br>python3 -m pip install telethon colorama;<br>


PRIMA DI ESEGUIRE IL BACKUP OCCORRE RECUPERARE I DATI DEL PROPRIO ACCOUNT<br>
<br>Recuperare quindi api_id e api_hash e aggiungerli al file di configurazione "config.py";<br>
 <br> per fare questo seguire questa guida: https://docs.telethon.dev/en/latest/basic/signing-in.html<br>
  
  <br>Inserire anche il chatid: eseguire ids.py (python3 ids.py presente nella repository), dopo essersi registrati con il numero di cellulare es. +393335553355 verranno visualizzate tutte le chat di Telegram<br>
  <br> Oppure apprite telegram desktop e recuperare l'id dall'URL (vecchia versione)<br>
  <br> Oppure Usare un bot da telegram per smartphone come IdBot<br>
  <br>Copiare quindi il chatid dentro a config.py<br>
  <br>UNA VOLTA EFFETTUATO IL BACKUP NON VARIARE I PARAMETRI DI "max_size" QUESTO COMPORTEREBBE DEI PROBLEMI NEL RIPRISTINO DEI DATI COMPRESSI DIVISI (per limite di 2GB per file imposto da Telegram)


# COME FUNZIONA

Eseguire python3 backup.py per eseguire un backup<br>
Eseguire python3 restore.py per eseguire il ripristino dei dati



NOTE

 - Attenzione alla cartella temporanea "dirar" poichè in base ai pormessi potrebbe essere necessario crearla manualmente
 - I file di testo devo contenere almento un carattere, telethon non elabora file vuoti, quelli vuoti non erranno considerati come le cartelle vuote
 - I file maggiori di due GB non possono essere caricati su telegram, per questo è necessario settare una dimensione inferiore ai 2GB alla variabile maxsize in config.py
 - I file di dimensione maggiore di maxsize verranno divisi in file di dimensione specificata in MB
 - Il programma è stato pensato per effettuare backup di file singoli, se lo stesso file (basato su MD5) è presente in percorsi diversi verrà caricato un solo file quello con percorso più lungo o con ordine alfabetico più vicino alla Z
 - Il programma si basa sul codice hash MD5 generato da un File, quindi modificando il nome o il percorso non verrebbe caricato, ma viene comunque aggiornata la variazione
 - Non garantisto la sicurezza e l'integrità dei file backuppati, non mi assumo quindi nessuna responsabilità per eventuali "falle del programma" e per perdita di dati, testate bene il programma PRIMA di usarlo con dati importanti (consiglio di non usarlo per dati importanti CAUTELA!)
