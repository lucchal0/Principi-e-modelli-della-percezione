# The Sound of Data

Progetto di gruppo per l'esame di **Principi e modelli della percezione**.

## Obiettivo

A partire da un dataset di brani musicali estratti da Spotify, ciascuno corredato da caratteristiche sonore e musicali e associato a uno specifico genere, il progetto si propone di analizzare il modo in cui i brani possono essere organizzati e raggruppati sulla base delle loro proprietà audio.

In particolare, l'obiettivo è indagare se la suddivisione dei brani in generi musicali rispecchi una struttura riconoscibile, basata su caratteristiche musicali e acustiche misurabili, oppure se sia il risultato di un processo di categorizzazione cognitiva e percettiva operato dalla mente umana.

Attraverso l'applicazione di tecniche di clustering, si intende individuare gruppi di brani caratterizzati da proprietà sonore simili, considerando variabili come danceability, energy, valence, acousticness e tempo, senza utilizzare direttamente il genere musicale nella fase di raggruppamento.

I risultati ottenuti verranno successivamente analizzati e confrontati con i generi musicali originali, al fine di individuare eventuali corrispondenze o discrepanze tra le caratteristiche oggettive dei brani e la loro classificazione.

Il progetto mira quindi a comprendere come le caratteristiche sonore possano contribuire all'organizzazione della musica in categorie e quale relazione esista tra la struttura dei dati e i processi di percezione e categorizzazione umana.

## Dataset

Dataset di partenza: [Spotify Tracks Dataset – Kaggle](https://www.kaggle.com/datasets/saichaitanyareddyai/spotify-tracks-dataset-audio-features).


## Struttura

```text
The-Sound-of-Data/
├── README.md
├── TODO.md
├── data/
│   └── README.md
├── notebooks/
│   └── sound_of_data.ipynb
├── presentation/
│   └── The_Sound_of_Data.pptx
└── figures/
    └── grafici/
```

## Notebook

Il notebook è organizzato per documentare:
- descrizione e controllo del dataset;
- pulizia e analisi esplorativa;
- selezione delle feature e valutazione della normalizzazione;
- applicazione e valutazione dell'algoritmo scelto;
- interpretazione dei risultati e conclusioni.

## Apri il progetto su Google Colab
[![Apri in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1NvIvWFx1nuCcdTKpMl1yHLgQhNi6oF6M)
