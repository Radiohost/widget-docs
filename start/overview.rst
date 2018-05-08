*******************
Instalacja widgetów
*******************

===========
Spis treści
===========

1. `Główny kod <#title.1.2>`_
2. `Popup <#title.1.3>`_
3. `iFrame <#title.1.4>`_
 - `Najważniejsze elementy konfiguracji iFrame-a <#title.1.4.1>`_
4. `Implementacja kodu html, css oraz js <#title.1.5>`_
 - `Początek <#title.1.5.1>`_
 - `HTML <#title.1.5.2>`_
 - `CSS <#title.1.5.3>`_
 - `JS <#title.1.5.4>`_
5. `Najczęstsze problemy <#title.1.6>`_
 - `Widget się nie ładuje <#title.1.6.1>`_
 - `$ / JQUERY is not defined <#title.1.6.2>`_
 - `MOMENT.js is not defined <#title.1.6.3>`_
 - `Niepoprawne wyświetlanie czcionki <#title.1.6.4>`_

==========
Główny kod
==========

Główny kod odpowiada za połączenie widgetu z api.
Umieszczamy go sekcji <header></header>, pod znacznikami <meta> znajdującym się zazwyczaj w górnej części strony.

=====
Popup
=====

Popup jest linkiem, który wykorzystujemy, jeśli chcemy otworzyć widget po wciśnięciu na jakiś link lub przycisk.

======
iFrame
======

iFrame jest elementem języka HTML, umożliwiającym zawieranie dokumentów HTML wewnątrz innych dokumentów HTML.
W przypadku widgetów, odpowiada za wyświetlanie całego widgetu w wybranej przez nas częsci strony.

Najważniejsze elementy konfiguracji iFrame-a
--------------------------------------------

| Jeśli chcemy zmienić rozmiar iframe-a, należy zmienić jedną lub obie ocje znajdujące się w dostępnym do skopiowania  kodzie iFrame-a. Są nimi **width="100%"** oraz **height="100%"**.
| Jeśli chcemy zmienić szerokość elementu, należy zmienić zawartość width ze 100% na inną interesującą nas wartość.
| Natomiast jeżeli chcemy zmienić wysokość elementu, należy zmienić zawartość **height** ze 100% na inną 
| interesującą nas wartość.

====================================
Implementacja kodu html, css oraz js
====================================

Początek
--------
Na samym początku musimy utworzyć plik .html, np. mojastrona.html.
Następnie dążymy do utworzenia szkieletu strony w wybranej przez nas wersji html. Dla potrzeb tego przykładu zastosujemy standard HTML5, który wygląda następująco:

.. code-block:: html

  <!DOCTYPE html> 
  <html> 
      <head> 
          <meta charset="UTF-8">
          <title>Przykładowy tytuł strony</title>
      </head>
  <body>

  </body>
  </html>

HTML
----

| Jeśli w kodzie HTML znajdują się na początku elementy ze znacznikami <link> lub <script>, kopiujemy te elementy, a następnie wklejamy do utworzonego przez nas pliku .html w sekcji <header></header>, preferowalnie pod znacznikiem <title>.
| Następnie kopiujemy *Główny kod*, o którym wspomniano na początku tej dokumentacji i umieszczamy go pod wcześniej wklejonymi elementami <link> / <script>.
| Reszte kodu HTML kopiujemy i wklejamy do sekcji <body></body>.

CSS
---
Kod znajdujący się w zakładce CSS należy skopiować i umieścić w naszym pliku .html, poza znacznikiem <html> na dole strony w sekcji <style type="text/css"></style>

JS
---
Kod znajdujący się w zakładce CSS należy skopiować i umieścić w naszym pliku .html, na samym dole, pod kodem CSS w sekcji <script type="text/javascript"></script>

====================
Najczęstsze problemy
====================

Widget się nie ładuje
---------------------
Upewnij się, że w pliku .html znajduje się Główny kod

.. code-block:: html

   <script> (function() { var script = document.createElement("script"); script.type = "text/javascript"; script.id = "rh-script"; script.src = "https://widget.radiohost.pl/api/v2.2/script.js"; script.setAttribute("eventListener", false); script.async = true; document.getElementsByTagName("head")[0].appendChild(script); })(); </script>

$ / JQUERY is not defined
-------------------------
Sprawdź czy posiadasz cdn jquery

.. code-block:: html

   <script src="//ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js"></script>

MOMENT.js is not defined
------------------------
Sprawdź czy posiadasz cdn moment.js

.. code-block:: html

    <script src="//cdnjs.cloudflare.com/ajax/libs/moment.js/2.18.1/moment.min.js"></script>

Niepoprawne wyświetlanie czcionki
---------------------------------
Sprawdź czy posiadasz cdn materializer od google, lub font awesome

.. code-block:: html

    <link href="//fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">

.. code-block:: html

    <link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet">