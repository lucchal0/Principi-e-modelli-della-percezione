# TODO – The Sound of Data

Legenda:
- [ ] Da fare
- [x] Completato

## Fase 1 – Definizione del progetto

- [x] Rileggere le indicazioni della docente.
- [x] Verificare nelle slide quale algoritmo è presentato come modello della percezione umana.
- [x] Definire un obiettivo preciso.

## Fase 2 – Dataset

- [x] Scaricare il CSV dalla fonte indicata in `data/README.md`.
- [x] Rilevare il numero effettivo di righe e colonne.
- [x] Documentare i tipi delle variabili e il significato delle colonne utilizzate.
- [x] Documentare la fonte e la provenienza del dataset.
- [x] Verificare eventuali limitazioni del dataset.

## Fase 3 – Analisi esplorativa (EDA)

### 3.1 Controllo della qualità dei dati

- [ ] Controllare la presenza di valori mancanti.
- [ ] Controllare la presenza di righe duplicate.
- [ ] Calcolare le statistiche descrittive delle caratteristiche audio.
- [ ] Verificare gli intervalli dei valori delle variabili.

### 3.2 Visualizzazioni esplorative

- [x] Selezionare i grafici coerenti con le domande di ricerca.
- [ ] Realizzare il Bar Chart del numero di brani per genere.
- [ ] Realizzare gli istogrammi delle otto caratteristiche audio.
- [ ] Realizzare la Correlation Heatmap delle otto caratteristiche.
- [ ] Realizzare Box Plot per confrontare le caratteristiche audio tra alcuni generi.
- [ ] Inserire titoli, etichette e didascalie nei grafici.
- [ ] Commentare i risultati e le osservazioni emerse dai grafici.

## Fase 4 – Preparazione dei dati

### 4.1 Selezione delle variabili

- [x] Definire e motivare le otto caratteristiche audio da utilizzare:
  - `danceability`
  - `energy`
  - `valence`
  - `acousticness`
  - `instrumentalness`
  - `speechiness`
  - `tempo`
  - `loudness`
- [ ] Motivare la scelta delle caratteristiche selezionate e l'esclusione delle altre variabili.
- [ ] Separare le caratteristiche utilizzate dal clustering dalle etichette e dai campi identificativi.
- [ ] Assicurarsi che `track_genre` non venga utilizzata come input di K-Means.

### 4.2 Pulizia e standardizzazione

- [ ] Decidere come gestire eventuali valori mancanti e duplicati.
- [ ] Valutare eventuali valori anomali e decidere come gestirli.
- [ ] Applicare `StandardScaler` alle otto caratteristiche selezionate.
- [ ] Conservare i dati originali per interpretare i risultati nelle unità di misura iniziali.
- [ ] Documentare le decisioni prese durante il preprocessing.

## Fase 5 – Clustering e valutazione

### 5.1 Scelta dell'algoritmo

- [ ] Spiegare l'algoritmo scelto e il collegamento con gli argomenti del corso.
- [ ] Motivare perché l'algoritmo è adatto alla domanda di ricerca.
- [ ] Descrivere brevemente i limiti dell'algoritmo.

### 5.2 Scelta del numero di cluster

- [ ] Definire un intervallo di valori di K da provare.
- [ ] Calcolare e visualizzare l'Elbow Method (WCSS/Inertia).
- [ ] Calcolare e visualizzare il Silhouette Score per diversi valori di K.
- [ ] Confrontare i risultati dei due metodi e motivare la scelta finale di K.

### 5.3 Applicazione di K-Means

- [ ] Applicare K-Means alle otto caratteristiche standardizzate.
- [ ] Impostare i parametri dell'algoritmo, ad esempio `random_state` e `n_init`.
- [ ] Assegnare a ogni brano l'etichetta del cluster.
- [ ] Registrare il numero di brani appartenenti a ciascun cluster.

### 5.4 Valutazione dei risultati

- [ ] Valutare la compattezza e la separazione dei cluster.
- [ ] Controllare le dimensioni dei cluster ed eventuali gruppi sbilanciati.
- [ ] Verificare la stabilità dei risultati con inizializzazioni differenti.

## Fase 6 – Interpretazione e visualizzazione dei risultati

### 6.1 Visualizzazione dei cluster

- [ ] Realizzare lo Scatter Plot tramite PCA, colorando i punti in base al cluster.
- [ ] Specificare che la PCA viene utilizzata per visualizzare i dati in due dimensioni, mentre K-Means viene applicato alle otto caratteristiche originali standardizzate.
- [ ] Gestire l'eventuale sovrapposizione dei punti nel grafico PCA, utilizzando trasparenza o un campione rappresentativo.
- [ ] Realizzare la Heatmap dei profili medi delle otto caratteristiche per cluster.
- [ ] Interpretare le caratteristiche musicali che contraddistinguono ciascun cluster.

### 6.2 Confronto tra cluster e generi musicali

- [ ] Confrontare i cluster ottenuti con il genere originale `track_genre`.
- [ ] Realizzare la Heatmap Cluster vs Genre con conteggi o percentuali.
- [ ] Utilizzare le percentuali per riga per osservare la composizione interna dei cluster.
- [ ] Individuare i generi distribuiti in più cluster.
- [ ] Individuare i cluster che contengono generi differenti.
- [ ] Interpretare le corrispondenze e le differenze tra caratteristiche acustiche e generi musicali.
- [ ] Valutare l'utilizzo dell'Adjusted Rand Index (ARI) per misurare la concordanza tra cluster e generi.

## Fase 7 

### 7.1 Classificazione supervisionata

- [ ] Applicare un Decision Tree per provare a prevedere il genere musicale.
- [ ] Applicare una Random Forest.
- [ ] Realizzare il grafico Feature Importance.
- [ ] Confrontare le prestazioni dei modelli.
- [ ] Realizzare una Confusion Matrix per analizzare gli errori di classificazione.

### 7.2 Ulteriori confronti

- [ ] Valutare l'applicazione di altri algoritmi di clustering, come Mean Shift.
- [ ] Confrontare i risultati di algoritmi differenti.
