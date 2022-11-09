# Spis treści
- [Wstęp](https://github.com/gabriel-cacayan/php-cheatsheet#table-of-contents)
  - [Typy instalacji](https://github.com/gabriel-cacayan/php-cheatsheet#types-of-installation)
- [Podstawowa składnia](https://github.com/gabriel-cacayan/php-cheatsheet#basic-syntax)
  - [Tagi PHP](https://github.com/gabriel-cacayan/php-cheatsheet#php-tags)
  - [Opuszczanie znaczników HTML](https://github.com/gabriel-cacayan/php-cheatsheet#escaping-from-html)
  - [Separacja instrukcji](https://github.com/gabriel-cacayan/php-cheatsheet#instruction-separation)
  - [Komentarze](https://github.com/gabriel-cacayan/php-cheatsheet#comments)
- [Typy zmiennych](https://github.com/gabriel-cacayan/php-cheatsheet#data-types)
- [Zmienne](https://github.com/gabriel-cacayan/php-cheatsheet#variables)
  - [Predefiniowane zmienne](https://github.com/gabriel-cacayan/php-cheatsheet#predefined-variables)
  - [Zakres zmiennych](https://github.com/gabriel-cacayan/php-cheatsheet#variable-scope)
  - [Podwójne zmienne](https://github.com/gabriel-cacayan/php-cheatsheet#variable-variables)
- [Stałe](https://github.com/gabriel-cacayan/php-cheatsheet#constants)
  - [Magiczne stałe](https://github.com/gabriel-cacayan/php-cheatsheet#magic-constants)
- [Wyrażenia](https://github.com/gabriel-cacayan/php-cheatsheet#expressions)
- [Operatory](https://github.com/gabriel-cacayan/php-cheatsheet#operators)
- [Instrukcje warunkowe](https://github.com/gabriel-cacayan/php-cheatsheet#control-structures)
  - [if, else, elsif](https://github.com/gabriel-cacayan/php-cheatsheet#elseifelse-if)
  - [if jednolinijowy](https://github.com/gabriel-cacayan/php-cheatsheet#ternary-operator)
  - [switch](https://github.com/gabriel-cacayan/php-cheatsheet#switch)
  - [Alternatywna składnia dla instrukcji warunkowej](https://github.com/gabriel-cacayan/php-cheatsheet#alternative-syntax-for-control-structures)
  - [for](https://github.com/gabriel-cacayan/php-cheatsheet#for)
  - [while](https://github.com/gabriel-cacayan/php-cheatsheet#while)
  - [do while](https://github.com/gabriel-cacayan/php-cheatsheet#do-while)
  - [foreach](https://github.com/gabriel-cacayan/php-cheatsheet#foreach)
  - [break](https://github.com/gabriel-cacayan/php-cheatsheet#break)
  - [continue](https://github.com/gabriel-cacayan/php-cheatsheet#continue)
  - [include](https://github.com/gabriel-cacayan/php-cheatsheet#include)
  - [require](https://github.com/gabriel-cacayan/php-cheatsheet#require)
- [Tablice](https://github.com/gabriel-cacayan/php-cheatsheet#arrays)
  - [Tablice asocjacyjne](https://github.com/gabriel-cacayan/php-cheatsheet#associative-arrays)
- [Funkcje](https://github.com/gabriel-cacayan/php-cheatsheet#functions)
  - [Wbudowane funkcje](https://github.com/gabriel-cacayan/php-cheatsheet#internal-built-in-functions)
    - [Praca na zmiennych](https://github.com/gabriel-cacayan/php-cheatsheet#variable-handling)
    - [Funkcje do pracy z ciągami znaków ](https://github.com/gabriel-cacayan/php-cheatsheet#string-functions)


**PHP** (skrót od PHP: Hypertext Preprocessor) jest szeroko stosowanym językiem skryptowym ogólnego przeznaczenia o otwartym kodzie źródłowym, który szczególnie nadaje się do tworzenia stron internetowych i może być osadzony w HTML.

> **Przykład:** Przykład wprowadzający
```php
<!DOCTYPE html>
<html>
    <head>
        <title>Przykładowa strona</title>
    </head>
    <body>

        <?php
            echo "To moja pierwsza strona w języku PHP!";
        ?>

    </body>
</html>
```

Powyższy kod, wstawia do znacznika `<body>` napis "To mój pierwszy skrypt". Najważniejsze zasady, wynikające z niego to:
- Aby skrypt się wykonał musi być on umieszczony pomiędzy znacznikami `<?php`, który wskazuje kompilatorowi gdzie skrypt się zaczyna i znacznik `?>` wskazujący na zakończenie skryptu.
- Każda linijka kończy się znakiem średnika (wyjątkiem są funkcje i pętle, o których będzie później) 
- Polecenie `echo` służy do wyświetlania tekstu.

## Czego potrzebujesz do uruchomienia PHP?
Aby rozpocząć pracę z programowaniem w języku PHP należy posiadać na swoim komputerze jedną z instancji:
- [**LAMP**](https://ubuntu.com/server/docs/lamp-applications) (Linux, Apache, MySQL, PHP)
- [**MAMP**](https://www.mamp.info/en/windows/) (Mac, Apache, MySQL, PHP)
- [**WAMP**](https://www.wampserver.com/en/) (Windows, Apache, MySQL, PHP)
- [**XAMPP**](https://www.apachefriends.org/pl/index.html) (Apache, MariaDB, PHP, Perl)


## Podstawowa składnia  

### Tagi PHP 

Aby utworzyć stronę, którą będzie obsługiwał interpreter PHP należy dodać rozszerzenie **.php** do wybranego pliku. 

**Ważne! Plik .php obsługuje znaczniki HTML, co oznacza, że w tych plikach można zarówno tworzyć skrypty, jak i budować siatkę strony.**

Kiedy PHP parsuje plik, szuka tagów otwierających i zamykających skrypt PHP, które wyglądają następująco: znacznik otwierający `<?php`, znacznik zamykający `?>`.

```php
<?php echo "Standardowy tag PHP"; ?>

<?= "Skrócony tag PHP, za pomocą którego można wyświetlać tekst na stronie"; ?>
```

Jeżeli plik zawiera skrypt w języku PHP, zaleca się nie domykanie skryptu na końcu pliku. Ochroni to przed potencjalnymi białymi znakami, które mogę znajdować się na końcu pliku za znacznikami zamykającymi, które mogą powodować niepożądane efekty, ponieważ PHP rozpocznie próbę wyświetlania treści, której nie ma. 

```php
<?php
echo "Mój pierwszy tekst napisany w PHP";

// ... dalszy kod

echo "Ostatnia linijka kodu";

// skrypt kończy działanie tutaj bez znacznika zamykającego
```

### Opuszczanie znaczników HTML 

Wszystko poza parą otwierającego oraz zamykającego znacznika jest ignorowane przez parser PHP, który pozwala na zmiksowaną treść, co oznacza, że w plikach PHP mogą znajdować się elementy HTML np. do tworzenia szablonów.

```php
<p>Ten znacznik jest zignorowany przez PHP i wyświetlany przez przeglądarkę.</p>

<?php echo 'Podczas kiedy ta linijka jest parsowana przez PHP.'; ?>

<p>I to również jest ignorowane przez PHP i wyświetlane przez przeglądarkę.</p>


// Przykład #1 Zaawansowane opuszczanie znaczników z wykorzystaniem wyrażeń
<?php if ($expression == true): ?>

  // Treść wypisana tutaj pojawi się, jeżeli wyrażenie będzie prawdziwe.

<?php else: ?>

  // W innym przypadku pojawi się treść stąd.

<?php endif; ?>
```

### Separacja instrukcji

Tak samo jak w językach C, czy Perl (w którym napisany jest język PHP), PHP również wymaga, aby na końcu każdej linijki instrukcji znajdował się średnik. Znacznik zamykający skrypt PHP automatycznie kończy też linijkę niewidzialnym średnikiem, co oznacza, że nie musimy wstawiać średnika, jeżeli polecenie jest jednolinijkowe.

```php
<?php echo "Ala ma kota"; ?>

Brak nowej linii

<?= "Tutaj już jest nowa linia" ?>
```
### Komentarze

PHP wspiera komentarze w takiej samej składni jak 'C' czy 'C++'. Na przykład: 

```php
<?php
    echo 'To jest test'; // To jest jednolinijkowy komentarz
    /* Tutaj mamy wieloliniowy komentarz,
       dalszy ciąg komentarza znajduje się tutaj
       i kolejna linijka */
    echo 'Drugi test';

    echo 'Trzeci test'; # Jedno liniowy komentarz
```

# Zmienne i ich typy

PHP wspiera 7 podstawowych typów zmiennych.

**Podstawowe typy:** **_boolean_**, **_integer_**, **_float_** i **_string_**.

**Typy związkowes:** **_array_**.

**Specjalne typy:** **_NULL_**.

Data Types | Description
------------ | -------------
`boolean` | Wyrażenie boolean może przyjmować tylko wartość TRUE lub FALSE
`integer` | Liczba cakowita to numer ze zbioru liczb Naturalnych = {..., -2, -1, 0, 1, 2, ...}.
`float` | Liczby zmiennoprzecinkowe.
`string` | Ciąg znaków. 
`array` | Tablica wiele wartości zapisanych w jednej zmiennej. Tablica w PHP zachowuje się jak uporządkowana mapa, w której do wartości przypisujemy klucze.
`NUll` | Specjalny typ NULL, którego wartość reprezentuje zmienną bez wartości. NULL może być jedynym typem tej zmiennej.

> **Notatka:** Aby sprawdzić typ i wartość zmiennej użyj funkcji `var_dump()`.
> Aby otrzymać czytelną reprezentację typu np. dla debugowania użyj funkcji `gettype()`. Jeżeli chcesz sprawdzić typ danej funkcji, nie używaj `gettype()`, ale funkcji `is_type`. Przykłady:

```php
<?php
  $bool = TRUE;                 // boolean
  $int = 12;                    // integer
  $float = 4.1;                 // float
  $string  = "foo";             // string
  $array = ["Apple", "Banana"]; // array
  $null;                        // null


  echo gettype($bool);          // wyświetla:  boolean
  echo gettype($int);           // wyświetla:  interger
  echo gettype($float);         // wyświetla:  double
  echo gettype($string);        // wyświetla:  string
  echo gettype($array);         // wyświetla:  array
  echo gettype($null);          // wyświetla:  NULL

```

## Zmienne

**_Zmienne_** w PHP reprezentowane są przy użyciu znaku $, po którym następuje nazwa zmiennej. Nazwy zmiennych są wrażliwe na wielkość liter.

> **WAŻNE:** W PHP funkcjonuje konwencja nazewnicza camelCase. Oznacza to, że w przypadku zmiennych, które zawierają w sobie jeden wyraz nazwa jest pisana z małej litery np. `$age`, natomiast w przypadku wielowyrazowych zmiennych każda pierwsza litera drugiego i następnych wyrazów pisana jest dużym znakiem, czyli: `$rowNumberFromDatabase`

```php
<?php
$var = 'Jakub';
$Var = 'Złotek';
echo "$var, $Var";             // wyświetli: "Jakub, Złotek"

$4site = 'Lorem Ipsum';        // BŁĄD! Zmienna zaczyna się od cyfry
$_4site = 'Dolor sit amet';    // POPRAWNIE! Zaczyna się od podkreślenia
$täyte = 'mansikka';           // POPRAWNIE! 'ä' jest rozszerzeniem ASCII 228.
?>

<?php
// Łączenie ciągów znaków przy pomocy cudzysłowiów.
$firstName = "Piotr";
$lastName = "Gawryl";
echo "$firstName $lastName";       // wyświetli: Piotr Gawryl 
  
// Łączenie ciągów znaków przy pomocy kropki.
echo $firstName . " " . $lastName; // wyświetli: Piotr Gawryl   
```

### Predefiniowane zmienne

PHP zapewnia dużą ilość **_predefiniowanych zmiennych_** dla skryptów. Zmienne te reprezentują wszystko począwszy od zmiennych zewnętrznych, po wbudowane zmienne środowiskowe, ostatnie komunikaty o błędach, czy ostatnio pobrane nagłówki.

Zmienne superglobalne | Opis
------------          | -------------
`$GLOBALS`            | Odwołuje się do wszystkich zmiennych dostępnych globalnie
`$_SERVER`            | Informacje o serwerze i środowisku, w którym skrypt jest wykonywany
`$_GET`               | Dane przekazywane przez protokół HTTP GET
`$_POST`              | Dane przekazywane przez protokół HTTP POST
`$_FILES`             | Dane przekazywane przez protokuł HTTP podczas przesyłania plików na serwer
`$_REQUEST`           | Zmienne żądania HTTP
`$_SESSION`           | Zmienna sesyjna
`$_ENV`               | Zmienna środowiskowa
`$_COOKIE`            | Zmienna odpowiedzialna za obsługę ciasteczek w przeglądarce


### Zakres zmiennych

Zakres zmiennej to kontekst, w którym jest ona zdefiniowana. W większości przypadków wszystkie zmienne PHP mają tylko jeden zakres.

**Zmienne lokalne:** Zmienne zadeklarowane wewnątrz funkcji nazywane są zmiennymi _lokalnymi_ do tej funkcji i mają swój zakres tylko w tej konkretnej funkcji.

```php
<?php
 function localVariable() {
    $variable = "Jesten lokalną zmienną";
    return $variable;
}

echo localVariable(); // wyświetli: Jestem lokalną zmienną
```
**Zmienne globalne:** Zmienne zadeklarowane poza funkcją nazywane są _zmiennymi globalnymi_.

```php
<?php
    global $globalVariable;
    $globalVariable= "Jestem zmienną globalną!";

  function globalVariable() {
    global $globalVariable;
    return $globalVariable;
  }

echo globalVariable(); // wyświetli: Jestem zmienną globalną!
```

**Zmienne statyczne:** Cechą charakterystyczną PHP jest usuwanie zmiennej, po zakończeniu jej wykonywania i zwolnieniu pamięci. Czasami jednak potrzebujemy przechowywać zmienne nawet po zakończeniu wykonywania funkcji. Aby to zrobić używamy słowa kluczowego static i zmienne są wtedy nazywane _statycznymi_.

```php
<?php
  // Bez słowa static
  function staticKeyword() {
      $count = 1;
      echo $count . "<br>";
      $count = $count + 1;

  }

  staticKeyword(); // 1
  staticKeyword(); // 1
  staticKeyword(); // 1
  staticKeyword(); // 1
  staticKeyword(); // 1

  // Ze słowem static
  function staticKeyword() {
     static $count = 1;
      echo $count . "<br>";
      $count = $count + 1;

  }

  staticKeyword(); // 1
  staticKeyword(); // 2
  staticKeyword(); // 3
  staticKeyword(); // 4
  staticKeyword(); // 5
```

### Podwójne zmienne

Czasami wygodnie jest móc mieć zmienne nazwy zmiennych. To znaczy, nazwa zmiennej, która może być ustawiona i używana dynamicznie. Zwykłą zmienną ustawia się za pomocą instrukcji takiej jak:

```php
<?php
  $name = "Daniel Kamiński";
  $fullName = "name";

  echo $fullName . "<br>";  // wyświetli: name
  echo $$fullName;          // wyświetli: Daniel Kamiński
```


## Stałe

**_Stała_** jest identyfikatorem (nazwą) dla prostej wartości. Jak sama nazwa wskazuje, wartość ta nie może się zmienić podczas wykonywania skryptu. Stała domyślnie rozróżnia wielkość liter. Zgodnie z konwencją, identyfikatory stałych są zawsze pisane wielkimi literami.

```php
<?php

  // Poprawne nazwy zmiennych
  define("FOO",     "something");
  define("FOO2",    "something else");
  define("FOO_BAR", "something more");

  // Niepoprawna nazwa zmiennej
  define("2FOO",    "something");

  // Ta nazwa, jest poprawna, ale należy jej unikać:
  // PHP może pewnego dnia dostarczyć magiczną stałą.
  // która nadpiszę taką stała, co poskutkuje zepsuciem skryptu
  define("__FOO__", "something"); 
```

### Stałe magiczne

Istnieje 8 **_magicznych stałych_**, które zmieniają się w zależności od tego, gdzie są używane. Na przykład, wartość __LINE__ zależy od linii, w której jest użyta w twoim skrypcie. Wszystkie te "magiczne" stałe są rozwiązywane w czasie kompilacji, w przeciwieństwie do zwykłych stałych, które są rozwiązywane w czasie wykonywania. Te specjalne stałe nie rozróżniają wielkości liter i są następujące:

Magic constants | Description
------------    | -------------
`__LINE__`      | Bieżący numer linii pliku.
`__FILE__`      | Pełna ścieżka i nazwa pliku. Jeśli użyto go wewnątrz include, zwracana jest nazwa dołączonego pliku.
`__DIR__`       | Katalog pliku. Jeśli użyto wewnątrz include, to zwracany jest katalog dołączonego pliku. Jest to odpowiednik dirname(__FILE__). Nazwa tego katalogu nie posiada końcowego ukośnika, chyba że jest to katalog główny.
`__FUNCTION__`  | Nazwa funkcji.
`__CLASS__`     | Nazwa klasy. Nazwa klasy zawiera również przestrzeń nazw, w której została zadeklarowana np. DKaminski\TerrainGames.
`__METHOD__`    | Nazwa metody klasy.
`__NAMESPACE__` | Nazwa bieżącej przestrzeni nazw.


## Wyrażenia
**_Wyrażenia_**. Najprostszy sposób na zdefiniowanie wyrażenia to "wszystko co ma wartość".

```php
<?php
  $a = 12;
  $b = 47;

  $total = $a + $b;
  echo $total; // 59
```


## Operatory
Arytmetyczne     | Przypisania                    | Porównania              | Logiczne 
------------     | -------------                  | -------------           | -------------
Dodawania `+`    | Dodanie do zmiennej `+=`       | Równe `==`              | I `AND`
Odejmowania `-`  | Odjęcie od zmiennej `-=`       | Identyczne* `===`       | LUB `OR`
Mnożenia `*`     | Pomnożenie przez zmienną  `*=` | Nie równe `!=`          | Xor `XOR`
Dzielenia `/`    | Podzielenie przez zmienną `/=` | Większe lub równe `>=`  | NIE `!`
Modulo `%`       | Modulo assignment `%=`         | Nie identyczne `!==`    | ORAZ `&&`
Potęgowania `**` | Konkatenacja stringów `.=`     | Mniejsze niż `<`        | LUB `II`
Negacji `-`      |                                | Większe niż `>`         |
|                |                                | Mniejsze lub równe `<=` | 
|                |                                | Większe lub równe `>=`  |


> **Ważne:** W operatorze logicznym używamy znaków ||, zostały one zamienione na II, aby nie zepsuć tabeli. 


## Instrukcje warunkowe


### if, else, elseif
IF to najprostsza instrukcja warunkowa używana w języku PHP. Służy ona do sprawdzenia "CZY" dany warunek jest spełniony

```php
<?php
  $a = 5;
  $b = 10;

  if ($a > $b) {
    echo "A jest większe niż B";
  } elseif ($a < $b) {
    echo "B jest większe niż A";
  }  else {
    echo "Niepoprawne dane!";
  }

  // Wyjście: B jest większe niż A
```

### if jednolinijkowy
W języku PHP istnieje możliwość używania instrukcji warunkowej w IF w jednej linii kodu. Wtedy jej struktura wygląda następująco:
`warunek ? działanie jeśli prawda : działanie jeżeli fałsz`. Np.
```php
<?php
   $a = 5;
   $b = 10;

  echo $a > $b ? "A jest większe niż B": "B jest większe niż A";

  // Wyjście: B jest większe niż A
```

Prostsze rozwiązanie, prawda?

### switch
```php
<?php

    $i = 2;

    switch ($i) {
      case 0:
          echo "I jest równe 0";
          break;
      case 1:
          echo "I jest równe 1";
          break;
      case 2:
          echo "I jest równe 2";
          break;
  }

   // Wyjście: I jest równe 2
```

### Alternatywna składnia dla instrukcji warunkowej
PHP oferuje alternatywną formę składni dla instrukcji warunkowych, czy pętli. W każdym przypadku podstawowa forma się nie zmienia. Zamiast znaków `{}` używamy `:` oraz instrukcji kończącej czyli `endif;` lub `endwhile;` lub `endfor;` lub `endforeach;` lub `endswitch;`. Jest to forma często używana podczas wyświetlania dużej ilości kodu HTML, ponieważ zwiększa przejrzystość kodu

```php
<?php
  
  $a = 5;

  if ($a == 5):
      echo "A jest równe 5";
  elseif ($a == 6):
      echo "A jest równe 6";
  else:
      echo "A nie równa się ani 5, ani 6";
  endif;

  // Wyjście: A jest równe 5
```

### Pętla for

Składnia pętli for wygląda następująco:
`for(deklaracja zmiennej ; wykonywanie pętli do momentu kiedy warunek się spełni ; zmiana wartości zmiennej po każdej iteracji) {}`. Np.

```php
<?php

  for ($a = 0; $a < 5; $a++) {
    echo $a . "<br>"; 
  }

  /*
  
    Wyjście:
    0
    1
    2
    3
    4
  
  */
```

### Pętla while

Składnia pętli while wygląda następująco:
`while(warunek do kiedy ma działać pętla) {}`. Np.

```php
<?php

  $a = 0;

  while($a < 5){
    echo $a . "<br>";
    $a++;
  }


   /*

    Wyjście:
    0
    1
    2
    3
    4
  
  */
```

### Pętla do while

Składnia pętli do while wygląda następująco:
`do {} while(warunek do kiedy ma działać pętla)`. Np.

```php
<?php

    $a = 0;
      
    do {
      echo $a . "<br>";
      $a++;
  } while ($a < 5);

  /*

    Wyjście:
    0
    1
    2
    3
    4
  
  */
```

### foreach 
Pętla foreach została stworzona w celu łatwiejszej iteracji po tabelach. Umożliwia ona szybsze przeglądanie danych zawartych w tabelach. Tak jak jest to opisane w poniżzym przykładzie

```php
<?php

  $array = [1,2,3,4,5];

  foreach($array as $value){
    echo $value; 
  }

  // Wyjście: 12345
```



### break
Polecenie `break` służy do "opuszczenia" pętli. Zazwyczaj używa się go w przypadku kiedy chcemy przerwać pętlę w momencie kiedy jakiś warunek się spełni.

```php
<?php
    for ($i = 0; $i < 5; $i++) {
      if ($i === 3) {
         break;
       }
       echo $i . "<br>";
    }

    /*

    Wyjście:
    0
    1
    2
  
  */
```

### continue

Polecenie `continue` działa podobnie do `break`. Pomija ono iterację pętli nie przerywając jej wykonywania. Przykład poniżej

```php
<?php
    for ($i = 0; $i < 5; $i++) {
      if ($i === 2) {
          continue;
      }
    echo $i . "<br>";
  }

   /*

    Wyjście:
    0
    1
    3
    4

  */
```

### include

Include to instrukcja, dzięki której możemy importować skrypty w PHP do naszego pliku.

>Struktura pliku index.php
```php
<!DOCTYPE html>
<html>
    <head>
        <title>Strona Include</title>
    </head>
    <body>
        <?php include "navbar.php"; ?>
        <?php
            echo "Tekst pod paskiem nawigacyjnym!";
        ?>
    </body>
</html>
```

>Struktura pliku navbar.php
```php
<?php
  <header>
    <a href="strona1.php">Strona 1</a>
    <a href="strona2.php">Strona 2</a>
    <a href="strona3.php">Strona 3</a>
  </header>
?>
```

Po otworzeniu strony w przeglądarce zostanie wyświetlona strona w postaci:
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Strona Include</title>
    </head>
    <body>
        <header>
            <a href="strona1.php">Strona 1</a>
            <a href="strona2.php">Strona 2</a>
            <a href="strona3.php">Strona 3</a>
        </header>
            Tekst pod paskiem nawigacyjnym!
    </body>
</html>
```


### require

Instrukcja require działa praktycznie tak samo jak instrukcja include. Jedyna różnica to zmiana nazwy instrukcji.

```php
<!DOCTYPE html>
<html>
    <head>
        <title>Strona require</title>
    </head>
    <body>
        <?php require "navbar.php"; ?>
        <?php
            echo "Strona używająca instrukcji require!";
        ?>

    </body>
</html>
```

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

## Funkcje

Funkcja to wydzielona część programu, która przetwarza argumenty i ewentualnie zwraca wartość, która następnie może być wykorzystana, jako argument w innych 
działaniach lub funkcjach. Funkcja może posiadać własne zmienne lokalne.


W funkcjach możemy zdefiniować wartości domyślne w przypadku, kiedy nie zostaną podane wszystkie parametry funkcji

```php
<?php
  
    function add($a = 0, $b = 0) {
      return $a + $b;
    }


  echo add(10,5);   // Wyjście: 15
  echo add();       // Wyjście: 0
```


### Wbudowane funkcje

#### Praca na zmiennych

Nazwa         | Opis 
------------  | ------------- 
`empty`       | Sprawdza, czy zmienna jest pusta.
`isset`       | Sprawdza czy zmienna jest zadeklarowana oraz czy jest różna od NULL
`print_r`     | Wyświetla czytelne informacje o zmiennej
`unset`       | Usuwa zmienną z pamięci
`var_dump`    | Wyświetla techniczne informacje o zmiennej


##### Przykład:

```php
<?php

  $progLan = "PHP";
  $number = 1.25;
  $boolean = true;
  $arr = [1,2,3,4,5];
  $anInteger = 10;

  // Sprawdza czy zmienna jest zadeklarowana z jakąś wartością.
  var_dump(empty($progLan)) . "<br>";    // bool(false) - zmienna $progLan nie jest pusta
  var_dump(isset($progLan)) . "<br>";    // bool(true) - zmienna $progLan jest zadeklarowana
  

  // Wyświetlanie wartości zmiennych
  print_r($number);    // 1.25
  var_dump(10);        // int(10)
```

#### Funkcje do pracy z ciągami znaków 

Nazwa           | Opis 
------------    | ------------- 
`echo()`        | Wyświetla ciąg znaków
`print()`       | Wyświetla ciąg znaków
`str_replace()` | Zamienia wszystkie wartości w podanym ciągu znaków
`strtolower()`  | Zamienia ciąg znaków na małe znaki
`strtoupper()`  | Zamienia ciąg znaków na duże znaki
`substr()`      | Zwraca część ciągu znaków


##### Przykład:

```php
<?php

  $progLan = "PHP";
  $arr = [1,2,3,4,5];
  $longText = "Lubię programować w PHP!";
  $vowels = ["p", "r", "o", "g", "r", "a", "m"];

  print ("Witaj świecie!") . "<br>";                                // Hello, World!

  // Wyszukwianie pierwszego przypadku
  print(substr($longText, 2, 4));                                   // programować

  // Zwraca podmieniony ciąg znaków
  print(str_replace($vowels, "", $longText));                       //  Lubię wć w PHP!!

  print(strtolower($longText));            // lubię programować w php!
  print(strtoupper($longText));            // LUBIĘ PROGRAMOWAĆ W PHP!
```
