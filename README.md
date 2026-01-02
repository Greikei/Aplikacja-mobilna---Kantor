# Aplikacja-mobilna---Kantor
SZABLON DOKUMENTACJI PROJEKTOWEJ 

Przedmiot: Zagadnienia sieciowe w systemach mobilnych 

Część 1 – Projekt koncepcyjny 

Temat projektu: System mobilny kantoru wymiany walut (lub alternatywny temat zaakceptowany przez prowadzącego) 

1. Informacje ogólne 

Nazwa projektu 

 

Autorzy projektu 

 

Kierunek studiów 

 

Rok / Semestr 

 

Prowadzący 

 

Data oddania 

 

2. Opis projektu 

2.1. Cel projektu 

Celem projektu jest stworzenie mobilnej aplikacji Personal Data Turist, która wspiera użytkownika w planowaniu i realizacji podróży poprzez dostarczanie w czasie rzeczywistym informacji o jego aktualnej lokalizacji, warunkach pogodowych, jakości powietrza oraz kursach walut. 

 

Aplikacja automatycznie pobiera bieżące dane meteorologiczne i o zanieczyszczeniu powietrza, kursy walut, a także listę atrakcji turystycznych w określonym promieniu od użytkownika.  Po wybraniu zakładki Gastronomia system pobiera najbliższe restauracje i lokale gastronomiczne. 

 

Użytkownik może zapisywać wybrane miejsca jako ulubione w lokalnej bazie danych, a aplikacja wyświetli powiadomienia push, gdy: 

•	poziom smogu przekroczy ustalone normy, 

•	prognoza zapowiada deszcz, 

•	użytkownik znajdzie się w odległości poniżej 300 m od zapisanej lokalizacji. 

 

Dodatkowo system umożliwia nawigację do wybranego punktu co zwiększa komfort korzystania z aplikacji. 

 

Wartość użytkowa systemu polega na połączeniu funkcji informacyjnych, finansowych i praktycznych w jednym narzędziu, które dostarcza spersonalizowanych danych turystycznych, klimatycznych, ekonomicznych i nawigacyjnych – wspierając użytkownika w planowaniu i bezpiecznym odkrywaniu nowych miejsc. 

2.2. Zakres projektu 

2.2. Zakres projektu – opis modułów systemu oraz ich roli 

 

Projekt Personal Data Turist obejmuje zestaw modułów tworzących spójny system, którego celem jest dostarczanie użytkownikowi informacji turystycznych, pogodowych, ekonomicznych i środowiskowych w czasie rzeczywistym. 

 

⸻ 

 

1. Moduł aplikacji mobilnej (Frontend) – React Native (Expo) 

•	Główna część interfejsu użytkownika umożliwiająca interakcję z systemem. 

•	Realizuje kluczowe funkcje: 

•	logowanie i rejestracja użytkownika, 

•	pobieranie i wyświetlanie aktualnej lokalizacji GPS, 

•	prezentacja pogody, jakości powietrza i kursów walut, 

•	wyświetlanie atrakcji turystycznych i restauracji, 

•	zapisywanie miejsc do ulubionych, 

•	obsługa powiadomień push. 

•	Komunikacja z backendem odbywa się przez REST API w formacie JSON. 

•	Technologia: React Native (Expo), z wykorzystaniem bibliotek takich jak expo-location, expo-notifications, react-navigation, axios. 

 

⸻ 

 

2. Moduł serwera aplikacji (Backend) – Node.js + Express 

•	Odpowiada za logikę biznesową i pośredniczy między aplikacją mobilną a bazą danych oraz zewnętrznymi API. 

•	Realizuje funkcje: 

•	autoryzacja i uwierzytelnianie użytkowników (JWT), 

•	pobieranie i przetwarzanie danych z zewnętrznych API: 

•	OpenWeatherMap API – dane pogodowe, 

•	IQAir API – jakość powietrza, 

•	NBP API – kursy walut, 

•	OpenTripMap / Google Places API – atrakcje turystyczne i gastronomia, 

•	Google Maps Directions API – nawigacja. 

•	Odpowiada za wysyłanie danych w ujednoliconym formacie JSON do aplikacji mobilnej. 

