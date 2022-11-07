# Zmienne i ich typy

PHP wspiera 7 podstawowych typów zmiennych.

**Podstawowe typy** **_boolean_**, **_integer_**, **_float_**, & **_string_**.

**Typy związkowes:** **_array_**.

**Specjalne typy:** **_NULL_**.

Data Types | Description
------------ | -------------
`boolean` | Wyrażenie boolean może przyjmować tylko wartość TRUE lub FALSE
`integer` | Liczba cakowita to numer ze zbioru liczb ℤ = {..., -2, -1, 0, 1, 2, ...}.
`float` | Liczby zmiennoprzecinkowe.
`string` | Ciąg znaków. 
`array` | Tablica wiele wartości zapisanych w jednej zmiennej An array in PHP is actually an ordered map. A map is a type that associates values to keys.
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


  echo gettype($bool);   // wyświetla:  boolean
  echo gettype($int);   // wyświetla:  interger
  echo gettype($float);  // wyświetla:  double
  echo gettype($string);    // wyświetla:  string
  echo gettype($array);   // wyświetla:  array
  echo gettype($null);   // wyświetla:  NULL

```
