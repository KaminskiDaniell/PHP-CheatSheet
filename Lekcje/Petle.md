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
