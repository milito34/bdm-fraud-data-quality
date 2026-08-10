# Data Quality & Anomaly Detection auf Finanztransaktionsdaten

Projektarbeit im Modul **Big Data Management**, Sommersemester 2026 TU Clausthal, Wirtschaftsinformatik B.Sc.

**Autor:** Alain Zidane Momo Fofou (Matrikelnummer 602032\) **Betreuer:** M.Sc. Denis Kruschinski

---

## Inhalt des Repositories

| Datei | Beschreibung |
| :---- | :---- |
| [`BDM_Fraud_Quality.ipynb`](http://BDM_Fraud_Quality.ipynb) | Jupyter Notebook mit Profiling, Quality-Checks und Isolation Forest |
| `Fraud Detection Dataset.csv` | Verwendeter Datensatz (51.000 Transaktionen, Quelle: Kaggle) |
| `Projektbericht.pdf` | Projektbericht |
| `requirements.txt` | Benötigte Python-Pakete |

**Hinweis für den Betreuer:** Das Notebook lässt sich direkt hier auf GitHub ansehen — inklusive aller Ausgaben und Diagramme, ohne Installation. Einfach auf `BDM_Fraud_Quality.ipynb` klicken.

---

## Kurzfassung

Untersucht wird ein Datensatz mit 51.000 Finanztransaktionen anhand eines dreistufigen Quality-Konzepts:

1. **Profiling** — fehlende Werte, Duplikate, Datentypen, Ausreißer (IQR)  
2. **Quality-Checks** — fünf automatisierte Regeln  
3. **Anomalieerkennung** — Isolation Forest (unüberwacht)

### Wichtigste Ergebnisse

- Fünf Spalten mit jeweils rund 5 % fehlenden Werten (systematisch, nicht zufällig)  
- 1.000 doppelte `Transaction_ID`, 881 vollständige Zeilen-Duplikate  
- 3.060 Platzhalterwerte („Unknown Device", „Invalid Method")  
- 508 Ausreißer bei `Transaction_Amount`, Maximum rund 50.000 USD  
- Isolation Forest erkennt statistische Ausreißer zuverlässig, aber nur 5,3 % der tatsächlichen Fraud-Fälle (120 von 2.259)

**Fazit:** Statistische Anomalieerkennung eignet sich gut zum Aufdecken von Datenqualitätsproblemen, für die Betrugserkennung ist ein überwachtes Verfahren nötig.

---

## Ausführen

pip install \-r requirements.txt

jupyter notebook BDM\_Fraud\_Quality.ipynb

Danach im Notebook: **Kernel → Restart & Run All**.

Die CSV-Datei liegt im selben Ordner wie das Notebook, es sind keine Pfadanpassungen nötig. Isolation Forest verwendet `random_state = 42`, die Ergebnisse sind daher exakt reproduzierbar.

---

## Verwendete Literatur

- Liu, F. T., Ting, K. M., & Zhou, Z.-H. (2008). Isolation Forest. *ICDM 2008*, S. 413–422. [https://doi.org/10.1109/ICDM.2008.17](https://doi.org/10.1109/ICDM.2008.17)  
- Pipino, L. L., Lee, Y. W., & Wang, R. Y. (2002). Data Quality Assessment. *Communications of the ACM*, 45(4), S. 211–218. [https://doi.org/10.1145/505248.506010](https://doi.org/10.1145/505248.506010)  
- Abedjan, Z., Golab, L., & Naumann, F. (2015). Profiling Relational Data: A Survey. *The VLDB Journal*, 24(4), S. 557–581. [https://doi.org/10.1007/s00778-015-0389-y](https://doi.org/10.1007/s00778-015-0389-y)  
- Pedregosa, F., et al. (2011). Scikit-learn: Machine Learning in Python. *JMLR*, 12, S. 2825–2830.  
- Fraud Detection Dataset. Kaggle. [https://www.kaggle.com](https://www.kaggle.com)

