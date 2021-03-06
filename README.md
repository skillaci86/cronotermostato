<img src="https://img.shields.io/badge/Versione-1.2-brightgreen">  <a href="https://forum.hassiohelp.eu/showthread.php?tid=503"><img src="https://img.shields.io/badge/Forum-hassiohelp-blue"> <img src="https://img.shields.io/badge/Aggiornato-si-orange"></a>
<br> 
<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/schermata_iniziale.png" alt="Immagine cronotermostato">


<p align="center"/> <b>Change log V1.2:</b> <br> </p>
Quando il termostato è in modalità manuale e si passa in modalità auto o preriscaldamento e l'ora è fuori dall'intervallo di tempo impostato per l'accensione (e anche il tracking per la modalità auto), il termostato si spegne per poi accendersi all'ora impostata.<br>
In modalità auto se si esce di casa, il termostato si spegne ed invia un messaggio per avvisare del cambiamento di stato.<br>
Sempre per la modalità auto, se si è fuori casa e poi si rientra, il termostato si accende appena il tracker viene rilevato.<br><br>
<p align="center"/> <b>Package Cronotermostato per Home Assistant.</b> <br> </p>
Questo package crea una serie di entità ed automazioni per fare in modo che il termostato funzioni in varie 
modalità selezionabili dall’utente e che sia possibile accenderlo in determinati orari e se si è o meno in casa. <br>
Vediamo come installarlo. <br>
<br>
<p align="center"/> <b>Prerequisiti</b> <br> </p>
Per funzionare ha bisogno o di un'entità climate già installata oppure di 2 entità: uno switch che attivi e disattivi il termostato ed un sensore di temperatura. <br>
Per installare questo package avrete bisogno di:<br>
1. aver configurato <a href="https://hassiohelp.eu/2018/11/30/package-configurazione/">i packages</a><br>
2. installare <a href="https://github.com/custom-cards/button-card">button-card, </a> <a href="https://github.com/thomasloven/lovelace-card-mod"> card-mod </a> e <a href="https://github.com/thomasloven/lovelace-state-switch">state-switch</a>  (da HACS)<br><br>

<p align="center"/> <b>Installazione con entità climate non pre installata</b> <br> </p>
Scaricare il file cronotermostato-master.zip (clone or download in alto a destra e poi download zip) e decomprimere i file. <br>
Copiare i file in questo modo:<br>
Pkg_cronotermostato_v1_2.yaml nella cartella packages <br>
blu.jpg e fiamma.gif nella cartella www/immagini/lovelace/<br>

Aprire il file Pkg_cronotermostato_v1_2.yaml ed effettuare le seguenti modifiche:<br>
1. sostituire switch.caldaia con lo switch che accende il termostato (riga 12)<br>
2. sostituire sensor.temperature con il sensore della temperatura (riga 13)<br>
3. sostituire device_tracker.dispositivo con il proprio device_tracker (riga 14)<br>
4. sostituire la zona home con la propria zona se è diversa (riga 15)<br>
5. sostituire il servizio di notifica con il proprio (riga 16)<br>
6. se non si ha già il sensor.time, togliere i commenti (righe da 102 a 105)<br>
7. sostituire sensor.sensore_temperature con il proprio (riga 497)<br>
8. se volete un’isteresi, ovvero che il termostato si spenga ad una temperatura superiore o che si riaccenda 
ad una inferiore a quella impostata, dovrete modificare hot_tolerance e cold_tolerance. 
Esempio: impostando la temperatura a 23 e impostando cold_tolerance a 2 e hot_tollerance a 0, il termostato si spegnerà 
quando arriverà a 23 gradi e si riaccenderà a 21. Di default sono impostati cold_tolerance: 0.5 e hot_tolerance: 0.<br>
Riavviare home assistant<br><br>

<p align="center"/> <b>Installazione con entità climate già installata</b> <br> </p>
Scaricare il file cronotermostato-master.zip (clone or download in alto a destra e poi download zip) e decomprimere i file. <br>
Copiare i file in questo modo:<br>
Pkg_cronotermostato_v1_2_no_climate.yaml nella cartella packages <br>
blu.jpg e fiamma.gif nella cartella www/immagini/lovelace/<br>

