
# 4. Grafici da utilizzare

I grafici sono suddivisi in due categorie:

- **PRINCIPALE:** grafico da realizzare perché contribuisce direttamente al raggiungimento dell'obiettivo della ricerca.
- **FACOLTATIVO:** grafico utile come approfondimento, ma non indispensabile.

## Conoscere e analizzare il dataset

### 1. Numero di brani per genere — PRINCIPALE

- **Tipo di grafico:** Bar Chart orizzontale.
- **Dati da utilizzare:** `track_genre`, numero di brani per ciascun genere.

- **Obiettivo:**
  - Capire quanti brani sono presenti per ogni genere.
  - Individuare i generi con pochi o molti brani.
  - Verificare se la distribuzione dei generi è equilibrata.

- **Motivo per realizzare il grafico:**
  - Permette di conoscere la composizione del dataset prima di iniziare l'analisi.
  - Aiuta a individuare eventuali squilibri nella distribuzione dei generi, che potrebbero influenzare le analisi successive.

- **Perché utilizzare questo tipo di grafico:**
  - Il Bar Chart è adatto a confrontare quantità appartenenti a categorie differenti.
  - L'orientamento orizzontale permette di visualizzare facilmente i nomi dei generi musicali, anche quando sono lunghi.
  - Ordinando le barre dalla più lunga alla più corta è immediato individuare i generi più e meno rappresentati.

### 2. Distribuzione delle caratteristiche musicali — PRINCIPALE

- **Tipo di grafico:** Istogrammi (possibilmente organizzati in Small Multiples).

- **Dati da utilizzare:**
  - `danceability`
  - `energy`
  - `valence`
  - `acousticness`
  - `instrumentalness`
  - `speechiness`
  - `tempo`
  - `loudness`

- **Obiettivo:**
  - Osservare come sono distribuite le caratteristiche musicali.
  - Capire quali valori sono più frequenti.
  - Individuare eventuali distribuzioni asimmetriche e valori estremi.

- **Motivo per realizzare il grafico:**
  - Permette di comprendere la distribuzione delle variabili che utilizzeremo per il clustering.
  - Aiuta a individuare caratteristiche con distribuzioni particolari o valori anomali, che potrebbero influenzare l'analisi.

- **Perché utilizzare questo tipo di grafico:**
  - L'istogramma permette di visualizzare la distribuzione di una variabile numerica.
  - Consente di capire quali intervalli di valori sono più frequenti e se la distribuzione è simmetrica oppure asimmetrica.
  - Utilizzando Small Multiples possiamo confrontare le distribuzioni delle otto caratteristiche attraverso grafici separati, senza sovraccaricare un'unica visualizzazione.

### 3. Correlazione tra le caratteristiche musicali — PRINCIPALE

- **Tipo di grafico:** Correlation Heatmap.
- **Dati da utilizzare:** le stesse otto caratteristiche musicali del grafico 2.

- **Obiettivo:**
  - Individuare le caratteristiche che tendono a variare insieme.
  - Individuare eventuali correlazioni positive o negative.
  - Capire se alcune variabili descrivono aspetti musicali simili.

- **Motivo per realizzare il grafico:**
  - Permette di comprendere le relazioni tra le variabili utilizzate nel clustering.
  - Aiuta a individuare eventuali correlazioni molto forti tra caratteristiche musicali.

- **Perché utilizzare questo tipo di grafico:**
  - La Heatmap utilizza colori differenti per rappresentare l'intensità e la direzione delle correlazioni.
  - Permette di confrontare rapidamente tutte le coppie di caratteristiche musicali.
  - È particolarmente utile quando si hanno diverse variabili, perché una tabella numerica sarebbe meno immediata da interpretare.

### 4. Differenze delle caratteristiche musicali tra generi — FACOLTATIVO

- **Tipo di grafico:** Box Plot.
- **Dati da utilizzare:**
  - `track_genre`
  - Un sottoinsieme delle otto caratteristiche musicali.

