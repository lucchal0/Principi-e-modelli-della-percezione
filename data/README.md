# Dataset

## Fonte

[Spotify Tracks Dataset – Kaggle](https://www.kaggle.com/datasets/saichaitanyareddyai/spotify-tracks-dataset-audio-features)

# Cosa abbiamo capito e scoperto nella parte 4

## 4.1.1 – Numero di brani per genere

Il dataset inizialmente conteneva 114.000 righe. Dopo aver eliminato 450 copie duplicate, siamo arrivati a 113.550 righe.

Abbiamo individuato 89.741 brani distinti, suddivisi in:

- 73.442 brani associati a un solo genere.
- 16.299 brani associati a più generi.
- 114 generi musicali complessivi.

Circa il 18,2% dei brani distinti compare associato a più generi.

Questo ci fa capire che le etichette musicali non sono sempre separate nettamente. Uno stesso brano può essere associato a generi differenti, pur mantenendo lo stesso `track_id`.

Abbiamo quindi eliminato le copie duplicate senza eliminare le associazioni valide tra brani e generi.

## 4.1.2 – Distribuzione delle caratteristiche musicali

Abbiamo realizzato nove istogrammi, uno per ciascuna caratteristica audio, considerando 89.741 brani distinti.

Dai grafici notiamo che:

- **Danceability:** molti brani hanno valori medio-alti, soprattutto tra 0,5 e 0,75.
- **Energy:** la distribuzione tende a concentrarsi maggiormente sui valori medio-alti e alti.
- **Valence:** i valori sono distribuiti su un intervallo abbastanza ampio.
- **Acousticness:** molti brani hanno valori vicini a zero, ma sono presenti anche valori più elevati.
- **Instrumentalness:** la maggior parte dei brani presenta valori vicini a zero; esiste anche un gruppo più piccolo con valori elevati.
- **Speechiness:** la maggior parte dei brani ha valori bassi, soprattutto nella parte iniziale della distribuzione.
- **Tempo:** molti brani si concentrano approssimativamente tra 80 e 150 BPM, con un picco intorno a 120 BPM.
- **Loudness:** la maggior parte dei valori si concentra approssimativamente tra -15 e -5 dB.
- **Liveness:** molti brani presentano valori bassi, soprattutto intorno a 0,1-0,2.

Le caratteristiche non sono distribuite tutte nello stesso modo. Alcune sono molto concentrate in determinati intervalli, mentre altre presentano distribuzioni più ampie.

Questa analisi è utile perché ci permette di conoscere meglio le variabili che utilizzeremo successivamente per il clustering.

## 4.1.3 – Correlazione tra le caratteristiche musicali

Abbiamo realizzato una Correlation Heatmap utilizzando le nove caratteristiche audio e 89.741 brani distinti.

Abbiamo individuato alcune correlazioni particolarmente evidenti:

- **Energy ↔ Loudness: +0,76**

  Correlazione positiva: i brani con maggiore energia tendono ad avere anche valori di loudness più elevati.

- **Energy ↔ Acousticness: -0,73**

  Correlazione negativa: i brani più energici tendono ad avere valori di acousticness inferiori.

- **Acousticness ↔ Loudness: -0,58**

  I valori più alti di acousticness tendono ad associarsi a valori di loudness più bassi.

- **Danceability ↔ Valence: +0,49**

  I brani più adatti al ballo tendono moderatamente ad avere anche valori di valence più elevati.

Abbiamo quindi capito che alcune caratteristiche musicali tendono a variare insieme, mentre altre presentano relazioni più deboli.

È importante ricordare che la correlazione non dimostra un rapporto di causa-effetto.

## 4.1.4 – Differenze delle caratteristiche musicali tra generi

In questa sezione confrontiamo direttamente i generi musicali.

Abbiamo realizzato:

- 9 Box Plot, uno per ogni caratteristica audio.
- Una Clustered Heatmap per confrontare i profili musicali dei 114 generi.

Dai Box Plot possiamo osservare che alcuni generi presentano mediane differenti. Un aspetto importante è che le distribuzioni di molti generi si sovrappongono.

Questo significa che non possiamo distinguere sempre un genere musicale da un altro osservando una sola caratteristica.

La Clustered Heatmap aggiunge un'altra informazione: utilizza il clustering gerarchico per raggruppare i generi che presentano profili audio simili, considerando contemporaneamente tutte e nove le caratteristiche.

In particolare, confronta le mediane delle caratteristiche standardizzate per ciascun genere e utilizza il metodo Ward con distanza euclidea per individuare gruppi di generi simili.

## 4.1.5 – Raggruppamento dei generi musicali in famiglie

Dopo aver confrontato le caratteristiche audio dei singoli generi, abbiamo approfondito le somiglianze tra i 114 generi musicali, cercando di raggrupparli in famiglie sulla base dei loro profili audio.

Per farlo, abbiamo calcolato il valore mediano delle nove caratteristiche musicali per ciascun genere, ottenendo un profilo audio rappresentativo di ogni categoria.

Successivamente abbiamo:

- Standardizzato i profili audio dei generi, in modo da rendere confrontabili le diverse caratteristiche.
- Applicato un clustering gerarchico agglomerativo, utilizzando il metodo Ward e la distanza euclidea.
- Provato diverse configurazioni, considerando un numero di famiglie da 2 a 20.
- Confrontato i risultati attraverso tre indicatori: Silhouette Score, Calinski-Harabasz Index e Davies-Bouldin Index.

Dal confronto degli indicatori abbiamo osservato che:

- **K = 3:** ottiene il risultato migliore secondo Silhouette Score (0,5382) e Davies-Bouldin Index (0,4140), indicando gruppi relativamente più compatti e separati.
- **K = 10:** permette una suddivisione più dettagliata dei generi e ottiene un Calinski-Harabasz Index più alto rispetto a K = 3 (41,9828 contro 32,8985).

Gli indicatori, quindi, non individuano tutti la stessa soluzione. K = 3 risulta migliore secondo due misure su tre, mentre K = 10 offre una suddivisione più dettagliata.

Abbiamo inoltre analizzato la composizione delle famiglie ottenute, osservando quali generi appartengono a ciascun gruppo e individuando per ogni famiglia il **medoid**, cioè il genere che meglio rappresenta il gruppo in base alle distanze tra i profili audio.

Questa analisi ci permette di osservare che alcuni generi presentano caratteristiche musicali simili e possono essere raggruppati, anche quando hanno etichette originali differenti.

È importante precisare che queste famiglie rappresentano gruppi costruiti sulla base delle caratteristiche audio e non nuove classificazioni ufficiali dei generi musicali.

## Considerazioni complessive

I generi musicali presentano alcune differenze nelle caratteristiche audio, ma queste differenze non sono sempre nette e le distribuzioni spesso si sovrappongono.

Abbiamo inoltre osservato che alcune caratteristiche musicali sono fortemente correlate tra loro e che alcuni generi, pur avendo etichette differenti, presentano profili audio simili.

Il raggruppamento gerarchico dei generi ci ha permesso di approfondire queste somiglianze, individuando possibili famiglie musicali.

Queste analisi preliminari ci forniscono una base per la fase successiva, nella quale applicheremo K-Means ai singoli brani, senza utilizzare il genere musicale come variabile di ingresso. In questo modo potremo verificare se i gruppi individuati automaticamente attraverso le caratteristiche audio presentano corrispondenze con i generi originali del dataset.
