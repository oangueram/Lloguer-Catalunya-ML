# 🏠 Anàlisi i Predicció del Mercat de Lloguer a Catalunya (2007–2025)

[![Obre a Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1Gp7rLmXEymNWr8Xev6oVvg3ubiLOx266)
![Python](https://img.shields.io/badge/Python-3.x-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange)
![Plotly](https://img.shields.io/badge/Plotly-interactive-teal)

Quant ha pujat el lloguer a Catalunya en gairebé vint anys, i on té sentit invertir? Aquest projecte parteix de dades reals del mercat de lloguer català (2007–2025) i les fa passar per un pipeline complet —neteja, exploració, mapatge, predicció i segmentació amb Machine Learning— per intentar respondre-hi amb dades en comptes d'intuïció.

## Què fa

- **Neteja les dades** — normalitza el format numèric de la renda i elimina outliers per any i municipi (mètode IQR), per no confondre inflació amb pujades reals ni municipis bombolla amb outliers.
- **Explora el mercat** — distribució de preus, rànquings de creixement (anual i històric) i de volatilitat per municipi.
- **Mapeja Catalunya** — un mapa interactiu que mostra l'efecte "taca d'oli" de Barcelona sobre els preus dels municipis veïns.
- **Prediu preus a Barcelona** — compara models polinòmics amb validació temporal (`TimeSeriesSplit`) i els millora amb *lag features* per captar la tendència recent.
- **Busca oportunitats d'inversió** — segmenta tots els municipis amb K-Means (preu, creixement, volum de contractes) i aplica un Isolation Forest per descartar els més anòmals.

## Dades

Es carreguen automàticament per URL des d'aquest mateix repositori:
- `ambits_trimestral_lloguer.csv` — preus de lloguer per municipi
- `municipis.zip` — geometries GeoJSON dels municipis catalans, per al mapa

## Com executar-ho

La manera més ràpida és obrir-lo directament a Colab (botó de dalt).

## Conclusions principals

- La regressió lineal és el model més sòlid a curt termini — els polinomis de grau alt pateixen d'overfitting. Els *lag features* en redueixen l'error, però a llarg termini l'error es va acumulant de manera exponencial.
- El K-Means aïlla un segment de municipis amb preus d'entrada baixos i creixement històric fort: la millor oportunitat detectada, tot i tenir menys volum de mercat.
- L'Isolation Forest descarta molt pocs municipis d'aquest segment, cosa que confirma que la segmentació ja havia deixat fora la majoria de mercats inestables.

## Propers passos

- Incorporar variables macroeconòmiques (Euríbor, IPC) i provar models més complexos per reduir l'error de predicció.
- Entrenar un Isolation Forest local, només dins el segment emergent, per detectar sobrevaloracions relatives entre municipis similars.

## 🤖 Desenvolupament Assistit per IA

Aquest projecte s'ha construït integrant eines de models de llenguatge avançats (LLMs) per accelerar el cicle de creació i mantenir el codi net. L'ús de la IA s'ha centrat estratègicament en:

- **Refactorització i Depuració (Debugging):** Diagnòstic de codi i resolució d'errors.
- **Generació de Codi Estructural:** Creació de blocs estàndard.
- **Cerca de sintaxi:** Ús de la IA com a diccionari avançat de Python per materialitzar en codi les decisions analítiques i metodològiques preses per l'autor.
- **Documentació i Format:** Estructuració d'aquest `README.md` i suport en la redacció de comentaris.

> **Nota d'auditoria:** Tot i l'assistència en la picada de codi, **les decisions estructurals i de negoci**  són íntegrament d'autoria humana. Tota la feina assistida per IA ha estat revisada i validada manualment.
---

**Autor:** [Oriol Anguera Milà](https://github.com/oangueram)