- **Obiettivo:**
  - Confrontare le caratteristiche musicali tra generi.
  - Osservare mediane, dispersione e valori estremi.
  - Capire se alcuni generi presentano caratteristiche simili o differenti.

- **Motivo per realizzare il grafico:**
  - Permette di effettuare un primo confronto tra le caratteristiche acustiche dei generi originali.
  - Aiuta a capire se esistono differenze misurabili tra le categorie prima di applicare il clustering.
  - È un approfondimento utile, ma alcune informazioni verranno riprese nel confronto finale tra cluster e generi.

- **Perché utilizzare questo tipo di grafico:**
  - Il Box Plot riassume la distribuzione di una variabile numerica attraverso mediana, quartili e valori anomali.
  - Permette di confrontare contemporaneamente la distribuzione di una caratteristica tra diversi generi.
  - È utile per individuare differenze e sovrapposizioni tra le categorie.
  
---

## Clustering: trovare gruppi senza conoscere il genere

### 1. Elbow Method — PRINCIPALE

- **Tipo di grafico:** Line Chart.

- **Dati da utilizzare:**
  - Le otto caratteristiche musicali standardizzate.
  - Numero di cluster `K`.
  - Inertia / WCSS calcolata da K-Means (somma dei quadrati delle distanze all'interno dei cluster).

- **Obiettivo:**
  - Provare diversi valori di `K`.
  - Osservare come diminuisce l'inerzia aumentando il numero di cluster.
  - Individuare il possibile punto di equilibrio per scegliere `K`.

- **Motivo per realizzare il grafico:**
  - Permette di individuare un possibile numero di cluster appropriato per raggruppare i brani.
  - Evita di scegliere il numero di gruppi in modo arbitrario.

- **Perché utilizzare questo tipo di grafico:**
  - Il Line Chart è adatto a mostrare come cambia una misura al variare di un parametro.
  - Permette di osservare l'andamento della WCSS quando aumenta il numero di cluster `K`.
  - Rende visibile il possibile punto di gomito, nel quale il miglioramento ottenuto aggiungendo altri cluster diventa meno significativo.

### 2. Silhouette Score — PRINCIPALE

- **Tipo di grafico:** Line Chart.

- **Dati da utilizzare:**
  - Le otto caratteristiche musicali standardizzate.
  - Diversi valori di `K`.
  - Silhouette Score calcolato per ogni valore di `K`.

- **Obiettivo:**
  - Valutare quanto i cluster sono compatti e separati tra loro.
  - Confrontare la qualità delle diverse configurazioni.
  - Affiancare questa valutazione all'Elbow Method nella scelta di `K`.

- **Motivo per realizzare il grafico:**
  - Permette di valutare se i gruppi individuati da K-Means sono effettivamente ben separati.
  - Completa l'Elbow Method, fornendo un'altra misura per scegliere il numero di cluster.

- **Perché utilizzare questo tipo di grafico:**
  - Permette di confrontare il Silhouette Score ottenuto con diversi valori di `K`.
  - La linea rende immediatamente visibili eventuali aumenti e diminuzioni della qualità del clustering.
  - Facilita l'individuazione dei valori di `K` che producono una migliore separazione tra i gruppi.

### 3. Visualizzazione dei cluster tramite PCA — PRINCIPALE

- **Tipo di grafico:** Scatter Plot.

- **Dati da utilizzare:**
  - Le otto caratteristiche musicali standardizzate.
  - Etichetta del cluster assegnata da K-Means.
  - Prime due componenti principali ottenute con PCA.

- **Obiettivo:**
  - Rappresentare visivamente i gruppi individuati.
  - Osservare se i cluster appaiono separati o sovrapposti.
  - Individuare eventuali gruppi molto vicini tra loro.

- **Motivo per realizzare il grafico:**
  - Permette di visualizzare in due dimensioni i gruppi individuati utilizzando otto caratteristiche musicali.
  - Aiuta a interpretare visivamente la distribuzione dei cluster.

- **Perché utilizzare questo tipo di grafico:**
  - Lo Scatter Plot permette di rappresentare osservazioni individuali attraverso punti in uno spazio bidimensionale.
  - Ogni punto rappresenta un brano e il colore identifica il cluster di appartenenza.
  - Consente di osservare la vicinanza tra i brani, la separazione tra i gruppi e le eventuali sovrapposizioni.
  - La PCA permette di rappresentare in due dimensioni informazioni originariamente distribuite su otto caratteristiche.

**Nota:** la PCA viene utilizzata per ridurre le dimensioni e visualizzare i dati in due dimensioni. K-Means viene applicato alle otto caratteristiche standardizzate originali, non alle sole due componenti PCA.

### 4. Profilo musicale dei cluster — PRINCIPALE

- **Tipo di grafico:** Heatmap.

- **Dati da utilizzare:**
  - Etichetta `cluster` ottenuta da K-Means.
  - Le otto caratteristiche musicali.
  - Media di ciascuna caratteristica per cluster.

- **Obiettivo:**
  - Analizzare le caratteristiche medie di ogni cluster.
  - Capire quali variabili caratterizzano maggiormente ciascun gruppo.
  - Attribuire un'interpretazione musicale ai cluster.

- **Motivo per realizzare il grafico:**
  - Permette di comprendere quali caratteristiche acustiche contraddistinguono i gruppi individuati.
  - Aiuta a interpretare musicalmente i cluster, andando oltre la semplice visualizzazione dei punti.

- **Perché utilizzare questo tipo di grafico:**
  - La Heatmap permette di confrontare contemporaneamente più caratteristiche per ciascun cluster.
  - L'utilizzo dei colori facilita l'individuazione delle caratteristiche con valori medi più alti o più bassi.
  - È particolarmente adatta a una matrice con i cluster sulle righe e le caratteristiche musicali sulle colonne.

### 5. Confronto tra cluster e generi musicali — PRINCIPALE

- **Tipo di grafico:** Heatmap.

- **Dati da utilizzare:**
  - `cluster` assegnato da K-Means.
  - `track_genre` originale.
  - Conteggi e percentuali per ogni combinazione cluster-genere.

- **Obiettivo:**
  - Confrontare i cluster individuati autonomamente con i generi originali.
  - Osservare quali generi sono presenti in ciascun cluster.
  - Individuare generi distribuiti in più cluster.
  - Individuare cluster che contengono generi differenti.
  - Verificare quanto i gruppi acustici corrispondono alle categorie di genere.

- **Motivo per realizzare il grafico:**
  - È il grafico più importante per rispondere alla domanda di ricerca.
  - Permette di verificare se i gruppi individuati attraverso le caratteristiche musicali corrispondono ai generi assegnati nel dataset oppure se generi diversi vengono raggruppati insieme.
  - Aiuta a individuare eventuali sovrapposizioni tra categorie musicali.

- **Perché utilizzare questo tipo di grafico:**
  - La Heatmap permette di rappresentare una relazione tra due variabili categoriali: cluster e genere musicale.
  - I colori evidenziano quali combinazioni cluster-genere sono più frequenti.
  - Utilizzando percentuali per riga è possibile confrontare la composizione dei cluster anche quando hanno dimensioni differenti.
  - Consente di individuare immediatamente se un cluster contiene prevalentemente un genere oppure se raccoglie brani appartenenti a generi differenti.

**Nota:** utilizzare percentuali per riga, in modo che ogni cluster mostri la propria composizione interna. Considerando la presenza di 114 generi, potrebbe essere necessario selezionare o aggregare alcune categorie secondo un criterio dichiarato, per mantenere leggibile la visualizzazione.

---

## Classificazione: verificare quanto le caratteristiche predicono il genere — FACOLTATIVA

Questa fase rappresenta un approfondimento rispetto all'obiettivo principale. A differenza del clustering, utilizza i generi originali come etichette da prevedere.

### 1. Decision Tree — FACOLTATIVO

- **Tipo di grafico:** Decision Tree.

- **Dati da utilizzare:**
  - Input: le otto caratteristiche musicali.
  - Target: `track_genre`.

- **Obiettivo:**
  - Costruire un modello che provi a prevedere il genere.
  - Osservare quali caratteristiche vengono utilizzate nelle decisioni.
  - Comprendere le regole di classificazione.

- **Motivo per realizzare il grafico:**
  - Permette di verificare se le caratteristiche musicali possono essere utilizzate per riconoscere e prevedere i generi.
  - Offre un confronto aggiuntivo rispetto ai risultati ottenuti con il clustering.

- **Perché utilizzare questo tipo di grafico:**
  - L'albero decisionale rappresenta le regole utilizzate dal modello attraverso nodi e rami.
  - Permette di seguire il percorso delle decisioni e comprendere quali caratteristiche vengono utilizzate per classificare un brano.
  - È una visualizzazione interpretabile, utile per comprendere il funzionamento del modello.

### 2. Feature Importance — FACOLTATIVO

- **Tipo di grafico:** Bar Chart orizzontale.

- **Dati da utilizzare:**
  - Modello Random Forest.
  - Le otto caratteristiche musicali.
  - Valori di feature importance.

- **Obiettivo:**
  - Individuare le caratteristiche più utilizzate dal modello.
  - Ordinare le variabili in base alla loro importanza.
  - Capire quali proprietà musicali contribuiscono maggiormente alla previsione del genere.

- **Motivo per realizzare il grafico:**
  - Permette di capire quali caratteristiche musicali risultano più informative per il modello nella classificazione dei generi.
  - Aggiunge un'interpretazione dei risultati della classificazione.

- **Perché utilizzare questo tipo di grafico:**
  - Il grafico a barre permette di confrontare e ordinare l'importanza delle diverse caratteristiche.
  - L'orientamento orizzontale rende leggibili i nomi delle variabili.
  - Consente di individuare rapidamente quali caratteristiche risultano più informative per il modello.

### 3. Confronto Decision Tree vs Random Forest — FACOLTATIVO

- **Tipo di grafico:** Bar Chart comparativo.

- **Dati da utilizzare:**
  - Decision Tree.
  - Random Forest.
  - Accuracy calcolata sullo stesso test set.

- **Obiettivo:**
  - Confrontare le prestazioni dei due algoritmi.
  - Verificare quale riesce a prevedere meglio il genere.
  - Capire se un modello più complesso migliora i risultati.

- **Motivo per realizzare il grafico:**
  - Permette di confrontare due approcci di classificazione.
  - Aiuta a capire se Random Forest offre risultati migliori rispetto a un singolo Decision Tree.

- **Perché utilizzare questo tipo di grafico:**
  - Le barre permettono di confrontare direttamente le prestazioni dei due modelli.
  - Utilizzando la stessa scala è possibile osservare facilmente quale modello ottiene il risultato migliore.
  - È una soluzione semplice e immediata per confrontare le metriche di valutazione.

### 4. Confusion Matrix — FACOLTATIVO

- **Tipo di grafico:** Confusion Matrix / Heatmap.

- **Dati da utilizzare:**
  - Generi reali nel test set.
  - Generi previsti dal modello.
  - Risultati del Decision Tree o Random Forest.

- **Obiettivo:**
  - Osservare quali generi vengono classificati correttamente.
  - Individuare quali generi vengono confusi tra loro.
  - Analizzare eventuali somiglianze tra categorie.

- **Motivo per realizzare il grafico:**
  - Permette di approfondire gli errori commessi dal modello.
  - Aiuta a individuare quali generi sono più difficili da distinguere attraverso le caratteristiche musicali.
  - Completa l'analisi delle prestazioni dei modelli.

- **Perché utilizzare questo tipo di grafico:**
  - La Heatmap permette di rappresentare il confronto tra classi reali e classi previste.
  - I colori rendono immediatamente visibili le classificazioni corrette e gli errori.
  - Consente di individuare quali generi vengono confusi più frequentemente dal modello.