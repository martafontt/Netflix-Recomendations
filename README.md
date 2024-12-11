# Classificació i Recomanació de Continguts de Netflix

## Introducció
Aquest projecte aborda el desenvolupament de dos sistemes de recomanació per a continguts de Netflix, amb l'objectiu de millorar l'experiència de l'usuari. Mitjançant tècniques d'aprenentatge automàtic i anàlisi de dades, es van dissenyar i implementar dos enfocaments diferenciats:
1. Un sistema que inclou un classificador Naive Bayes per predir gèneres de pel·lícules.
2. Un sistema que utilitza directament els gèneres existents al dataset.

Aquest README explica els passos seguits, les decisions preses i les eines utilitzades en el desenvolupament del projecte.

---

## Continguts del Projecte
- *Informe del projecte:* Document PDF que resumeix el treball realitzat.
- *Notebook Jupyter:* Inclou tot el codi necessari per replicar els experiments i els resultats obtinguts.

---

## Conjunt de Dades
El projecte fa servir el dataset netflix_titles disponible a Kaggle. Les característiques més rellevants són:
- show_id, type, title, director, cast, country, date_added, release_year, rating, duration, listed_in, i description.

### Tractament de les Dades
1. *Eliminació d'atributs no rellevants:*
   - Es van descartar show_id i date_added.
2. *Gestí de valors nuls:*
   - Es van aplicar tècniques com la imputació KNN i la substitució pel mode o el valor real.
3. *Codificació de dades categòriques:*
   - LabelEncoder, OneHotEncoder, i Random Category Encoding.
4. *Vectorització de text:*
   - Bag of Words i CountVectorizer amb un màxim de 20 paraules per simplificar l'anàlisi.
5. *Agrupació de gèneres:*
   - Reducció de 42 categories a 23 per optimitzar el rendiment dels models.

---

## Models Desenvolupats

### 1. Classificador Naive Bayes
- *Objectiu:* Predir els gèneres de les pel·lícules basant-se en les característiques disponibles.
- *Millores Implementades:*
  - *Feature selection:* Chi-quadrat i Mutual Information.
  - *Tractament del desbalanceig:* Tècnica SMOTE per augmentar les classes minoritàries.
  - *Optimització:* GridSearchCV amb StratifiedKFold.
- *Mètriques:* Accuracy, Precision, Recall, i F1-score.

### 2. Sistemes de Recomanació
- *Recomanador amb Classificador:*
  - Combina les prediccions del Naive Bayes amb similitud cosinus (TF-IDF).
  - Major personalització de les recomanacions.
- *Recomanador sense Classificador:*
  - Utilitza directament els gèneres del dataset.
  - Més senzill i eficient.

---

## Resultats
- *Recomanador amb Classificador:*
  - Major precisó en contextos on els gèneres estaven incomplets o incorrectes.
- *Recomanador sense Classificador:*
  - Ràpid i adequat per datasets amb gèneres ben definits.

### Exemple de Recomanacions 
- Pel·lícula d'entrada: Inception
  - Recomanador amb classificador:
    1. The Last Airbender (100.00% similitud).
    2. Shootout at Lokhandwala (11.30% similitud).
  - Recomanador sense classificador:
    1. The Bank Job (11.92% similitud).
    2. Quigley Down Under (11.75% similitud).

---

## Conclusions
- Els sistemes basats en classificadors són ideals per a una major personalització.
- Els sistemes simples, sense classificadors, són més eficients en termes de recursos.
- L'elecció del sistema depèn dels requeriments específics i la qualitat del dataset.

---

## Requisits
### Llibreries
- numpy, pandas, scikit-learn, matplotlib, seaborn, nltk

### Execució
1. Clona aquest repositori:
git clone https://github.com/martafontt/Netflix-Recomendations.git
2. Navega al directori del projecte:
cd Netflix-Recomendations
3. Executa el notebook Netflix.ipynb utilitzant Jupyter Notebook o Jupyter Lab:
jupyter notebook Netflix.ipynb
---

## Crèdits
- Nora Alquézar Presta.
- Marta Font Arimany.

---

## Referències
1. Harris, D. R., & Harris, M. (2013). Digital Design and Computer Architecture. Elsevier.
2. Manning, C. D., Raghavan, P., & Schütze, H. (2008). Introduction to Information Retrieval. Cambridge University Press.
3. Chawla, N. V., et al. (2002). SMOTE: Synthetic Minority Over-sampling Technique. Journal of Artificial Intelligence Research, 16, 321-357.
