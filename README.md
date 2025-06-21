# Monitoraggio WiFi con ESP8266 e InfluxDB Cloud

Questo repository contiene un esempio di codice sorgente Arduino per connettere una scheda di sviluppo **ESP8266** a **InfluxDB Cloud**. L'obiettivo è mostrare come inviare dati di monitoraggio (ad esempio, la potenza del segnale WiFi) da un dispositivo IoT a un database time-series basato su cloud.

-----

## Caratteristiche

  * **Connessione WiFi**: Stabilisce una connessione a una rete WiFi specificata.
  * **Lettura RSSI**: Ottiene la potenza del segnale RSSI (Received Signal Strength Indicator) della rete WiFi connessa.
  * **Invio Dati a InfluxDB Cloud**: Invia i dati RSSI, insieme ad altri metadati (come il nome dell'host dell'ESP8266), a un bucket InfluxDB Cloud.
  * **Facile Configurazione**: Le credenziali WiFi e InfluxDB sono gestite tramite variabili nel codice sorgente.

-----

## Prerequisiti

Prima di iniziare, assicurati di avere:

  * Una scheda di sviluppo **ESP8266** (es. NodeMCU, ESP-01S, Wemos D1 Mini).
  * **Arduino IDE** installato.
  * Il **core ESP8266** installato nell'Arduino IDE (Gestore Schede).
  * Le seguenti librerie installate nell'Arduino IDE (Gestore Librerie):
      * `ESP8266WiFi` (di solito inclusa con il core ESP8266)
      * `ESP8266HTTPClient` (di solito inclusa con il core ESP8266)
      * `InfluxDbClient` (dovrai installarla manualmente, cerca "InfluxDbClient" nel Gestore Librerie o installala da qui: [https://github.com/tobiasschuerg/InfluxDbClient](https://www.google.com/search?q=https://github.com/tobiasschuerg/InfluxDbClient))
  * Un account **InfluxDB Cloud** configurato con un'organizzazione, un bucket e un token API.

-----

## Configurazione

1.  **Clona il repository:**

    ```bash
    git clone https://github.com/emanbuc/monitoraggio_wifi.git
    ```

2.  **Apri il progetto in Arduino IDE:** Apri il file `misuratore_wifi.ino` con l'Arduino IDE.

3.  **Aggiorna le Credenziali:** Modifica le seguenti righe nel file `misuratore_wifi.ino` con le tue credenziali e impostazioni di InfluxDB Cloud:

    ```cpp
    #define WIFI_SSID "IL_TUO_SSID_WIFI"        // Il nome della tua rete WiFi
    #define WIFI_PASSWORD "LA_TUA_PASSWORD_WIFI" // La password della tua rete WiFi

    #define INFLUXDB_URL "https://us-east-1-1.aws.cloud2.influxdata.com" // L'URL della tua istanza InfluxDB Cloud
    #define INFLUXDB_TOKEN "IL_TUO_TOKEN_INFLUXDB" // Il token API di InfluxDB
    #define INFLUXDB_ORG "LA_TUA_ORGANIZZAZIONE_INFLUXDB" // Il nome della tua organizzazione InfluxDB
    #define INFLUXDB_BUCKET "IL_TUO_BUCKET_INFLUXDB" // Il nome del bucket InfluxDB dove verranno salvati i dati

    #define DEVICE "ESP8266-Monitor" // Nome identificativo per il tuo dispositivo
    ```

    Assicurati di sostituire i placeholder con i tuoi valori effettivi.

-----

## Compilazione e Caricamento

1.  **Seleziona la scheda e la porta:** Nell'Arduino IDE, vai su `Strumenti > Scheda` e seleziona la tua scheda ESP8266 (ad esempio, "NodeMCU 1.0 (ESP-12E Module)"). Poi, vai su `Strumenti > Porta` e seleziona la porta seriale a cui è collegato il tuo ESP8266.
2.  **Carica il codice:** Clicca sul pulsante "Carica" (freccia a destra) nell'Arduino IDE per compilare e caricare il codice sulla tua scheda ESP8266.
3.  **Monitor Seriale:** Apri il Monitor Seriale (Strumenti \> Monitor Seriale) per vedere i messaggi di debug e verificare che l'ESP8266 si stia connettendo e inviando i dati correttamente.

-----

## Utilizzo

Una volta caricato il codice, l'ESP8266 si connetterà automaticamente alla rete WiFi configurata e inizierà a inviare i dati RSSI al tuo bucket InfluxDB Cloud a intervalli regolari (definiti nel codice, tipicamente ogni 10 secondi).

Puoi visualizzare e analizzare questi dati direttamente nella tua interfaccia InfluxDB Cloud, creando dashboard o eseguendo query con Flux.

-----

## Contributi

Sentiti libero di clonare, modificare e migliorare questo codice. Se hai suggerimenti o incontri problemi, apri una issue o proponi una pull request.

-----

## Licenza

Questo progetto è rilasciato sotto licenza MIT. Per maggiori dettagli, consulta il file `LICENSE` (se presente nel repository, altrimenti puoi aggiungerne uno standard MIT).

-----
