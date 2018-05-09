==========
HandlebarsJS
==========

HandlebarsJs to narzędzie umożliwiające budowanie **semantycznych szablonów**.

Jest on w dużej mierze kompatybilny z szablonami *Mustache*. W większości przypadków jest możliwa
podmiana Handlebars za Mustache i kontynuowanie używania tego samego szablonu.

Działanie
---------
Szablon Handlebars wygląda jak zwykły HTML z dołączonymi wyrażeniami handlebars

.. code-block:: html

    <div class="entry">
        <h1>{{title}}</h1>
        <div class="body">
            {{body}}
        </div>
    </div
Wyrażenie handlebar to: **{{ zawartość }}**

Aby dostarczyć szablon do przeglądarki, należy załączyć go w tagu **<script>**

.. code-block:: html

    <script id="entry-template" type="text/x-handlebars-template">
        <div class="entry">
            <h1>{{title}}</h1>
            <div class="body">
                {{body}}
            </div>
        </div>
    </script>
Uwaga
^^^^^
Jest to bardzo ważne, aby umieścić szablon wewnątrz tagu **<script>**. Umieszczenie
HTML bezpośrednio może spowodować modyfikacje zawartości przez HTML-parser.

Kompilacja szablonu przez JavaScript odbywa się poprzez metodę **Handlebars.compile**

.. code-block:: js

    var source   = document.getElementById("entry-template").innerHTML;
    var template = Handlebars.compile(source);
Prosze zauwazyć, że ten sposób nie jest rekomendowany dla aplikacji na produkcji.
Lepszym sposobem jest prekompilacja templatek. Dzięki temu zapotrzebowanie biblioteki *runtime*
będzie mniejsze oraz zaoszczędzeniu czasu na procesie kompilacji szablonu przez przeglądarke.
Jest to szczególnie ważne podczas pracy z urządzeniami mobilnymi.

Otrzymalnie wersji HTML rezultatu obrabiania szablonu przez Handlebars jest możliwe poprzezwykonanie templatki z kontekstem.

.. code-block:: js

    var context = {title: "My New Post", body: "This is my first post!"};
    var html    = template(context);
Otrzymamy:

.. code-block:: html

    <div class="entry">
        <h1>My New Post</h1>
        <div class="body">
            This is my first post!
        </div>
    </div>
