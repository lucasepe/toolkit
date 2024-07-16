## `wactl` (Come fare per...)

Abilitare le opzioni sviluppatore sul tuo telefono
==========================================================================

Il tuo telefono ha diverse opzioni per sviluppatori che possono essere 
utilizzate da questi a scopo di test. Queste opzioni sono tipicamente 
nascoste dai produttori.

Segui questi passaggi per abilitare il menu delle opzioni sviluppatore:

1. Vai su "Impostazioni" > "Sistema"

2. Tocca "Informazioni sul telefono"

3. Tocca quindi sette volte l'opzione "Numero build" per abilitare 
   la Modalità Sviluppatore. 
   Vedrai un messaggio di conferma quando avrà effetto.

4. Torna alla schermata principale delle "Impostazioni", e dovresti 
   vedere un nuovo menu delle "Opzioni Sviluppatore" a cui puoi accedere.

5. Entra e abilita l'opzione di debug USB

Ora il tuo telefono è pronto per comunicare con il tuo computer.

Installare Android Debug Bridge (adb)
==========================================================================

wactl dipende dal tool Android Debug Bridge (adb), che è il modo ufficiale
fornito per interagire con i dispositivi Android tramite il terminale
da desktop e laptop.

Puoi scaricare Android SDK Platform Tools per il tuo sistema operativo qui:

   https://developer.android.com/tools/releases/platform-tools

Estrai i contenuti di questo file ZIP in una cartella facilmente accessibile.

Per accedere al tool adb da qualsiasi directory, devi semplicemente aggiungere
la directory adb alla variabile PATH del tuo sistema operativo.

Di seguito ecco dei modi più semplici per installare lo strumento sui diversi
sistemi operativi.

MacOS
-----
Se sei un utente di Homebrew (https://brew.sh/), il modo più facile
per installare adb su MacOS è:

   brew install --cask android-platform-tools

Linux
-----
Per Ubuntu/Debian:

   sudo apt install adb

Per Fedora Linux:

   sudo dnf install android-tools

Per Arch Linux:

   sudo pacman -S android-tools

Windows
-------
Se sei un utente di Chocolatey (https://chocolatey.org/install):

    choco install adb


Formato del file CSV dei contatti
==========================================================================

Ogni riga nel file CSV dei contatti è composta da quattro campi:

    FirstName,LastName,BirthDate,MobileNumber

- Il formato della Data di nascita (BirthDate) è: ISO 8601 (https://en.wikipedia.org/wiki/ISO_8601)

    Esempio: 8 gennaio 1971 deve essere scritto come "1971-01-08"

- Il formato del Numero di cellulare (MobileNumber) è: E.164 (https://en.wikipedia.org/wiki/E.164)

    Esempio: [+][codice del paese][codice di area][numero dell'abbonato]


Modelli di messaggio in formato TXT
==========================================================================

Il tuo messaggio può essere eventualmente 'templatizzato' utilizzando 
segnaposto e funzioni.

Esempio (un contenuto probabile del tuo file 'promo.txt'):

    Ciao {{ .FirstName }}!

    {{- $days := daysUntilNextBirthday .BirthDate -}}
    {{ if lt $days 6 }}

    Tra {{ $days }} giorni è il tuo compleanno e
    abbiamo pensato di farti un regalo!

    Ecco il tuo personalissimo codice sconto: XXXXXX.
    {{ end -}}

    Ti aspettano tante novità nel nostro negozio, vieni 
    a dare un'occhiata!

Spiegazione:

  Questo modello serve a creare un messaggio personalizzato. 
  Rende il messaggio speciale includendo il nome della persona 
  e dandogli un codice sconto se il suo compleanno è entro i 
  prossimi 6 giorni.

  Ecco come funziona:

    - Il messaggio inizia con "Ciao" seguito dal nome della persona.
      Il segnaposto {{ .FirstName }} è utilizzato per inserire il nome della
      persona nel messaggio.

    - Il modello calcola quanti giorni mancano al prossimo compleanno della persona.
      Questo calcolo è fatto utilizzando la data di nascita della persona.
      Il risultato è memorizzato in una variabile chiamata $days.

    - Il modello controlla se il compleanno della persona è entro i prossimi 6 giorni.
      Questo è fatto utilizzando un'istruzione "if": {{ if lt $days 6 }}. Se mancano
      meno di 6 giorni al compleanno, viene incluso il prossimo pezzo del messaggio.

    - Se la condizione è soddisfatta (cioè, il compleanno è entro i prossimi 6 giorni),
      il messaggio informa la persona di quanti giorni mancano al suo compleanno e
      menziona che è in arrivo un regalo.
      Il numero esatto di giorni è inserito utilizzando il segnaposto {{ $days }}.

  In sintesi, questo modello personalizza un messaggio con il nome del destinatario,
  controlla se il suo compleanno è prossimo e, in caso positivo, include un messaggio
  speciale di compleanno e un codice sconto.
  In caso contrario, invita semplicemente il destinatario a esplorare nuovi articoli nel negozio.
  