# Dataset

## Fonte

[Spotify Tracks Dataset – Kaggle](https://www.kaggle.com/datasets/saichaitanyareddyai/spotify-tracks-dataset-audio-features)

## Cosa abbiamo capito e scoperto nella parte 4
### 4.1.1 

Il dataset non contiene soltanto brani associati a un unico genere. Circa il 18,2% dei brani distinti compare associato a più generi. Quindi fa capire che le etichette musicali non sono sempre separate nettamente. Uno stesso brano può essere associato a generi differenti.

Inoltre sono state eliminate 450 copie duplicate senza eliminare le associazioni valide tra brani e generi.

### 4.1.2
nove istogrammi, uno per ciascuna caratteristica audio, considerando 89.741 brani distinti.

notiamo che: 
Danceability -> Molti brani hanno valori medio-alti, soprattutto tra 0,5 e 0,75.
Energy -> La distribuzione è concentrata maggiormente sui valori medio-alti.
Valence -> I valori sono distribuiti su un intervallo abbastanza ampio.
Acousticness -> Molti brani hanno valori vicini a zero, ma sono presenti anche valori più elevati.
Instrumentalness -> La maggior parte dei brani presenta valori vicini a zero; esiste anche un gruppo più piccolo con valori elevati.
Speechiness -> La maggior parte dei brani ha valori bassi, con una distribuzione concentrata nella parte iniziale.
Tempo -> Molti brani si concentrano approssimativamente tra 80 e 150 BPM, con un picco intorno a 120 BPM.
Loudness -> La maggior parte dei valori si concentra approssimativamente tra -15 e -5 dB.
Liveness -> Molti brani presentano valori bassi, soprattutto intorno a 0,1-0,2.

Le caratteristiche non sono distribuite tutte nello stesso modo e alcune caratteristiche sono molto concentrate in determinati intervalli, mentre altre presentano distribuzioni più ampie.

Un'informazione utile perché ci permette di conoscere le variabili che utilizzeremo successivamente per il clustering.


### 4.1.3
realizzato la Correlation Heatmap utilizzando le nove caratteristiche e 89.741 brani distinti.

abbiamo individuato alcune correlazioni significative: 

Energy ↔ Loudness +0,76
Correlazione positiva: i brani con maggiore energia tendono ad avere anche valori di loudness più elevati.

Energy ↔ Acousticness -0,73
Correlazione negativa: i brani più energici tendono ad avere valori di acousticness inferiori.

Acousticness ↔ Loudness -0,58
I valori più alti di acousticness tendono ad associarsi a valori di loudness più bassi.

Danceability ↔ Valence +0,49
I brani più adatti al ballo tendono moderatamente ad avere anche valori di valence più elevati.

Alcune caratteristiche musicali tendono a variare insieme, mentre altre presentano relazioni più deboli. La correlazione non dimostra un rapporto di causa-effetto.


### 4.1.4
onfrontiamo direttamente i generi.

Abbiamo realizzato:
9 Box Plot, uno per ogni caratteristica.
Una Clustered Heatmap per confrontare i profili musicali dei 114 generi.

possiamo osservare che alcuni generi presentano mediane differenti. Un aspetto importante le distribuzioni di molti generi si sovrappongono. 

Questo significa che non possiamo distinguere sempre un genere musicale da un altro osservando una sola caratteristica.
La Clustered Heatmap aggiunge un'altra informazione: utilizza il clustering gerarchico per raggruppare i generi che presentano profili audio simili, considerando contemporaneamente tutte e nove le caratteristiche.

## complessivamente 
I generi musicali presentano alcune differenze nelle caratteristiche audio, ma queste differenze non sono sempre nette e le distribuzioni spesso si sovrappongono.



