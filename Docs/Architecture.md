# Architektura logiczna i komponenty
Interaktywna aplikacja muzealna Peel P50 (Unity)

## 1. Charakterystyka ogólna

Aplikacja została zaprojektowana jako autonomiczna aplikacja kioskowa typu standalone, uruchamiana na dedykowanym urządzeniu multimedialnym w przestrzeni Muzeum Motoryzacji Wena.

System działa całkowicie lokalnie i nie wykorzystuje backendu, komunikacji sieciowej ani zewnętrznych interfejsów API. Wszystkie funkcje aplikacji realizowane są bezpośrednio w środowisku Unity przy użyciu języka C#.

Architektura aplikacji oparta została na podziale funkcjonalnym na sceny Unity oraz modularne komponenty logiczne realizowane przez skrypty C#.

---

## 2. Warstwy logiczne aplikacji

### 2.1 Warstwa prezentacji (UI)

Warstwa odpowiedzialna za interfejs użytkownika, nawigację oraz obsługę interakcji dotykowych.

Główne komponenty:
- MenuController – obsługa menu głównego oraz nawigacji między modułami aplikacji
- MainMenuController – zarządzanie logiką wyboru trybów interakcji
- UI Button Controllers – obsługa przycisków dotykowych
- CanvasAutoMatch / SafeAreaFitter – automatyczne dopasowanie interfejsu do proporcji i rozdzielczości ekranu kiosku
- InstructionHint – wyświetlanie podpowiedzi i komunikatów dla użytkownika

Warstwa została zoptymalizowana pod kątem prostoty obsługi oraz czytelności na ekranach dotykowych używanych w środowisku publicznym.

---

### 2.2 Warstwa logiki aplikacji

Warstwa odpowiedzialna za sterowanie przebiegiem działania aplikacji oraz kontrolę stanów systemu.

Główne komponenty:
- IdleReturn – mechanizm automatycznego powrotu do menu głównego po określonym czasie bezczynności użytkownika
- RaceManager – logika pomiaru czasu przejazdu i zarządzanie rankingiem wyników
- StartFinishTrigger / RaceTrigger – obsługa zdarzeń rozpoczęcia i zakończenia przejazdu
- Mechanizm PlayerPrefs – lokalne przechowywanie rekordów czasowych (TOP 5)

Warstwa logiki została zaprojektowana w sposób możliwie uproszczony, aby zapewnić stabilną pracę aplikacji w trybie ciągłym na urządzeniu kioskowym.

---

### 2.3 Warstwa symulacji i interakcji 3D

Warstwa odpowiedzialna za fizykę pojazdu, ruch kamery oraz interakcję użytkownika z wirtualnym środowiskiem.

Główne komponenty:
- PeelController_Lite – autorski kontroler pojazdu odpowiadający za uproszczoną fizykę jazdy
- CameraFollow – system podążania kamery
- SpeedometerAnalog – analogowy wskaźnik prędkości
- GearIndicatorUI – wskaźnik aktualnego biegu

Warstwa została zoptymalizowana pod kątem płynności działania na urządzeniu docelowym oraz prostoty sterowania dla użytkowników muzeum.

---

### 2.4 Warstwa multimedialna

Warstwa odpowiedzialna za obsługę efektów dźwiękowych oraz treści multimedialnych.

Główne komponenty:
- PeelEngineSound – generowanie dźwięku silnika podczas jazdy
- PeelSoundMenu – obsługa efektów dźwiękowych i interakcji audio

Zastosowane rozwiązania multimedialne mają na celu zwiększenie zaangażowania użytkownika oraz atrakcyjności ekspozycji muzealnej.

---

## 3. Struktura scen Unity

Aplikacja została podzielona na odrębne sceny Unity odpowiadające konkretnym funkcjom systemu.

Najważniejsze sceny:
- Menu główne (centralny hub aplikacji)
- Scena widoku 360 wnętrza pojazdu
- Scena jazdy testowej
- Scena interaktywnego modułu dźwięków

Każda scena realizuje jeden jasno określony cel funkcjonalny, co upraszcza zarządzanie aplikacją oraz poprawia stabilność działania.

---

## 4. Komunikacja między komponentami

Komunikacja pomiędzy komponentami realizowana jest lokalnie poprzez:
- referencje komponentów Unity,
- wywoływanie metod publicznych,
- system zdarzeń i triggerów.

Aplikacja nie wykorzystuje komunikacji sieciowej ani zewnętrznych usług API.

Dane tymczasowe, takie jak rekordy czasowe użytkowników, przechowywane są lokalnie przy użyciu mechanizmu PlayerPrefs.

---

## 5. Uzasadnienie przyjętej architektury

Zastosowana architektura została dobrana świadomie do:
- charakteru ekspozycji muzealnej,
- ograniczeń sprzętowych kiosku,
- wymagań pracy ciągłej,
- potrzeby maksymalnej stabilności i prostoty obsługi.

Przyjęty podział na sceny oraz modularne komponenty logiczne:
- upraszcza utrzymanie aplikacji,
- umożliwia dalszą rozbudowę projektu,
- pozwala łatwo dodawać nowe pojazdy lub sceny,
- ogranicza ryzyko błędów podczas pracy w środowisku publicznym.

Architektura jest adekwatna do skali projektu wdrożeniowego i odpowiada rzeczywistym wymaganiom beneficjenta.
