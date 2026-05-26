<p align="center">
  <img src="https://img.shields.io/badge/LaTeX-47A141?style=for-the-badge&logo=latex&logoColor=white"/>
  <img src="https://img.shields.io/badge/Biber-008080?style=for-the-badge&logo=tex&logoColor=white"/>
  <img src="https://img.shields.io/badge/PDF-FF0000?style=for-the-badge&logo=adobeacrobatreader&logoColor=white"/>
</p>

# 🎓 Tesi triennale — Steganografia generativa su immagini

**👤 Autore:** Matteo Diciotti
**👨‍🏫 Relatore:** Prof. Daniele Baracchi
**👩‍🔬 Correlatrice e correlatore:** PhD Giulia Bertazzini, Prof. Daniele Castellana
**📚 Corso di Laurea:** Informatica, Università di Firenze
**📅 Anno Accademico:** 2025/2026

---

📂 La presente repository contiene i file sorgenti **LaTeX** della mia tesi triennale, dal titolo:

> **"Steganografia generativa su immagini: adattamento del protocollo Meteor tramite l'architettura VQ-GAN"**
> (English title: *Generative Image Steganography: Adapting the Meteor Protocol to the VQ-GAN Architecture*)

## Abstract

La crittografia tradizionale, sebbene efficace nel proteggere la *confidenzialità* del contenuto dei messaggi, presenta una vulnerabilità intrinseca e spesso trascurata: la **visibilità del traffico cifrato**. L'elevata entropia e le firme statistiche distintive dei dati crittografati li rendono facilmente individuabili da sistemi di sorveglianza di massa e filtraggio di rete (firewall avanzati, DPI, *deep packet inspection*), consentendo a regimi autoritari o entità ostili di bloccare selettivamente le comunicazioni protette. In scenari operativi caratterizzati da censura estrema, la sola crittografia non è dunque sufficiente a garantire la libertà di comunicazione.

La **steganografia** si propone come disciplina complementare: il suo obiettivo non è nascondere il *significato* del messaggio (compito della crittografia), bensì nasconderne la *presenza stessa*. Un sistema steganografico cerca di rendere un *stego-object* (contenente il messaggio segreto) statisticamente indistinguibile da un innocuo *cover object* privo di informazioni nascoste. Le tecniche classiche (quali la manipolazione dei bit meno significativi — LSB — nelle immagini) si sono tuttavia dimostrate vulnerabili ad attacchi di crittoanalisi statistica sempre più sofisticati.

La ricerca più recente ha quindi abbracciato un cambio di paradigma, sfruttando le **capacità generative dei modelli di deep learning** per incorporare il messaggio segreto *durante* la fase di generazione stessa del contenuto, anziché modificare un contenuto preesistente. In questo contesto si inserisce **Meteor**, un innovativo algoritmo di steganografia a chiave simmetrica che utilizza modelli linguistici di grandi dimensioni (LLM, inizialmente GPT-2) per pilotare il campionamento dei token testuali in funzione del messaggio segreto cifrato, garantendo che il testo generato sia statisticamente indistinguibile dall'output naturale del modello.

Il lavoro di questa tesi estende il principio fondamentale di Meteor dal dominio testuale a quello delle **immagini digitali ad alta risoluzione**, definendo un nuovo modello denominato **SwE** (*Steganography without Embeddment*). Per conseguire questo obiettivo viene utilizzata l'architettura **VQ-GAN** (*Vector Quantized Generative Adversarial Network*), che consente di modellare immagini complesse attraverso un vocabolario discreto di "token visivi" memorizzati in un *codebook*. Questa rappresentazione discreta permette di applicare un modello Transformer autoregressivo per guidare la sintesi dell'immagine e, parallelamente, incorporare il messaggio cifrato direttamente nel flusso generativo, senza richiedere l'addestramento di un nuovo modello né modificare la distribuzione di probabilità appresa.

L'obiettivo finale è duplice: da un lato, ottenere immagini visivamente realistiche e indistinguibili da quelle prodotte dal modello generativo originale; dall'altro, garantire una robustezza elevata contro tentativi di rilevamento steganografico, validata attraverso metriche quantitative come la *Fréchet Inception Distance* (FID) e specifici test di indistinguibilità statistica. I risultati sperimentali, discussi nella parte finale dell'elaborato, dimostrano l'efficacia dell'approccio proposto e ne delineano i possibili sviluppi futuri, con implicazioni significative per la costruzione di strumenti di comunicazione *censorship-resistant*.

## 📁 Struttura del repository

| 🗂 File/Directory     | 📄 Descrizione                                              |
|-----------------------|-------------------------------------------------------------|
| `Thesis.tex`          | 📜 File principale della tesi                               |
| `Chapters/`           | 📖 Capitoli (Introduzione, Stato dell'arte, Definizioni, Evaluation, Conclusioni) |
| `FrontMatter/`        | 🏷 Frontespizio                                             |
| `Figures/`            | 🖼 Figure e diagrammi                                       |
| `Bibliography.bib`    | 📚 Database bibliografico                                   |
| `classicthesis.sty`   | 🎨 Stile ClassicThesis                                      |
| `logo/`               | 🏛 Logo dell'Università di Firenze                          |

## 🛠 Compilazione

Per compilare la tesi è necessario un sistema **LaTeX** aggiornato. Una volta clonata la repository, eseguire:

```bash
pdflatex Thesis.tex
biber Thesis
pdflatex Thesis.tex
pdflatex Thesis.tex
```

🔄 In alternativa, è possibile utilizzare un editor LaTeX con supporto `biber` (es. TeXstudio, Overleaf).
