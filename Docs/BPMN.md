# BPMN – proces działania interaktywnego kiosku Peel P50

## Opis

Dokument przedstawia uproszczony proces BPMN (Business Process Model and Notation) opisujący działanie interaktywnego kiosku muzealnego Peel P50.

Proces obejmuje:
- przejście użytkownika do menu głównego,
- wybór modułu,
- uruchomienie wybranego trybu,
- interakcję użytkownika,
- automatyczny lub ręczny powrót do menu głównego.

Proces ma charakter cykliczny i został zaprojektowany dla środowiska publicznego (muzeum / wystawa interaktywna).

---

# Uczestnicy procesu (Pool / Lanes)

## Zwiedzający
Osoba korzystająca z kiosku interaktywnego.

## System
Aplikacja uruchomiona na kiosku odpowiedzialna za:
- wyświetlanie interfejsu,
- uruchamianie modułów,
- obsługę interakcji,
- monitorowanie aktywności użytkownika.

---

# Przebieg procesu BPMN

## 1. Zdarzenie początkowe

Proces rozpoczyna się zdarzeniem startowym systemu.

System przechodzi do menu głównego aplikacji.

---

## 2. Przejście do menu głównego

System:
- wyświetla menu główne,
- oczekuje na wybór modułu przez użytkownika.

---

## 3. Wybranie modułu

Zwiedzający wybiera jeden z dostępnych modułów systemu.

---

## 4. Bramka decyzyjna – „Jaki moduł został wybrany?”

System analizuje wybór użytkownika i uruchamia odpowiedni moduł.

Możliwe ścieżki procesu:

- prezentacja pojazdu,
- widok 360 wnętrza,
- jazda testowa,
- menu dźwięków pojazdów.

---

# Ścieżki procesu

## 4.1 Widok 360 wnętrza

### Zadanie systemowe
System uruchamia widok 360 wnętrza pojazdu.

### Aktywność użytkownika
Zwiedzający eksploruje widok wnętrza pojazdu.

---

## 4.2 Jazda testowa

### Zadanie systemowe
System uruchamia tryb jazdy testowej.

### Aktywność użytkownika
Zwiedzający steruje pojazdem.

---

## 4.3 Menu dźwięków pojazdów

### Zadanie systemowe
System uruchamia menu dźwięków pojazdów.

### Aktywność użytkownika
Zwiedzający słucha dźwięków pojazdu.

---

# Zakończenie interakcji

Każdy moduł może zostać zakończony na dwa sposoby.

## Wariant 1 – użycie przycisku „Wstecz”

Zwiedzający używa przycisku „Wstecz”.

System:
- kończy aktualny moduł,
- wraca do menu głównego.

---

## Wariant 2 – brak aktywności

System wykrywa brak aktywności użytkownika.

System:
- automatycznie kończy aktualny moduł,
- przywraca menu główne,
- przechodzi do stanu oczekiwania na kolejnego użytkownika.

---

# Charakterystyka procesu

- Proces działa lokalnie na kiosku.
- Proces nie wymaga backendu.
- Proces może być wykonywany wielokrotnie.
- System działa autonomicznie.
- Proces został zaprojektowany dla środowiska muzealnego.

---

# Elementy BPMN wykorzystane w diagramie

## Zdarzenia
- Start Event
- Timer Event („brak aktywności”)

## Bramki
- Exclusive Gateway (XOR)

## Zadania
- zadania systemowe,
- aktywności użytkownika.

## Przepływy
- przepływ sekwencyjny pomiędzy modułami,
- powrót do menu głównego.

---

# Podsumowanie

Diagram BPMN przedstawia uproszczony proces obsługi interaktywnego kiosku muzealnego Peel P50.

Proces umożliwia:
- wybór modułu przez użytkownika,
- uruchomienie interaktywnego doświadczenia,
- obsługę aktywności użytkownika,
- automatyczny reset systemu po zakończeniu interakcji.# BPMN – proces end-to-end (kiosk Peel P50)

Dokument opisuje uproszczony proces end-to-end działania interaktywnej aplikacji muzealnej Peel P50, zgodnie z ideą BPMN (Business Process Model and Notation).

Proces obejmuje pełną ścieżkę od uruchomienia aplikacji na kiosku, poprzez interakcję zwiedzającego, aż do automatycznego powrotu systemu do stanu początkowego.

## 1. Uczestnicy procesu (Pool / Lanes)

- Zwiedzający (użytkownik kiosku)
- System (aplikacja Unity uruchomiona na kiosku)

## 2. Opis procesu głównego (end-to-end)

### Start procesu
Zdarzenie początkowe:
- Aplikacja uruchomiona na kiosku
- Wyświetlany ekran startowy (Tap to Start)

### Przebieg procesu

1. Zwiedzający dotyka ekranu startowego  
   → System przechodzi do menu głównego

2. Zwiedzający wybiera tryb działania  
   (widok 360 / jazda testowa)

3. System uruchamia wybrany moduł:
   - widok 360 wnętrza
   - tryb jazdy testowej

4. Zwiedzający korzysta z wybranego modułu:
   - sterowanie pojazdem
   - eksploracja widoku

5. Zwiedzający kończy interakcję:
   - używa przycisku „Wstecz”
   LUB
   - opuszcza kiosk (brak aktywności)

6. System:
   - wraca do menu głównego
   - lub po czasie bezczynności automatycznie resetuje widok

### Zdarzenie końcowe
- Aplikacja znajduje się w stanie początkowym (menu)
- Kiosk gotowy dla kolejnego zwiedzającego

## 3. Decyzje i zdarzenia (bramki BPMN – uproszczone)

- Decyzja: „Czy użytkownik jest aktywny?”
  - TAK → kontynuuj interakcję
  - NIE → automatyczny powrót do menu

- Decyzja: „Czy użytkownik wybrał tryb?”
  - TAK → uruchom moduł
  - NIE → pozostań w menu

## 4. Charakterystyka procesu

- Proces jest w pełni autonomiczny (brak backendu).
- Proces może być wykonywany wielokrotnie w pętli.
- Projektowany pod środowisko publiczne (muzeum).

Uwaga:
Diagram BPMN został uproszczony do formy opisowej ze względu na charakter projektu i środowisko akademickie.
