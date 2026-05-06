# Use Cases + aktorzy — PeelP50_Proto

Dokument opisuje aktorów oraz przypadki użycia interaktywnej aplikacji Unity uruchamianej na kiosku multimedialnym w Muzeum Motoryzacji Wena w Oławie.

Aplikacja działa jako rozwiązanie typu standalone, bez backendu, bez kont użytkowników i bez wymaganego połączenia z Internetem. System został przygotowany do obsługi dotykowej oraz pracy w trybie kioskowym.

---

# 1. Aktorzy

## 1.1 Zwiedzający / użytkownik kiosku

Osoba korzystająca z aplikacji na ekranie dotykowym kiosku muzealnego.

### Cele użytkownika:
- wybrać dostępny moduł aplikacji,
- obejrzeć wnętrze pojazdu Peel P50 w trybie 360,
- odsłuchać dźwięki pojazdu,
- uruchomić jazdę testową,
- sprawdzić wyniki przejazdu.

---

## 1.2 Administrator / opiekun ekspozycji

Osoba odpowiedzialna za uruchomienie kiosku oraz zapewnienie ciągłości działania stanowiska.

### Cele administratora:
- uruchomić kiosk i aplikację,
- zapewnić stabilne działanie stanowiska,
- ograniczyć potrzebę ręcznej obsługi,
- w razie potrzeby zresetować urządzenie lub wyczyścić lokalną tabelę wyników.

---

# 2. Założenia systemu

- aplikacja działa offline,
- brak backendu i API,
- brak logowania użytkowników,
- brak przetwarzania danych osobowych,
- wyniki TOP 5 zapisywane są lokalnie przy użyciu PlayerPrefs,
- aplikacja działa na kiosku dotykowym,
- system automatycznie wraca do menu głównego po czasie bezczynności,
- aplikacja działa w trybie kioskowym,
- użytkownik nie może opuścić aplikacji i przejść do systemu Android.

---

# 3. Przypadki użycia

---

# UC-01 — Uruchomienie aplikacji i menu główne

## Aktor
Zwiedzający

## Cel
Rozpoczęcie korzystania z aplikacji.

## Warunek wstępny
Aplikacja jest uruchomiona na kiosku.

## Scenariusz główny
1. Zwiedzający podchodzi do kiosku.
2. Aplikacja wyświetla menu główne.
3. Użytkownik wybiera jeden z dostępnych modułów:
   - widok 360,
   - dźwięki pojazdu,
   - jazda testowa.

## Rezultat
System przechodzi do wybranego modułu.

---

# UC-02 — Nawigacja po menu

## Aktor
Zwiedzający

## Cel
Wybranie funkcji aplikacji.

## Warunek wstępny
Menu główne jest aktywne.

## Scenariusz główny
1. Użytkownik wybiera przycisk modułu.
2. System ładuje odpowiednią scenę.
3. Użytkownik rozpoczyna interakcję.

## Rezultat
Wybrany moduł zostaje uruchomiony.

---

# UC-03 — Widok wnętrza 360

## Aktor
Zwiedzający

## Cel
Obejrzenie wnętrza Peel P50 w trybie panoramicznym.

## Warunek wstępny
Użytkownik wybrał moduł widoku 360.

## Scenariusz główny
1. System uruchamia widok 360 wnętrza pojazdu.
2. Użytkownik przesuwa palcem po ekranie.
3. Kamera obraca się zgodnie z ruchem użytkownika.
4. Zwiedzający ogląda wnętrze pojazdu.
5. Użytkownik wybiera przycisk powrotu.
6. System wraca do menu głównego.

## Rezultat
Użytkownik kończy przeglądanie wnętrza pojazdu.

## Scenariusz alternatywny
Jeżeli użytkownik pozostaje nieaktywny przez określony czas, aplikacja automatycznie wraca do menu głównego.

---

# UC-04 — Odtwarzanie dźwięków pojazdu

## Aktor
Zwiedzający

## Cel
Odtworzenie dźwięków związanych z pojazdem.

## Warunek wstępny
Użytkownik wybrał moduł dźwięków.

## Scenariusz główny
1. System wyświetla panel dźwięków.
2. Użytkownik wybiera jeden z dostępnych efektów:
   - uruchomienie silnika,
   - praca silnika,
   - klakson,
   - drzwi.
3. System odtwarza wybrany dźwięk.
4. Użytkownik może odtworzyć kolejny dźwięk lub wrócić do menu.

## Rezultat
Wybrany efekt audio zostaje odtworzony.

---

# UC-05 — Jazda testowa

## Aktor
Zwiedzający

## Cel
Uruchomienie uproszczonej symulacji jazdy.

## Warunek wstępny
Użytkownik wybrał moduł jazdy testowej.