•	Zapewnia warstwę bezpieczeństwa oraz kontrolę dostępu do danych użytkownika. 

 

⸻ 

 

3. Moduł bazy danych – MySQL 

•	Przechowuje dane trwałe aplikacji, takie jak: 

•	informacje o użytkownikach, 

•	zapisane lokalizacje ulubionych miejsc i restauracji, 

•	historia wyszukiwań, 

•	dane powiązane z ustawieniami użytkownika. 

•	Struktura bazy danych obejmuje tabele m.in.: 

Users, Favorites, Places, Restaurants, Notifications. 

•	Komunikacja z backendem realizowana poprzez ORM Sequelize lub natywne zapytania SQL. 

 

⸻ 

 

4. Moduł powiadomień push 

•	Odpowiada za wysyłanie automatycznych powiadomień w sytuacjach: 

•	przekroczenia norm smogu, 

•	prognozowanych opadów, 

•	zbliżenia użytkownika do ulubionego miejsca na odległość <300 m. 

•	Wykorzystuje usługi Expo Notifications lub Firebase Cloud Messaging (FCM). 

 

⸻ 

 

5. Moduł geolokalizacji i nawigacji 

•	Realizuje pobieranie bieżącej lokalizacji użytkownika z GPS oraz obliczanie odległości do punktów z listy atrakcji i ulubionych miejsc. 

•	Integracja z Google Maps Directions API umożliwia uruchomienie nawigacji z poziomu aplikacji. 

•	Dane o lokalizacji są również wykorzystywane do wywoływania powiadomień kontekstowych. 

 

⸻ 

 

6. Moduł integracji z API zewnętrznymi 

•	Zapewnia komunikację z usługami open-source i publicznymi API: 

•	OpenWeatherMap – pogoda, 

•	IQAir – jakość powietrza, 

•	NBP API – kursy walut, 

•	OpenTripMap / Google Places API – atrakcje turystyczne, gastronomia, 

•	Google Maps Directions API – trasy i nawigacja. 

•	Dane są okresowo odświeżane i przechowywane w pamięci podręcznej serwera w celu optymalizacji wydajności. 

 

System w całości tworzy nowoczesną architekturę klient–serwer, w której: 

•	warstwa mobilna zapewnia wygodny interfejs i doświadczenie użytkownika, 

•	warstwa serwerowa przetwarza dane i komunikuje się z API, 

•	baza danych MySQL gwarantuje trwałość i integralność informacji. 

 

3. Wymagania systemowe 

3.1. Wymagania funkcjonalne 

Tabela przedstawiająca wszystkie funkcje systemu: 

ID 

Nazwa funkcji 

Opis działania 

Priorytet 

F1 

Rejestracja użytkownika 

Użytkownik może utworzyć konto 

Wysoki 

3.2. Wymagania niefunkcjonalne 

Opis wymagań dotyczących jakości systemu: 

ID 

Nazwa 

Opis 

Kategoria 

N1 

Wydajność 

Czas odpowiedzi systemu ≤ 2 s 

Wydajność 

4. Diagramy UML 

4.1. Diagram przypadków użycia 

Wstaw diagram przedstawiający interakcje między użytkownikiem a systemem. 

4.2. Diagram klas 

Przedstaw strukturę logiczną systemu – główne klasy, atrybuty, relacje. 

5. Projekt bazy danych 

Model ERD (Entity-Relationship Diagram), opis tabel i relacji, klucze główne, obce, typy danych. 

6. Architektura systemu 

Opis wzajemnych powiązań między modułami aplikacji oraz schemat logiczny przepływu danych. 

7. Plan realizacji projektu 

Etap 

Opis 

Termin 

Osoba odpowiedzialna 

1 

Analiza wymagań 

 

 

8. Wnioski i możliwe rozszerzenia 

Opis potencjalnych funkcjonalności dodatkowych lub usprawnień, które mogą zostać dodane po ukończeniu projektu. 

9. Źródła 

Lista źródeł i materiałów wykorzystanych w projekcie (np. dokumentacja API NBP, dokumentacja technologii, literatura). 
