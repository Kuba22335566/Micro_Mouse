# 🐭 Micro_Mouse

Autonomiczny robot klasy **Micromouse** oparty na mikrokontrolerze **ESP32-WROVER-IE**, zaprojektowany do samodzielnej eksploracji labiryntu oraz wyznaczania i pokonywania najkrótszej trasy do celu.

Poniżej znajduje się plan realizacji projektu podzielony na trzy główne etapy.

![Plan budowy robota Micromouse](assets/roadmap.png)

## 🗺️ Kamienie Milowe

```text
[KM 1: SPRZĘT & STEROWNIKI] ───► [KM 2: ALGORYTM FLOODFILL] ───► [KM 3: KONSTRUKCJA & OPTYMALIZACJA]
```

---

### 🔧 KM 1: Warstwa sprzętowa i sterowniki (HAL)
> **Cel:** Uruchomienie i przetestowanie każdego podzespołu „na biurku” (makieta testowa).

- [ ] **ESP32-WROVER-IE:** Konfiguracja mikrokontrolera (rezerwacja pinów, eliminacja konfliktów z PSRAM i ADC2).
- [ ] **Silniki i enkodery:** Obsługa PWM (mostek H) oraz zliczanie impulsów (odometria i prędkość kół).
- [ ] **Czujniki odległości:** Pulsacyjne wyzwalanie diod IR + odczyty ADC (eliminacja wpływu światła otoczenia).
- [ ] **IMU MPU6050:** Komunikacja I2C i odczyt żyroskopu (estymacja kąta obrotu robota).

**✅ Kryterium sukcesu:** Poprawne, stabilne odczyty z każdego czujnika i płynne sterowanie silnikami w czasie rzeczywistym.

---

### 🧠 KM 2: Algorytm nawigacji (Floodfill)
> **Cel:** Zaprogramowanie „mózgu” robota i przetestowanie go w symulacji.

- [ ] **Wirtualny labirynt:** Struktura mapy 16×16 w pamięci (zapisywanie odkrywanych ścian).
- [ ] **Algorytm Floodfill:** Dynamiczne przeliczanie najkrótszej drogi do celu (przypisywanie wag komórkom).
- [ ] **Maszyna stanów:** Obsługa faz (`eksploracja` → `powrót na start` → `szybki bieg po trasie optymalnej`).
- [ ] **Symulacja (SIL):** Testy kodu w symulatorze (np. MMS) na różnych układach labiryntów.

**✅ Kryterium sukcesu:** Algorytm bezbłędnie rozwiązuje i optymalizuje trasy w symulacji (brak pętli i błędów).

---

### 🏎️ KM 3: Integracja, testy i ulepszanie
> **Cel:** Złożenie gotowego robota, kalibracja ruchu i walka o czas.

- [ ] **Budowa i zasilanie:** Montaż mechaniczny, stabilne zasilanie z pakietu LiPo (separacja zakłóceń).
- [ ] **Pętle PID:** Kaskadowa regulacja prędkości, jazdy prosto oraz trzymania się środka korytarza za pomocą czujników bocznych.
- [ ] **Korekcja i kalibracja:** Wykorzystanie krawędzi ścian (detekcja przerw) do zerowania błędu odometrii.
- [ ] **Optymalizacja:** Płynne zakręty bez zatrzymywania się, jazda po przekątnych oraz podkręcanie prędkości maksymalnej.

**✅ Kryterium sukcesu:** Autonomiczne pokonanie fizycznego labiryntu i wykonanie szybkiego przejazdu bez kolizji.