## Scenariusz główny
1. System ładuje scenę jazdy testowej.
2. Pojazd zostaje ustawiony na pozycji startowej.
3. System wyświetla odliczanie.
4. Po zakończeniu odliczania rozpoczyna się jazda.
5. Użytkownik steruje pojazdem przy użyciu ekranowych przycisków.
6. Kamera podąża za pojazdem.
7. System wyświetla HUD:
   - prędkościomierz,
   - wskaźniki jazdy.

## Rezultat
Użytkownik może przejechać trasę testową.

## Scenariusz alternatywny
W przypadku bezczynności aplikacja automatycznie wraca do menu głównego.

---

# UC-06 — Pomiar czasu przejazdu

## Aktor
Zwiedzający

## Cel
Uzyskanie czasu przejazdu.

## Warunek wstępny
Aktywna jazda testowa.

## Scenariusz główny
1. Pojazd przekracza linię startu.
2. System rozpoczyna pomiar czasu.
3. Użytkownik przejeżdża trasę.
4. Pojazd przekracza linię mety.
5. System zatrzymuje pomiar czasu.
6. Wynik zostaje wyświetlony.

## Rezultat
System prezentuje czas przejazdu.

---

# UC-07 — Ranking TOP 5

## Aktor
Zwiedzający

## Cel
Wyświetlenie najlepszych wyników.

## Warunek wstępny
Użytkownik ukończył przejazd.

## Scenariusz główny
1. System porównuje wynik użytkownika z lokalną tabelą rekordów.
2. Jeżeli wynik znajduje się w TOP 5:
   - system zapisuje rekord,
   - aktualizuje ranking.
3. System wyświetla tabelę najlepszych wyników.

## Rezultat
Ranking zostaje zaktualizowany.

## Scenariusz alternatywny
Jeżeli wynik nie znajduje się w TOP 5, tabela pozostaje bez zmian.

---

# UC-08 — Ponowne uruchomienie przejazdu

## Aktor
Zwiedzający

## Cel
Rozpoczęcie kolejnego przejazdu.

## Warunek wstępny
Poprzedni przejazd został zakończony.

## Scenariusz główny
1. Użytkownik wybiera opcję restartu.
2. System resetuje pozycję pojazdu.
3. System zeruje czas przejazdu.
4. Rozpoczyna się nowe odliczanie.
5. Użytkownik rozpoczyna kolejny przejazd.

## Rezultat
Nowa jazda testowa zostaje uruchomiona.

---

# UC-09 — Czyszczenie tabeli rekordów

## Aktor
Administrator / opiekun ekspozycji

## Cel
Usunięcie zapisanych wyników TOP 5.

## Warunek wstępny
Tabela wyników jest dostępna.

## Scenariusz główny
1. Administrator wybiera opcję wyczyszczenia rekordów.
2. System usuwa zapisane dane lokalne.
3. Ranking zostaje wyzerowany.

## Rezultat
Tabela rekordów zostaje wyczyszczona.

---

# UC-10 — Automatyczny reset po bezczynności

## Aktor
Zwiedzający

## Cel
Przywrócenie aplikacji do stanu gotowości.

## Warunek wstępny
Aplikacja działa w dowolnym module.

## Scenariusz główny
1. Użytkownik przestaje korzystać z aplikacji.
2. System monitoruje czas bezczynności.
3. Po przekroczeniu limitu czasu system automatycznie wraca do menu głównego.

## Rezultat
Aplikacja jest gotowa dla kolejnego użytkownika.

---

# UC-11 — Obsługa kiosku

## Aktor
Administrator / opiekun ekspozycji

## Cel
Zapewnienie poprawnego działania stanowiska.

## Warunek wstępny
Kiosk znajduje się na ekspozycji muzealnej.

## Scenariusz główny
1. Administrator uruchamia kiosk.
2. Android uruchamia aplikację w trybie kioskowym.
3. System automatycznie wyświetla menu główne.
4. Administrator sprawdza działanie ekranu dotykowego.
5. W razie problemu wykonuje restart urządzenia.

## Rezultat
Stanowisko działa poprawnie i jest gotowe dla zwiedzających.

---

# 4. Kryteria akceptacji

- aplikacja uruchamia się poprawnie na kiosku,
- menu główne jest dostępne po uruchomieniu,
- użytkownik może przejść do wszystkich modułów,
- widok 360 działa poprawnie,
- dźwięki pojazdu odtwarzają się prawidłowo,
- jazda testowa uruchamia się poprawnie,
- system mierzy czas przejazdu,
- ranking TOP 5 zapisuje wyniki lokalnie,
- użytkownik może ponownie uruchomić przejazd,
- aplikacja automatycznie wraca do menu po bezczynności,
- system działa bez Internetu,
- aplikacja nie wymaga logowania,
- interfejs jest dostosowany do obsługi dotykowej,
- użytkownik nie może opuścić aplikacji i przejść do systemu Android.
