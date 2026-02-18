# 🏎️ F1 Strategy Dashboard - Predicția Timpilor pe Tur

[cite_start]Aplicația dezvoltată are ca scop optimizarea strategiilor de cursă în Formula 1 prin estimarea precisă a timpilor pe tur[cite: 3]. [cite_start]Problema este modelată ca o sarcină de învățare supervizată de tip regresie, unde modelul învață să prezică o valoare continuă pe baza condițiilor de cursă[cite: 4].

## 📊 Setul de Date
* [cite_start]S-au utilizat date de telemetrie și cronometrare din sezonul 2024 de Formula 1[cite: 5].
* [cite_start]Datele brute sunt structurate în fișiere CSV per sesiune, conținând informații detaliate despre fiecare tur efectuat de piloți[cite: 5].
* [cite_start]Variabila prezisă este TimeSec (timpul pe tur convertit în secunde)[cite: 6].
* [cite_start]Variabilele de intrare sunt: Circuitul, Pilotul, Numărul turului, Tipul pneului, Uzura pneului, Temperaturile, Umiditatea și nivelul de combustibil[cite: 7].

## ⚙️ Preprocesarea Datelor
* [cite_start]Au fost eliminate tururile de ieșire de la boxe și tururile de intrare la boxe[cite: 10].
* [cite_start]S-a folosit metoda intervalului interquartilic (IQR) pentru a elimina tururile anomalice, păstrând doar timpii relevanți statistic[cite: 11].
* [cite_start]Datele meteorologice lipsă au fost completate cu medii standard[cite: 12].
* [cite_start]Variabilele categorice au fost transformate în valori numerice folosind LabelEncoder[cite: 13].

## 🧠 Modele de Machine Learning
* [cite_start]HistGradientBoostingRegressor (HGBR): Model principal, optimizat cu constrângeri monotonice pentru a respecta fizica uzurii pneurilor[cite: 16].
* [cite_start]RandomForestRegressor: Model secundar, folosit pentru validare încrucișată și robustețe[cite: 17].

## 📈 Rezultate și Performanță
* [cite_start]În condiții normale de cursă, diferența dintre predicție și realitate este frecvent sub 0.1 - 0.2 secunde[cite: 30].
* [cite_start]Distribuția punctelor arată o liniaritate puternică, acestea grupându-se strâns în jurul diagonalei ideale[cite: 24].
* [cite_start]Aceasta demonstrează că modelul are o eroare mică și constantă[cite: 25].
* [cite_start]Când diferența dintre predicție și realitate este mare, modelul funcționează ca un detector de anomalii[cite: 31].
* [cite_start]Modelul HistGradientBoosting s-a dovedit superior în captarea nuanțelor fine (degradarea pneurilor)[cite: 33].
