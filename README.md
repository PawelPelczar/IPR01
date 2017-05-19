# IPR01
Wstępne, próbne repozytorium dla projektu inżynierskiego PSI

## Członkowie
* Paweł Pelczar
* Dawid Twardowski
* Michał Szczepanowski
* Mikołaj Dzik
* Mateusz Zwolanowski


# Cele projektu - stratyfikacja: 
1. Minimum: Planowanie maksymalnej liczby zadań przy spełnianiu norm prawa transportowego, prawa pracy i z uwzględnieniem wyszkolenia kierowców w danym typie taboru
2. Miarą jakości algorytmu będzie możliwość minimalizowania nadgodzin i niedogodzin w danym, określonym z góry, niektóryszym, niż dwa tygodnie i nie dłuższym, niż kwartał okresie rozliczeniowym.
3. Nadgodziny mogą pojawiać się w planie dziennym, nigdy w planie miesięcznym.
4. Głównym celem projektu nie jest zaplanowanie 100% zadań, a nie zaplanowanie pracownikowi 100% jego nominału
5. Cechy dodatkowe:
  5.1. Metryki:
   5.1.1 Uwzględnianie preferencji osobniczych w ocenie jakości planu.
   5.1.2 Niedogodziny zaplanowane
   5.1.3 Procent zaplanowanych zadań
   5.1.4 Post-factum- wynikłe nadgodziny
     

6. Optymalizacja kwartalna - pozwoli na zamianę nadgodziny wypracowanych w jednym miesiącu na wolne w innym w ramach jednego kwartału - godzina za godzinę - zamiast na wypłacenie należności za pracę po godzinach. Jest to jednak cel dodatkowy, na razie nie kompensujemy nadgodzin.
7. Półetatowcy i inni pracownicy niezatrudnieni na umowę o pracę - ich zadań nie można planowań w rozliczeniu miesięcznym. Jeżeli mimo wszystko chcemy zapełnić nimi jakąś lukę już w wyprzedzeniem, to w dniu zgłoszonym przez pracownika nie planujemy nikogo na dane zadanie, a pracownik na np. połowę etatu, czy umowę-zlecenie jest o tym informowany z parodniowym wyprzedzeniem.


### Guidelines:
1. Lepiej opłacić nadgodziny, niż stracić kilometry - jeśli mamy do wyboru tylko jednego człowieka z 4-godzinowym nominałem i 10-godzinną trasę to przesuwamy go na 10h i płącimy.
2. Optymalizujemy nieprzydzielone zadania pod wzlgędem
   2.1 Małej częstotliwości kursu
   2.2 Kilometrażu
   2.3 Istotności zadania
3. Miesiąc optymalizujemy pod względem procentu zaplanowanych zadań. Dzień, z kolei, pod względem nad- i niedzogodzin.
4. Pierwsza połowa miesiąca ma być stała, resztę można replanować (nie jestem pewny kształtu, brzmienia, i znaczenia tego punku - dopytać)

### Implementacja:
1. Produktem końcowym projektu ma być biblioteka napisana w języku C# w standardzie .net.
2. Jeśli okaże się to pożyteczne biblioteka stworzona zostanie w architekturze rozproszonej. W chwili obecnej użyteczny wydaje się następujący model architektury:
   2.1. Jeden, główny komputer z dostępem do bazy danych prześle model danych poszczególnym jednostkom obliczeniowym, które zajmą się próbkowaniem przestrzeni rozwiązań.
   2.2. Próbkowanie może być ograniczone z góry:
     2.2.1 Czasem operacji
     2.2.2 Liczbą wykonanych planów
   2.3. Próbowanie może być ograniczone z dołu:
    2.3.1 Czasem operacji
    2.3.2 Liczbą wykonanych planów
    2.3.3 Wartością metryk dla rozwiązania
   2.4. Spośród uzyskanych rozwiązań jednostka obliczeniowa wybierze pewną liczbę rozwiązań, którą zwróci do komputera     wysyłającego żądanie.
   2.5. Komputer agraguje te rozwiązania, zapisuje je i przedstawia czynnikowi ludzkiemu do wyboru.
3. Kod musi być czysty, przejrzysty, zgodny ze standardem.
