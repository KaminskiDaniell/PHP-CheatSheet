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