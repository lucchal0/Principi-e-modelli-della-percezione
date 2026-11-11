# The Sound of Data

Progetto di gruppo per l'esame di **Principi e modelli della percezione**.

## Obiettivo

Analizzare un dataset di tracce musicali Spotify attraverso visualizzazioni e un algoritmo studiato durante il corso, con particolare attenzione al collegamento tra algoritmo e modello della percezione umana richiesto dalla docente.

> **Scelta metodologica ancora da verificare:** prima di fissare l'algoritmo principale, controllare le slide del corso e identificare il metodo esplicitamente presentato come modello della percezione umana. K-means e Mean Shift non vanno considerati intercambiabili né scelti solo perché disponibili nel materiale.

## Dataset

Dataset di partenza: [Spotify Tracks Dataset – Kaggle](https://www.kaggle.com/datasets/saichaitanyareddyai/spotify-tracks-dataset-audio-features).

Il file CSV non viene incluso automaticamente nel repository. Consultare [data/README.md](data/README.md) per le istruzioni. Verificare licenza e condizioni d'uso prima di pubblicare o redistribuire i dati.

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

## Come iniziare

1. Leggere e aggiornare [TODO.md](TODO.md).
2. Verificare sulle slide l'algoritmo centrale richiesto.
3. Scaricare il dataset seguendo le istruzioni in `data/README.md`.
4. Aprire `notebooks/sound_of_data.ipynb` e seguire le sezioni nell'ordine.
5. Salvare i grafici finali in `figures/grafici/`.
6. Inserire la presentazione definitiva in `presentation/The_Sound_of_Data.pptx`.

## Notebook

Il notebook è organizzato per documentare:
- descrizione e controllo del dataset;
- pulizia e analisi esplorativa;
- selezione delle feature e valutazione della normalizzazione;
- applicazione e valutazione dell'algoritmo scelto;
- interpretazione dei risultati e conclusioni.

## Uso dell'AI generativa

Il gruppo documenterà nella presentazione come sono stati usati strumenti di AI generativa, quali attività hanno supportato, quali limiti/errori sono emersi e come le risposte sono state verificate.

## Consegna

La consegna richiesta dalla docente comprende codice e presentazione PPTX in una repository GitHub pubblica. Inserire il link della repository nel file Excel richiesto per l'esame. Prima della consegna verificare che la repository sia pubblica e che il notebook sia eseguibile dall'inizio alla fine.
