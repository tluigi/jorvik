# Gaia Jovik

Jorvik è il nome in codice del progetto di ridisegno del software del **Progetto Gaia** Croce Rossa Italiana
([GitHub](https://github.com/CroceRossaCatania/gaia), [Web](https://gaia.cri.it)).

I punti chiave nella riprogettazione sono i seguenti:
* Raccogliere il feedback ottenuto tramite <feedback@gaia.cri.it>,
* Raccogliere le necessità espresse dagli utenti tramite il Supporto,
* Raccogliere le nuove necessità dell'Associazione,

## Sviluppo

Sei interessato a partecipare allo sviluppo di Gaia/Jorvik? Contattaci all'indirizzo e-mail <sviluppo@gaia.cri.it>!

### Integrazione continua

Jorvik viene installato e testato sulle recenti versioni di Python 2 e 3, in modo automatico, da Travis CI ad ogni push.

Stato attuale di `master`: [![Build Status](https://travis-ci.org/CroceRossaItaliana/jorvik.svg?branch=master)](https://travis-ci.org/CroceRossaItaliana/jorvik)

### Documentazione

Puoi trovare la **[Documentazione sul Wiki del progetto](https://github.com/CroceRossaItaliana/jorvik/wiki)**.

### Requisiti

* **[Python 2.7-3.x](https://www.python.org/downloads/)** (es. `python3`)
* **[PIP 2 o 3](https://www.python.org/downloads/)** (es. `pip3`)
* **[MySQL Community Server 5.5+](https://dev.mysql.com/downloads/mysql/)**, o [MariaDB 10.x](https://mariadb.org/), o [PostgreSQL](http://www.postgresql.org/) con [PostGIS](http://postgis.net/))
* **[GEOS](http://trac.osgeo.org/geos/)** (Geometry Engine Open Source)
* **Linux**, Mac OS X e, probabilmente, Windows Server 2008 o 7 e superiori

```bash
# Ubuntu 14.10+ (installa i Requisiti sopra indicati)
sudo apt-get install git python3-pip mysql-server binutils libproj-dev gdal-bin python3-dev libmysqlclient-dev
```

### Installazione e configurazione

1. **Scarica Jorvik** usando git
  
    ```bash
    git clone https://github.com/CroceRossaItaliana/jorvik 
    cd jorvik
    ```
  
2. **Installa i moduli** necessari usando **pip3**
    
    ```bash
    sudo pip3 install -r requirements.txt
    ```
    
4. **Database** 
  1. Crea un file di configurazione MySQL copiando quello di esempio
  
    ```bash
    cp config/mysql.cnf{.sample,}
    ```
  
  2. Crea un database per Jorvik, es. con nome `jorvik`
  
    ```bash
    mysql -u root -p -e 'CREATE DATABASE jorvik CHARSET utf8;'
    ```
    
  3. Modifica `config/mysql.cnf` con le credenziali ed il nome del database creato
  4. Crea tutte le tabelle di database necessarie
  
    ```bash
    python3 ./manage.py syncdb
    ```
    
4. **Posta, debug, chiave di produzione**
  * Fare quanto al punto (1.1) per tutti i file `config/*.cnf.sample` che si vuole personalizzare 
5. **Assets (CSS, JS, Immagini)**
  * Per creare la cartella `assets` e riempirla di contenuti
  
    ```bash
    python3 ./manage.py collectstatic
    ```

6. **Avvia il server** 
  * Per avviare il server su [http://localhost:8000/](http://localhost:8000)
    
    ```bash
    python3 ./manage.py runserver
    ```
    
    
    

[JetBrains PyCharm](https://www.jetbrains.com/pycharm/) racchiude gli strumenti Django in un buon IDE.