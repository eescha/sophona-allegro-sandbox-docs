# Base w Sophonie — panel sprzedaży i integracja Allegro Sandbox

Publiczna dokumentacja prywatnej aplikacji Base rozwijanej i uruchamianej na platformie Sophona. Repozytorium opisuje przeznaczenie aplikacji, jej moduły oraz zakres prac nad integracją Allegro. Nie jest repozytorium kodu źródłowego panelu.

Kontakt: **biuro@parts4you.pl**

## Przeznaczenie i odbiorcy

Base jest panelem do obsługi własnej sprzedaży, katalogu produktów, magazynu i zamówień. Aplikacja jest przeznaczona do użytku własnego, z rozróżnieniem dostępu administratora i pracownika. Nie jest obecnie usługą oferowaną innym sprzedawcom.

Integracja marketplace jest rozwijana z myślą o własnym koncie Allegro. Na obecnym etapie konfiguracja i testy dotyczą Allegro Sandbox. Projekt nie jest oficjalnym produktem Allegro ani deklaracją certyfikacji integratora.

## Moduły panelu

Poniższa tabela opisuje zakres funkcjonalny projektu. Nie stanowi potwierdzenia zakończenia testów każdej funkcji.

| Moduł | Zakres |
| --- | --- |
| Produkty | Katalog produktów, warianty i identyfikatory SKU |
| Magazyn | Stany magazynowe i rezerwacje |
| Zamówienia | Obsługa zamówień, statusy, notatki i historia zmian |
| Klienci | Ewidencja klientów związanych ze sprzedażą |
| Oferty wewnętrzne | Obsługa ofert w panelu, odrębna od ofert Allegro |
| Cenniki | Ceny i reguły cenowe |
| Raporty i dziennik | Raportowanie oraz rejestrowanie zdarzeń |
| Użytkownicy | Role i ograniczenia uprawnień administratora oraz pracownika |
| Marketplace | Konfiguracja połączenia Allegro i rozwijana obsługa ofert |

## Architektura

- Interfejs: React 18 i Vite 5.
- Backend: Node.js i Express.
- Dane biznesowe: projekt przewiduje trwałą bazę SQLite obsługiwaną przez backend. localStorage nie jest bazą danych biznesowych.
- Hosting i podgląd deweloperski: Sophona Native App.
- Integracja z Allegro: logika wywołań API i obsługi tokenów znajduje się w backendzie, nie w publicznej dokumentacji.

Schemat docelowego przepływu:

```text
Użytkownik → interfejs Base → backend Express → baza danych
                                      ↓
                               Allegro Sandbox API
```

## Integracja Allegro — stan prac

| Obszar | Stan udokumentowany na 14 listopada 2026 |
| --- | --- |
| Konfiguracja połączenia | Przygotowano ekran i endpointy konfiguracji |
| OAuth Authorization Code | Przygotowano kod rozpoczęcia autoryzacji, callbacku i obsługi tokenów; pełny test z kontem Sandbox pozostaje do wykonania |
| Oferty Allegro | Przygotowano kod importu, listy i przypisania oferty do produktu Base; poprawność z rzeczywistymi danymi Sandbox wymaga weryfikacji |
| Ceny i stany | Synchronizacja do Allegro pozostaje zakresem dalszych prac i testów |
| Zamówienia Allegro | Import, ekran zamówień i obsługa realizacji pozostają kolejnymi etapami |
| Logi integracji | Przygotowano mechanizm zapisu wybranych operacji; ekran diagnostyczny i pełna obsługa błędów wymagają dalszych prac |
| User-Agent | Konfiguracja własnego identyfikatora jest w toku; jego wdrożenie w wywołaniach backendu nie zostało potwierdzone |

Przygotowanie kodu nie oznacza udanego testu end-to-end. Integracja wymaga dalszych poprawek oraz przeglądu bezpieczeństwa przed ewentualnym użyciem produkcyjnym.

## Docelowy sposób podłączenia konta

1. Administrator konfiguruje dane aplikacji dla środowiska testowego.
2. Użytkownik uruchamia połączenie w sekcji Marketplace.
3. Base przekierowuje go do autoryzacji na stronie Allegro Sandbox.
4. Po udzieleniu zgody backend obsługuje callback i zapis połączenia.
5. Użytkownik uruchamia import ofert i przypisuje je do produktów Base.

To opis zamierzonego przebiegu, nie potwierdzenie zakończonego testu. Hasła do Allegro należy podawać wyłącznie na stronie logowania Allegro, nie w dokumentacji ani zgłoszeniach.

## Aktualny status i weryfikacja

Stan dokumentacji: **14 listopada 2026 r.**

- Podgląd deweloperski Base został uruchomiony; kontrola platformy potwierdziła serwowanie strony i jej zasobów.
- Właściciel potwierdził, że aplikacja otwiera się po uruchomieniu podglądu.
- Nie przeprowadzono w tej sesji pełnego testu wszystkich ekranów ani API.
- Pełna autoryzacja i operacje Allegro Sandbox nie zostały potwierdzone testem end-to-end.
- Aplikacja nie została wdrożona na produkcję.
- Osobna publiczna strona dokumentacji w Sophonie nie została jeszcze opublikowana.

## Bezpieczeństwo i zawartość repozytorium

Repozytorium zawiera wyłącznie dokumentację. Nie publikujemy w nim kodu prywatnego panelu, kopii baz danych, danych klientów, zamówień, haseł, Client Secret, tokenów ani ciasteczek sesyjnych. Dokumentacja nie stanowi audytu bezpieczeństwa.

W zgłoszeniach technicznych należy usuwać nagłówki Cookie, Set-Cookie i Authorization oraz dane osobowe. Kontakt w sprawach integracji i bezpieczeństwa: **biuro@parts4you.pl**.

## Rozwój i testy

Prace prowadzone są etapami: plan, implementacja, test i akceptacja przed kolejnym etapem. Priorytetem jest dokończenie oraz weryfikacja połączenia Sandbox i importu ofert. Kolejne etapy obejmują synchronizację cen i stanów, zamówienia, realizację oraz diagnostykę. Decyzja o użyciu produkcyjnym pozostaje osobnym etapem.
