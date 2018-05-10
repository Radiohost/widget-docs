=====================
Zastosowanie helperów
=====================
#if_eq
----------
**#if_eq** (if equal | jeżeli równe) jest helperem sprawdzającym czy podane wartości są równe.
Jego składnia wygląda następująco:

.. code-block:: html

    {{#if_eq wartosc1 wartosc2}}
        Lorem ipsum
    {{/if_eq}}
Wartości mogą być zarówno elementami tablicy, obiektami jak i zwykłym tekstem, liczbą.
Jeśli obie wartości będą identyczne to zostanie przetworzony kod znajdujący się wewnątrz.

**Przykład:**

.. code-block:: html

    {{#each presenter.socials }} <!--pętla przelatująca przez wszystkie media społecznościowe przypisane danemu prezenterowi-->
        {{#if_eq service "facebook"}}
        <!--sprawdzanie czy nazwa media społecznościowego znajdująca się w obecnym elemencie "service" jest równa string-owi "facebook"--> 
            <a href="#"><li><i class="fa fa-facebook"></i></li></a> <!--jeśli tak to wyswietl link do przypisanego profilu Facebook-->
        {{/if_eq}} <!--koniec if-a-->
        {{#if_eq service "twitter"}}
        <!--sprawdzanie czy nazwa media społecznościowego znajdująca się w obecnym elemencie "service" jest równa string-owi "twitter"--> 
            <a href="#"><li><i class="fa fa-twitter"></i></li></a> <!--jeśli tak to wyswietl link do przypisanego profilu Twitter-->
        {{/if_eq}} <!--koniec if-a-->
        {{#if_eq service "linkedin"}}
        <!--sprawdzanie czy nazwa media społecznościowego znajdująca się w obecnym elemencie "service" jest równa string-owi "linkedin"--> 
            <a href="#"><li><i class="fa fa-linkedin"></i></li></a> <!--jeśli tak to wyswietl link do przypisanego profilu LinkedIn-->
        {{/if_eq}} <!--koniec if-a-->
    {{/each}} <!--koniec pętli-->

#if_not
----------
**#if_not** jest helperem sprawdzającym czy podane wartości różnią się od siebie.
Jego składnia wygląda następująco:

.. code-block:: html

    {{#if_not wartosc1 wartosc2}}
        Lorem ipsum
    {{/if_not}}
Wartości mogą być zarówno elementami tablicy, obiektami jak i zwykłym tekstem, liczbą.
Jeśli któraś wartość będzie różna od pozostałej to zostanie przetworzony kod znajdujący się wewnątrz.

**Przykład:**

.. code-block:: html

    <script id="rh-radio-current-broadcast-template" type="text/html"> <!--zadeklarowanie szablonu-->
        <div class="col-md-12">
            {#if_eq $live true}
            <!--sprawdzenie czy wartość atrybutu odpowiadającego za sprawdzenie czy trwa audycja na zywo jest równa true-->
                <img src="{{ broadcast.djavatar }}" alt="currentpresenter"> <!--jeśli tak to pojawia się avatar prezentera-->
            {/if_eq} <!--koniec if-a-->
            {#if_not $live true}
            <!--sprawdzenie czy wartość atrybutu odpowiadającego za sprawdzenie czy trwa audycja na zywo jest inna niż true-->
                <img class="radio-current-song-cover" src="" alt="albumcover"> <!--jeśli tak to pojawia się okładka piosenki-->
            {/if_not} <!--koniec if-a-->
            <!--połączenie if_eq z if_not jest niczym innym jak bardziej skomplikowanym "else"-->
        </div>
    </script> <!--koniec templatki-->
