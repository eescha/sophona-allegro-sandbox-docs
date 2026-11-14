# Sophona — integracja Allegro Sandbox

## Przeznaczenie

Prywatna aplikacja testowa do integracji panelu Base w Sophonie z własnym kontem Allegro Sandbox. Projekt jest przeznaczony wyłącznie do użytku własnego. Nie jest usługą dla innych sprzedawców ani oficjalnym produktem Allegro.

## Status

Wersja dokumentacyjna: 1.0. Stan na 14 listopada 2026 r.: integracja w trakcie konfiguracji i testów. Pełny przebieg autoryzacji i operacji API nie został jeszcze potwierdzony testem end-to-end. Publikacja tej dokumentacji nie oznacza gotowości produkcyjnej.

## Zakres prac

Przygotowano kod konfiguracji połączenia OAuth, importu ofert i przypisywania ofert do produktów Base. Funkcje te wymagają dalszej weryfikacji z kontem testowym.

Planowany zakres obejmuje odczyt ofert, synchronizację cen i stanów magazynowych, import zamówień oraz aktualizację statusu ich realizacji. Nie wszystkie wymienione funkcje zostały wdrożone lub przetestowane.

## Autoryzacja i środowisko

Docelowy przebieg: użytkownik uruchamia połączenie w Base, loguje się na stronie Allegro Sandbox i udziela zgody, a backend obsługuje powrót OAuth i zapis połączenia. Testy dotyczą środowiska Sandbox, nie konta produkcyjnego.

## Dane i bezpieczeństwo

To repozytorium zawiera wyłącznie dokumentację. Nie zawiera kodu prywatnego panelu, Client Secret, tokenów, ciasteczek sesyjnych ani danych klientów i zamówień. Dane uwierzytelniające nie powinny być publikowane w zgłoszeniach. Przegląd bezpieczeństwa integracji pozostaje częścią prac przed ewentualnym użyciem produkcyjnym.

## Kontakt

Właściciel integracji / kontakt techniczny: biuro@parts4you.pl

## Strona dokumentacji

Niniejszy README jest publicznym opisem integracji. Osobna strona w Sophonie jest planowana; jej adres zostanie dodany po publikacji i sprawdzeniu.
