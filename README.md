<p align="center">
  <a href="https://www.latex-project.org/"><img src="https://img.shields.io/badge/LaTeX-47A141?style=for-the-badge&logo=latex&logoColor=white"/></a>
  <a href="https://github.com/plk/biber"><img src="https://img.shields.io/badge/Biber-008080?style=for-the-badge&logo=tex&logoColor=white"/></a>
  <a href="https://github.com/dichohnf/tesi_triennale_latex/blob/main/Thesis/DiciottiMatteo.pdf"><img src="https://img.shields.io/badge/PDF-FF0000?style=for-the-badge&logo=adobeacrobatreader&logoColor=white"/></a>
</p>

# 🎓 Tesi triennale — Confronto di tecniche di steganografia tramite modelli generativi

**👤 Autore:** Matteo Diciotti  
**👨‍🏫 Relatore:** Prof. Daniele Baracchi  
**👩‍🔬 Correlatrice e correlatore:** Dott.ssa Giulia Bertazzini, Prof. Daniele Castellana  
**📚 Corso di Laurea:** Informatica, Università di Firenze  
**📅 Anno Accademico:** 2025/2026

---

📂 La presente repository contiene la tesi triennale, il riassunto e la presentazione finale, in formato PDF e con i relativi sorgenti LaTeX. Il titolo completo è:

> **"Confronto di tecniche di steganografia tramite modelli generativi"**
> (English title: *Comparing of steganography techniques using generative models*)

## Abstract

La steganografia occulta l'esistenza di una comunicazione dentro oggetti multimediali innocui. Mentre la crittografia produce traffico cifrato identificabile, la steganografia mira all'indistinguibilità statistica del flusso comunicativo. Un paradigma recente è la *Steganography without Embedding* (SwE), in cui il messaggio segreto guida la generazione di un nuovo artefatto invece di essere nascosto in un contenuto preesistente. L'esempio principale è **Meteor**, un algoritmo a chiave simmetrica che sfrutta un Large Language Model per pilotare i token testuali via arithmetic coding, producendo stego-text indistinguibile dall'output del modello.

Questa tesi indaga se un approccio analogo a Meteor sia applicabile al dominio visivo. L'obiettivo non è un sistema pronto all'uso, ma esplorare le condizioni in cui un modello generativo visuale può fungere da sampler steganografico, individuando i fattori che lo rendono possibile o lo limitano.

Il percorso sperimentale parte da **VQ-GAN**, che abbina un codebook discreto di token visivi a un Transformer autoregressivo. L'implementazione mostra che encoder e decoder non sono funzioni inverse: circa il 19% dei token non sopravvive al round-trip attraverso i pixel, impedendo il recupero del messaggio. Con **Open-MAGVIT2**, basato sulla *Lookup-Free Quantization* (LFQ), emerge un secondo problema: sebbene la LFQ sia matematicamente invertibile, il canale PNG introduce errori che si propagano a cascata nel campionamento autoregressivo, portando il bit error rate end-to-end a circa il 65%.

Per aggirare la propagazione si adotta una strategia alternativa: i bit del messaggio sono scritti direttamente nei piani di bit dei codici latenti tramite *Quantization Index Modulation* (QIM), con codici Reed-Solomon per la correzione degli errori. Questa soluzione consente il recupero completo del messaggio (30–50 byte per immagini 256×256 px), ma rappresenta un watermark robusto e statisticamente rilevabile, non steganografia indistinguibile.

Il risultato centrale è un trade-off tra indistinguibilità statistica (campionamento autoregressivo) e robustezza al canale (modulazione diretta dei codici): le due proprietà sono mutuamente esclusive per questo tipo di sistemi. La trasposizione di SwE al dominio visivo è concettualmente possibile ma ostacolata dall'assenza di un canale privo di rumore tra token e pixel, proprietà di cui il dominio testuale gode intrinsecamente.

## 📁 Struttura del repository

| 🗂 Directory/File                  | 📄 Descrizione                                                          |
|-----------------------------------|-------------------------------------------------------------------------|
| `Thesis/`                         | 📜 Tesi completa (PDF + sorgenti LaTeX)                                |
| `Thesis/DiciottiMatteo.pdf`       | PDF della tesi                                                          |
| `Thesis/DiciottiMatteo.tex`       | File principale LaTeX                                                   |
| `Thesis/Chapters/`                | 📖 Capitoli (Introduzione, Fondamenti, Sperimentazione, Conclusioni)    |
| `Thesis/FrontMatter/`             | 🏷 Frontespizio                                                         |
| `Thesis/Figures/`                 | 🖼 Figure e diagrammi                                                   |
| `Thesis/Bibliography.bib`         | 📚 Database bibliografico                                               |
| `Thesis/classicthesis.sty`        | 🎨 Stile ClassicThesis                                                  |
| `Thesis/logo/`                    | 🏛 Logo dell'Università di Firenze                                     |
| `Thesis/Archive/`                 | 🗄 Versioni precedenti di alcuni capitoli                               |
| `Riassunto/`                      | 📝 Riassunto esteso della tesi (PDF + sorgente LaTeX)                  |
| `Presentazione/`                  | 🖥 Presentazione finale (PDF)                                           |

## 🛠 Compilazione

Per compilare la tesi è necessario un sistema **LaTeX** aggiornato con supporto `biber`. Una volta clonata la repository, eseguire dalla directory `Thesis/`:

```bash
cd Thesis
pdflatex DiciottiMatteo.tex
biber DiciottiMatteo
pdflatex DiciottiMatteo.tex
pdflatex DiciottiMatteo.tex
```

🔄 In alternativa, è possibile utilizzare un editor LaTeX con supporto `biber` (es. TeXstudio, Overleaf).

Per compilare il riassunto:

```bash
cd Riassunto
pdflatex DiciottiMatteo_Riassunto.tex
```
