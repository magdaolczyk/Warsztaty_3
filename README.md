# Warsztaty_3


FUNKCJE APLIKACJI:

1. Jako użytkownik chcę po wejściu na stronę główną widzieć wszystkie sale konferencyjne i ich status danego dnia: zajęte lub wolne. Obok nazwy każdej sali chcę mieć link do modyfikacji danych sali oraz do jej usunięcia.

2. Jako użytkownik po kliknięciu w nazwę sali chcę zobaczyć wszystkie dane sali: jej nazwę, pojemność oraz informację, czy ma rzutnik. Dodatkowo chcę zobaczyć listę dni, w które sala będzie zajęta. Nie chcę widzieć dni, które minęły. Chcę widzieć link, który pozwoli zarezerwować tę salę.

3. Jako użytkownik chcę móc dodać nową salę.

4. Jako użytkownik po wejściu na stronę edycji sali chcę móc podać dane sali (nazwa, pojemność, rzutnik, ew. inne dane).

5. Jako użytkownik po wejściu na stronę z rezerwacją sali ponownie chcę zobaczyć listę dni, w których sala będzie zajęta (warunki jak w pkt. 2). Chcę móc podać datę rezerwacji danej sali. System powinien dbać o to, by nie dublować rezerwacji danego dnia dla danej sali i żeby data nie była z przeszłości. (Wystarczy walidacja po stronie widoku. Nie musisz implementować odpowiedniego mechanizmu w modelu).

6. Jako użytkownik chcę móc wyszukać sale z podaniem następujących warunków:
    - nazwa sali,
    - dzień,
    - pojemność sali,
    - dostępność rzutnika.


MODELE W APLIKACJI

Sala - Jest to reprezentacja sali w aplikacji. Powinna przechowywać następujące wartości: nazwa, pojemność, dostępność rzutnika.

Rezerwacja - Ma reprezentować rezerwację sali na dany dzień. Powinien przechowywać następujące dane: datę, id sali, komentarz dodany przy rezerwacji. Powinna być połączona z obiektem Sala relacją: jedna sala może mieć wiele całodniowych rezerwacji, każdą innego dnia.


ZADANIA


1. Przygotowanie projektu
Najpierw przygotuj nowy projekt, skonfiguruj projekt (połączenie z bazą danych, szablony itp.), stwórz nową aplikację.
2. Utwórz szablon bazowy
Stwórz szablon bazowy do aplikacji. Nie musi być wyrafinowany i skomplikowany. Umieść w nim elementy, które będą widoczne na wszystkich stronach, takie jak tytuł, stopka, menu itp.
3. Model sali
Stwórz nowy model dla sali. Jeżeli chcesz przetrzymywać dodatkowe informacje, to zaplanuj to teraz.
4. URL-e do Sali
Stwórz URL-e z następującymi funkcjonalnościami do zarządzania salami:
    a) Tworzenie formularza do stworzenia nowej sali (/room/new).
    b) Tworzenie nowej sali (POST formularza na adres /room/new).
    c) Tworzenie formularza do modyfikacji sali (/room/modify/{id}).
    d) Modyfikacja sali (POST formularza na adres /room/modify/{id}).
    e) Usunięcie podanej sali (/room/delete/{id}).
    f) Pokazanie danych jednej sali (/room/{id}).
    g) Pokazanie wszystkich sal (/).
5. Sala
Stwórz widoki sali. Widoki powinny wyświetlać/odbierać formularze lub wyświetlać listę sal. Nie zapomnij o przycisku Nowa sala i jego obsłudze na ekranie głównym.
6. Rezerwacja sali
Stwórz nowy model dla rezerwacji. Zmodyfikuj model sali w taki sposób, żeby trzymała relacje.
7. Zmiana widoku sali
Zmodyfikuj widok danych sali tak, aby umożliwiał dokonania rezerwacji.
Widok zmień następująco:
    a) Dodaj do widoku formularz, który będzie odsyłał do strony POST /reservation/{id-sali}
    b) Dodaj widok, który obsłuży formularz. Widok powinien sprawdzić następujące rzeczy:
        - czy sala jest już zarezerwowana tego dnia?
        - czy data rezerwacji nie jest z przeszłości?
Jeśli któryś z tych warunków zostanie spełniony, poinformuj użytkownika o błędzie. Jeśli dokonana zostanie rezerwacja, przenieś użytkownika na stronę główną.
8. Wyszukiwanie
Dodaj do strony głównej wyszukiwarkę. Umieść tam formularz przyjmujący wartości, według których program ma szukać wolnej sali:
    a) nazwę sali,
    b) minimalna potrzebna pojemność sali,
    c) dzień,
    d) obecność rzutnika.
Niech formularz wysyła dane metodą GET na adres /search.
Utwórz widok, w którym odbierzesz metodą GET dane z formularza wyszukiwania. Na podstawie tych danych zbuduj zapytanie do modeli, które wyszuka sale według podanych kryteriów.
Widok powinien zwrócić listę wolnych sal. Jeśli nie znajdzie żadnej, powinien pojawić się komunikat „Brak wolnych sal dla podanych kryteriów wyszukiwania”.

