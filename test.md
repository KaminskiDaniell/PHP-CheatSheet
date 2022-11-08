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
  - [Variable scope](https://github.com/gabriel-cacayan/php-cheatsheet#variable-scope)
  - [Variable variables](https://github.com/gabriel-cacayan/php-cheatsheet#variable-variables)
- [Constants](https://github.com/gabriel-cacayan/php-cheatsheet#constants)
  - [Magic constants](https://github.com/gabriel-cacayan/php-cheatsheet#magic-constants)
- [Expressions](https://github.com/gabriel-cacayan/php-cheatsheet#expressions)
- [Operators](https://github.com/gabriel-cacayan/php-cheatsheet#operators)
- [Control Structures](https://github.com/gabriel-cacayan/php-cheatsheet#control-structures)
  - [elseif/else if](https://github.com/gabriel-cacayan/php-cheatsheet#elseifelse-if)
  - [ternary operator](https://github.com/gabriel-cacayan/php-cheatsheet#ternary-operator)
  - [switch](https://github.com/gabriel-cacayan/php-cheatsheet#switch)
  - [Alternative syntax for control structures](https://github.com/gabriel-cacayan/php-cheatsheet#alternative-syntax-for-control-structures)
  - [for](https://github.com/gabriel-cacayan/php-cheatsheet#for)
  - [while](https://github.com/gabriel-cacayan/php-cheatsheet#while)
  - [do-while](https://github.com/gabriel-cacayan/php-cheatsheet#do-while)
  - [foreach](https://github.com/gabriel-cacayan/php-cheatsheet#foreach)
  - [break](https://github.com/gabriel-cacayan/php-cheatsheet#break)
  - [continue](https://github.com/gabriel-cacayan/php-cheatsheet#continue)
  - [include](https://github.com/gabriel-cacayan/php-cheatsheet#include)
  - [require](https://github.com/gabriel-cacayan/php-cheatsheet#require)
- [Arrays](https://github.com/gabriel-cacayan/php-cheatsheet#arrays)
  - [Associative Arrays](https://github.com/gabriel-cacayan/php-cheatsheet#associative-arrays)
- [Functions](https://github.com/gabriel-cacayan/php-cheatsheet#functions)
  - [Anonymous functions](https://github.com/gabriel-cacayan/php-cheatsheet#anonymous-functions)
  - [Arrow functions](https://github.com/gabriel-cacayan/php-cheatsheet#arrow-functions)
  - [Internal (built-in) functions](https://github.com/gabriel-cacayan/php-cheatsheet#internal-built-in-functions)
    - [Variable handling](https://github.com/gabriel-cacayan/php-cheatsheet#variable-handling)
    - [String Functions](https://github.com/gabriel-cacayan/php-cheatsheet#string-functions)
    - [Array Functions](https://github.com/gabriel-cacayan/php-cheatsheet#array-functions)


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

```php
<!DOCTYPE html>
<html>
    <head>
        <title>Example</title>
    </head>
    <body>
        /* 
            1.) Including navbar file 
            2.) Error message will occured when there is no file, but the web 
            will still execute.
        */
        <?php include "navbar.php"; ?>
        <?php
            echo "Hi, I'm a PHP script!";
        ?>

    </body>
</html>
```

### require

```php
<!DOCTYPE html>
<html>
    <head>
        <title>Example</title>
    </head>
    <body>
         /* 
            1.) Including navbar file 
            2.) Error message will occured when there is no file for whole page. 
        */
        <?php require "navbar.php"; ?>
        <?php
            echo "Hi, I'm a PHP script!";
        ?>

    </body>
</html>
```

<p align="right">
  <a href="https://github.com/gabriel-cacayan/php-cheatsheet#table-of-contents"> 
  <strong><span>&#8613;</span> Back To Top</strong>
  </a>
</p>

## Arrays

An array in PHP is actually an ordered map. A map is a type that associates values to keys. This type is optimized for several different uses; it can be treated as an array, list (vector), hash table (an implementation of a map), dictionary, collection, stack, queue, and probably more. As array values can be other arrays, trees and multidimensional arrays are also possible.

```php
// PHP Version: < 5.4
$fruits = array("Apple", "Orange", "Banana");


/* 
    Using the short array syntax

    PHP Version: >= 5.4
*/

$fruits = ["Apple", "Orange", "Banana"];

foreach ($fruits as $fruit) {
    var_dump($fruit);
    echo "<br>";
}

/* 
    Outputs: 

    string(5) "Apple"
    string(6) "Orange"
    string(6) "Banana"

*/      
```

### Associative Arrays

Associative arrays are arrays that use named keys that you assign to them.

```php
<?php 
// To loop through and print all the values of an associative array, you could use a foreach loop, like this:

$persons = [
  "Peter" => "35", 
  "Ben" => "37", 
  "Joe "=> "43"
];

foreach ($persons as $name => $age) {
  echo "My name is $name and my age is $age.";
  echo "<br>";
}

/* 
    Outputs: 

    My name is Peter and my age is 35
    My name is Ben and my age is 37
    My name is Joe and my age is 43

*/  
```

<p align="right">
  <a href="https://github.com/gabriel-cacayan/php-cheatsheet#table-of-contents"> 
  <strong><span>&#8613;</span> Back To Top</strong>
  </a>
</p>

## Functions

function with default arguments.

```php
<?php
  
    function add($a = 0, $b = 0) {
      return $a + $b;
    }


  echo add(10,5); // 15
  echo add(); // 0
```

### Anonymous functions

**_Anonymous functions_**, also known as **closures**, allow the creation of functions which have no specified name. They are most useful as the value of callback parameters, but they have many other uses.

```php
<?php
  
  $add = function($a = 0, $b = 0) {
      return $a + $b;
    };


echo $add(10,5);  // 15
?>
```

```php
<?php
  //global variable
  $ten = 10;

  $add = function($a) use ($ten){
        return $a + $ten;
      };


  echo $add(10); // 20  

?>
```

### Arrow Functions

Arrow functions were introduced in PHP 7.4 as a more concise syntax for anonymous functions.

```php
<?php

   $fn = fn($x, $y) => $x + $y;
 
  echo $fn(10,5); // 15
```

### Internal (built-in) functions

#### Variable handling 

Name | Description 
------------ | ------------- 
`empty` | Determine whether a variable is empty
`gettype` | Get the type of a variable
`is_array` | Finds whether a variable is an array
`is_bool`| Finds out whether a variable is a boolean
`is_double` | Alias of is_float
`is_float` | Finds whether the type of a variable is float
`is_int` | Find whether the type of a variable is integer
`is_integer` | Alias of is_int
`is_long` | Alias of is_int
`is_null` | Finds whether a variable is NULL
`is_numeric` | Finds whether a variable is a number or a numeric string
`is_object` | Finds whether a variable is an object
`is_real` | Alias of is_float
`is_scalar` | Finds whether a variable is a scalar
`is_string` | Find whether the type of a variable is string
`isset` | Determine if a variable is declared and is different than NULL
`print_r` | Prints human-readable information about a variable
`settype` | Set the type of a variable
`unset` | Unset a given variable
`var_dump` | Dumps information about a variable

<p align="right">
  <a href="https://www.php.net/manual/en/book.var.php" target="_blank"> 
  Reference</a>
</p>

##### Example:

```php
<?php

  $progLan = "PHP";
  $number = 1.25;
  $boolean = true;
  $arr = [1,2,3,4,5];
  $anInteger = 10;

  // Check whether the variable has value or none.
  var_dump(empty($progLan)) . "<br>"; // bool(false)
  var_dump(isset($progLan)) . "<br>"; // bool(true)

  // Check the Data type of the variable.
  echo gettype($progLan) . "<br>"; // string
  var_dump(is_array($arr)) . "<br>"; // bool(true)
  var_dump(is_bool($boolean)) . "<br>"; // bool(true)
  var_dump(is_double($number)) . "<br>"; // bool(true)
  var_dump(is_float($number)) . "<br>"; // bool(true)
  var_dump(is_int($number)) . "<br>"; // bool(false)
  var_dump(is_integer($anInteger)) . "<br>"; // bool(true)
  var_dump(is_long($number)) . "<br>"; // bool(false)
  var_dump(is_null($number)) . "<br>"; // bool(false)
  var_dump(is_numeric($number)) . "<br>"; // bool(true)
  var_dump(is_object($arr)) . "<br>"; // bool(false)
  var_dump(is_real($number)) . "<br>"; // bool(true)
  var_dump(is_scalar($progLan)) . "<br>"; // bool(true)
  var_dump(is_string($progLan)) . "<br>"; // bool(true)
  

  // Displaying variable's value
  print_r($number); // 1.25
  var_dump(10); // int(10)
```

#### String Functions 

Name | Description 
------------ | ------------- 
`echo()` | Output one or more strings
`htmlentities()` | Convert all applicable characters to HTML entities
`implode()` | Join array elements with a string
`join()` | Alias of implode
`lcfirst()` | Make a string's first character lowercase
`ltrim()` | Strip whitespace (or other characters) from the beginning of a string
`print()` | Output a string
`printf()` | Output a formatted string
`rtrim()` | Strip whitespace (or other characters) from the end of a string
`str_ireplace()` | Case-insensitive version of str_replace
`str_pad()` | Pad a string to a certain length with another string
`str_repeat()` | Repeat a string
`str_replace()` | Replace all occurrences of the search string with the replacement string
`str_shuffle()` | Randomly shuffles a string
`str_split()` | Convert a string to an array
`str_word_count()` | Return information about words used in a string
`strlen()` | Get string length
`strpbrk()` | Search a string for any of a set of characters
`strpos()` | Find the position of the first occurrence of a substring in a string
`strrchr()` | Find the last occurrence of a character in a string
`strrev()` | Reverse a string
`strripos()` | Find the position of the last occurrence of a case-insensitive substring in a string
`strrpos()` | Find the position of the last occurrence of a substring in a string
`strstr()` | Find the first occurrence of a string
`strtolower()` | Make a string lowercase
`strtoupper()` | Make a string uppercase
`substr()` | Return part of a string
`trim()` | Strip whitespace (or other characters) from the beginning and end of a string
`ucfirst()` | Make a string's first character uppercase
`ucwords()` | Uppercase the first character of each word in a string

<p align="right">
  <a href="https://www.php.net/manual/en/book.strings.php" target="_blank"> 
  Reference</a>
</p>

##### Example:

```php
<?php

  $progLan = "PHP";
  $script = "<script>Harmful script</script>";
  $arr = [1,2,3,4,5];
  $longText = "I love programming because, it is fun!";
  $vowels = ["a", "e", "i", "o", "u", "A", "E", "I", "O", "U"];

  printf("entities: %s <br>", htmlentities($script)); // &lt;script&gt;Harmful script&lt;/script&gt;
  printf("pad: %s <br>", str_pad("Hello", 10, "!!", STR_PAD_BOTH));  // !!Hello!!!
  printf("repeat: %s <br>", str_repeat("love", 5)); // lovelovelovelovelove
  print_r(str_split($progLan)); // Array ( [0] => P [1] => H [2] => P )
  echo "<br>";
  printf("search: %s <br>",strpbrk($longText, "f")); // fun!
  printf("pos: %d <br>",strpos($longText, "love")); // 2

  // Outputing string in different format.
  print ("print: Hello, World!") . "<br>"; // Hello, World!
  printf ("printf: %s <br>", $progLan); // The PHP is cool!

  // Finding the first occurrence of a string.
  printf("firstOcc: %s <br>",strstr($longText, "m")); // mming because, it is fun

  //  Finding the last occurrence of a string that is case sensitive and not.
  printf("lastiOcc: %d <br>",strripos($longText, "M")); // 14
  printf("lastOcc: %d <br>",strrpos($longText, "m")); // 14
  printf("lastOccu2: %s <br>",strrchr($longText, "m")); // ming because, it is fun!

  // Reverse or Shuffle the string
  printf("shuffle: %s <br>", str_shuffle($longText)); // random text
  printf("reverse: %s <br>", strrev($longText)); // !nuf si ti ,esuaceb gnimmargorp evol I

  // Slicing the string
  printf("slice: %s <br>",substr($longText, 2, 4)); // love

  // Returns a replaced word.
  printf("iReplace: %s <br>",str_ireplace("%body%", "black", "<body text=%BODY%>")); // <body text=black>
  printf("replace: %s <br>",str_replace($vowels, "", $longText)); //  lv prgrmmng bcs, t s fn!

  // Returns the length of a string.
  printf("length: %d <br>", strlen($longText)); // 38
  printf("word count: %d <br>", str_word_count($longText)); // 7

  // Changing the text to upper or lower case.
  printf("upperFirst: %s <br>" ,ucfirst($longText)); // I love programming because, it is fun!
  printf("upperWords: %s <br>", ucwords($longText)); // I Love Programming Because, It Is Fun!
  printf("toLower: %s <br>", strtolower($longText)); // i love programming because, it is fun!
  printf("toUpper: %s <br>", strtoupper($longText)); // I LOVE PROGRAMMING BECAUSE, IT IS FUN!

  // Returns removed whitespaces
  printf("leftTrim: %s <br>", ltrim("             Hello, World!")); // Hello, World!
  printf("rightTrim: %s <br>", rtrim("Text with whitespace!              ")); // Text with whitespace!
  printf("trim: %s <br>", trim(" Text with whitespace.       ")); // Text with whitespace.
```

#### Array Functions 

Name | Description 
------------ | ------------- 
`array_filter()` | Filters elements of an array using a callback function
`array_map()` | Applies the callback to the elements of the given arrays
`array_reduce()` | Iteratively reduce the array to a single value using a callback function
`array_reverse()` | Return an array with elements in reverse order
`array_push()` | Push one or more elements onto the end of array
`array_pop()` | Pop the element off the end of array
`array_shift()` | Shift an element off the beginning of array
`array_unshift()` | Prepend one or more elements to the beginning of an array
`count()` | Count all elements in an array, or something in an object
`array_replace()` | Replaces elements from passed arrays into the first array
`array_slice()` | Extract a slice of the array
`array_splice()` | Remove a portion of the array and replace it with something else
`array_search()` | Searches the array for a given value and returns the first corresponding key if successful
`array_key_exists()` | Checks if the given key or index exists in the array

<p align="right">
  <a href="https://www.php.net/manual/en/book.array.php" target="_blank"> 
  Reference</a>
</p>

##### Example:

```php
  <?php

  $arr = [1,2,3,4,5,6,7,8,9,10];


  function Even($var) {
    return $var%2 == 0;
  }

  function Odd($var) {
    return $var%2 == 1;
  }

  function sum($carry, $item) {
      $carry += $item;
      return $carry;
  }

  function squre($var){
    return $var * $var;
  }

  // filtering elements
  print_r(array_filter($arr, "Even")); // Array ( [1] => 2 [3] => 4 [5] => 6 [7] => 8 [9] => 10 )
  echo "<br>";
  print_r(array_filter($arr, "Odd"));  // Array ( [0] => 1 [2] => 3 [4] => 5 [6] => 7 [8] => 9 )
  echo "<br>";

  // modifying array elements
  print_r(array_map("squre", $arr)); // Array ( [0] => 1 [1] => 4 [2] => 9 [3] => 16 [4] => 25 [5] => 36 [6] => 49 [7] => 64 [8] => 81 [9] => 100 )
  echo "<br>";

  // reduce
  var_dump(array_reduce($arr, "sum")); // int(55)
  echo "<br>";

  // Reversing an array
  print_r(array_reverse($arr)); // Array ( [0] => 10 [1] => 9 [2] => 8 [3] => 7 [4] => 6 [5] => 5 [6] => 4 [7] => 3 [8] => 2 [9] => 1 )
  echo "<br>";

  // Adding element to the end of array
  array_push($arr, 11); 
  print_r($arr); 
  echo "<br>";

  // Removing element to the end of array
  array_pop($arr);
  print_r($arr);
  echo "<br>";

  // Adding element to the start of array
  array_unshift($arr, 0);
  print_r($arr);
  echo "<br>";

  // Removing element to the start of array
  array_shift($arr);
  print_r($arr); 
  echo "<br>";

  // Count of element in the array
  var_dump(count($arr)); // int(10)
```

<p align="right">
  <a href="https://github.com/gabriel-cacayan/php-cheatsheet#table-of-contents"> 
  <strong><span>&#8613;</span> Back To Top</strong>
  </a>
</p>
