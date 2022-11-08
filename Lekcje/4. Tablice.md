## Tablice

Tablica w języku PHP to w zasadzie uporządkowana mapa. Mapa jest typem, który przypisuje wartości do kluczy. Ten typ jest zoptymalizowany pod wiele różnych użyć:
- może być tablicą.
- listą (wektory),
- tablicą hashy,
- słownikiem,
- kolekcją
- kolejką,
- i wiele innych.
Wartościami tablicy mogą być inne tablice. Dzięki temu rozwiązaniu możemy tworzyć wielowymiarowe tablice

```php
$fruits = array("Jabłko", "Pomarańcz", "Banan", "Granat");


/* 
    Krótsza forma utworzenia tablicy
*/

$fruits = ["Jabłko", "Pomarańcz", "Banan"];

foreach ($fruits as $fruit) {
    var_dump($fruit);
}

/* 
    Wynik: 

    string(6) "Jabłko"     // typ string o długości 6 znaków
    string(9) "Pomarańcz"  // typ string o długości 9 znaków
    string(5) "Banan"      // typ string o długości 5 znaków

*/      
```

## Tablice asocjacyjne

Tablice asocjacyjne to takie, w których klucze mogą być ciągami znaków zamiast cyfr np. "owoc1" zamiast "1"

```php
<?php 
// Aby wypisać wszystkie wartości z tablicy asocjacyjnej, należy użyć pętli foreach w sposób podany poniżej:

$persons = [
  "Piotr" => "51", 
  "Jakub" => "25", 
  "Bartosz"=> "13.5"  
];

foreach ($persons as $name => $age) {
  echo "Mam na imię $name, mam $age lat.";
  echo "<br>";
}

/* 
    Wyjście: 

    Mam na imię Piotr, mam 51 lat.
    Mam na imię Jakub, mam 25 lat.
    Mam na imię Bartosz, mam 13.5 lat.

*/  
```