Aprire il file Pkg_cronotermostato_v1_2_no_climate.yaml ed effettuare le seguenti modifiche:<br>
1. sostituire device_tracker.dispositivo con il proprio device_tracker (riga 12)<br>
2. sostituire la zona home con la propria zona se è diversa (riga 13)<br>
3. sostituire il servizio di notifica con il proprio (riga 14)<br>
4. sostituire climate.termostato con il proprio (riga 15)<br>
4. se non si ha già il sensor.time, togliere i commenti (righe da 88 a 91)<br>
7. sostituire sensor.sensore_temperature con il proprio (riga 483)<br>
8. se volete un’isteresi, ovvero che il termostato si spenga ad una temperatura superiore o che si riaccenda 
ad una inferiore a quella impostata, dovrete modificare hot_tolerance e cold_tolerance. 
Esempio: impostando la temperatura a 23 e impostando cold_tolerance a 2 e hot_tollerance a 0, il termostato si spegnerà 
quando arriverà a 23 gradi e si riaccenderà a 21. Di default sono impostati cold_tolerance: 0.5 e hot_tolerance: 0.<br>
Riavviare home assistant<br><br>
<p align="center"/> <b>Per la configurazione della card:</b><br> </p>
Per chi usa la modalità raw, creare una nuova card e copiare il contenuto di lovelace_raw.yaml.<br>
Per chi usa la modalità yaml, aprire il file lovelace_yaml.yaml e copiare il contenuto nel proprio file lovelace. <br>
In entrambe le modalità dovrete sostituire sensor.temp con il vostro sensore e switch.caldaia (ce ne sono 2) con il
vostro switch.<br><br>
<p align="center"/> <b>Funzionamento</b><br> </p>
<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/schermata_iniziale.png" alt="Immagine cronotermostato"></p>
Nella card principale vi ritroverete in alto a sinistra un ingranaggio che apre le impostazioni per la modalità ECO, 
in alto a destra un pulsante per aprire le impostazioni degli orari di accensione e spegnimento per la modalità AUTO e 
PRERISCALDAMENTO, al centro a sinistra c’è la temperatura del vostro sensore mentre a destra la temperatura impostata che 
potete modificare con le 2 frecce che sono posizionate sopra e sotto; affianco sulla destra viene indicato se al momento 
il termostato è acceso o spento; in basso ci sono le 5 modalità di funzionamento; la modalità selezionata sarà evidenziata
in giallo.<br>In alto a sinistra c'è un'icona messaggio per attivare e disattivare le notifiche; quando è gialla è attivo il servizio.<br><br>
<p align="center"/> <b>Modalità di funzionamento</b><br> </p>
Il termostato, è configurato per funzionare in 5 modalità:<br>

OFF: termostato spento.<br>

MANUALE:  termostato acceso, non tiene conto di orari e posizione.<br>

AUTO:  il termostato si accende solo se si è a casa e se l’ora è tra gli intervalli di tempo impostati.<br>

PRE: il termostato si accende all’ora impostata anche se si è fuori casa.<br>

ECO:  imposta una temperatura più bassa, ideale per la notte o se si vuole lasciare una temperatura più bassa quando non 
si è a casa.<br><br>

Quando è acceso il termostato, in qualsiasi modalità tranne la OFF, resterà acceso fino a quando non arriverà alla temperatura 
impostata e si riaccenderà se la temperatura si riabbasserà. <br>
La modalità ECO si attiva automaticamente all’ora impostata per poi ritornare alla modalità precedente e alla temperatura 
precedente una volta che arriva all’ora impostata per lo spegnimento della modalità ECO. È possibile anche attivarla 
manualmente cliccando sul bottone ECO. Per disattivarla basta scegliere una modalità diversa e ritornerà anche la 
temperatura impostata precedentemente.<br>
<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/eco.png"> </p>
Dalla pagina iniziale, cliccando sull’ingranaggio in alto a sinistra, si aprirà il menù impostazioni modalità eco.<br>
Qui potete inserire l’orario di accensione e spegnimento della modalità e la temperatura da impostare quando si attiverà 
tale modalità. <br>
Cliccando sulla freccia in alto a destra si tornerà alla pagina iniziale.<br><br>
<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/accensione_spegnimento.png"> </p>
Dalla pagina iniziale, cliccando sull’icona  in alto a destra, si aprirà il menù impostazioni per l’accensione in 
modalita AUTO e PRERISCALDAMENTO.<br>
Qui potrete impostare l’orario di accensione e spegnimento del termostato.<br>
Cliccando sulla freccia in alto a destra si tornerà alla pagina iniziale.<br>

Per qualsiasi problema scrivete sul <a href="https://forum.hassiohelp.eu/showthread.php?tid=503">forum.</a><br>
<a href="https://www.buymeacoffee.com/mariocandida80"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee">
