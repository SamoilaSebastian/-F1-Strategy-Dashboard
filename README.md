# 🏎️ F1 Strategy Dashboard - Predicția Timpilor pe Tur

Aplicația dezvoltată are ca scop optimizarea strategiilor de cursă în Formula 1 prin estimarea precisă a timpilor pe tur.Problema este modelată ca o sarcină de învățare supervizată de tip regresie, unde modelul învață să prezică o valoare continuă pe baza condițiilor de cursă.

## 📊 Setul de Date
* S-au utilizat date de telemetrie și cronometrare din sezonul 2024 de Formula 1.
* Datele brute sunt structurate în fișiere CSV per sesiune, conținând informații detaliate despre fiecare tur efectuat de piloți.
* Variabila prezisă este TimeSec (timpul pe tur convertit în secunde).
* Variabilele de intrare sunt: Circuitul, Pilotul, Numărul turului, Tipul pneului, Uzura pneului, Temperaturile, Umiditatea și nivelul de combustibil.

## ⚙️ Preprocesarea Datelor
* Au fost eliminate tururile de ieșire de la boxe și tururile de intrare la boxe.
* S-a folosit metoda intervalului interquartilic (IQR) pentru a elimina tururile anomalice, păstrând doar timpii relevanți statistic.
* Datele meteorologice lipsă au fost completate cu medii standard.
* Variabilele categorice au fost transformate în valori numerice folosind LabelEncoder.

## 🧠 Modele de Machine Learning
* HistGradientBoostingRegressor (HGBR): Model principal, optimizat cu constrângeri monotonice pentru a respecta fizica uzurii pneurilor.
* RandomForestRegressor: Model secundar, folosit pentru validare încrucișată și robustețe.

## 📈 Rezultate și Performanță
* În condiții normale de cursă, diferența dintre predicție și realitate este frecvent sub 0.1 - 0.2 secunde.
* Distribuția punctelor arată o liniaritate puternică, acestea grupându-se strâns în jurul diagonalei ideale.
* Aceasta demonstrează că modelul are o eroare mică și constantă[cite: 25].
* Când diferența dintre predicție și realitate este mare, modelul funcționează ca un detector de anomalii.
* Modelul HistGradientBoosting s-a dovedit superior în captarea nuanțelor fine (degradarea pneurilor).
