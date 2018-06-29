### <a name="chained-popups-with-staysopenfalse"></a>Zřetězené automaticky otevíraná okna s StaysOpen = False

|   |   |
|---|---|
|Podrobnosti|Místní okno s StaysOpen = False je by měl zavřete po kliknutí na tlačítko mimo místní nabídce. Když jsou zřetězené dvou nebo více těchto automaticky otevíraná okna (tj. jeden obsahuje jiné), došlo k mnoha potížím, včetně:<ul><li>Otevřete dvě úrovně, klikněte na mimo P2, ale uvnitř P1.  Nedojde k žádné akci.</li><li>Otevřete dvě úrovně, klikněte na mimo P1.  Jak automaticky otevíraná okna zavřete.</li><li>Otevírají a zavírají dvě úrovně.  Zkuste se znovu otevřete P2.  Nedojde k žádné akci.</li><li>Zkuste otevřít tři úrovně.  Nelze vytvořit.  (Nedojde k žádné akci nebo první dvě úrovně zavřete, v závislosti na tom, kde kliknete.) Tyto případy (a ostatní varianty) nyní fungovat podle očekávání.</li></ul>|
|Rozsah|Edge|
|Version|4.7.1|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|

