# `wactl`

Invia messaggi pubblicitari su WhatsApp usando Android Debug Bridge (adb).

Il tool wactl invia messaggi personalizzati su WhatsApp ai tuoi contatti.
Fornisci semplicemente un file CSV con tutti i tuoi contatti e un file TXT
con il modello del messaggio. Puoi anche inviare immagini!

PREREQUISITI

 * Un dispositivo Android con le "Opzioni Sviluppatore" abilitate
   e che abbia installato WhatsApp
 * Un PC su cui è installato Android Debug Bridge (adb)

wactl dipende dal tool Android Debug Bridge (adb), che è il modo 
ufficiale di interagire con i dispositivi Android tramite il terminale
da desktop e laptop.

Consulta il file [HOWTO](HOWTO_it.md) per le istruzioni su come abilitare
le opzioni sviluppatore Android sul tuo telefono e su come installare
Android Debug Bridge (adb) sul tuo PC.

Il file [DOWNLOAD](DOWNLOAD.md) contiene tutti i links per scaricare i binari
per il tuo sistema operativo e la tua architettura.

Per specificare il PIN di sblocco dello schermo hai due opzioni:

 * imposta la variabile di ambiente WACTL_PIN
 * utilizza il flag -pin=XXX ogni volta

Se trovi utile questo strumento, considera di fare una donazione:

  * https://www.paypal.com/donate?hosted_button_id=WSXXQ36U37FMJ

Il tuo supporto mi motiva a continuare lo sviluppo e il miglioramento 
di questo software.

Dopo aver effettuato una donazione, per favore inviami una email con 
la tua "App Key", e io ti invierò la licenza che sblocca tutte le 
funzionalità.

Se hai una licenza per sbloccare tutte le funzionalità, crea la
variabile di ambiente WACTL_LIC per memorizzare la licenza.

Grazie per la tua generosità!