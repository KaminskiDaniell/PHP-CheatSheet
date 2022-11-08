# Pierwsza strona w PHP
Aby utworzyć stronę, którą będzie obsługiwał interpreter PHP należy dodać rozszerzenie **.php** do wybranego pliku. 

**Ważne! Plik .php obsługuje znaczniki HTML, co oznacza, że w tych plikach można zarówno tworzyć skrypty, jak i budować siatkę strony.**

```php
<!DOCTYPE html>
<html>
    <head>
        <title>Pierwsza strona w PHP</title>
    </head>
    <body>
        <?php
            echo "To mój pierwszy skrypt!";
        ?>
    </body>
</html>
```

Powyższy kod, wstawia do znacznika <body> napis "To mój pierwszy skrypt". Najważniejsze zasady, wynikające z niego to:
- Aby skrypt się wykonał musi być on umieszczony pomiędzy znacznikami `<?php`, który wskazuje kompilatorowi gdzie skrypt się zaczyna i znacznik `?>` wskazujący na zakończenie skryptu.
- Każda linijka kończy się znakiem średnika (wyjątkiem są funkcje i pętle, o których będzie później) 
- Polecenie `echo` służy do wyświetlania tekstu.
    
Wynikiem przedstawionego wyżej kodu będzie napis wyświetlony na stronie
![image](https://user-images.githubusercontent.com/27357868/196879365-994233c2-8231-4aee-9abb-4496a88bbfac.png)
