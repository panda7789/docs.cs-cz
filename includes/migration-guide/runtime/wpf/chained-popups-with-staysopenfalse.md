### <a name="chained-popups-with-staysopenfalse"></a>Zřetězené automaticky otevíraná okna s nastavením StaysOpen = False

|   |   |
|---|---|
|Podrobnosti|Automaticky otevíraného okna s nastavením StaysOpen = False by měl po kliknutí na mimo automaticky otevírané okno zavřít. Když jsou zřetězeny dva nebo více těchto automaticky otevíraná okna (to znamená jeden obsahuje další), došlo k mnoha problémům, včetně:<ul><li>Spusťte dvě úrovně, klikněte na mimo P2, ale uvnitř P1.  Nic se nestane.</li><li>Spusťte dvě úrovně, klikněte na vnější P1.  Zavřete obě automaticky otevíraná okna.</li><li>Otevření a zavření dvě úrovně.  Zkuste znovu otevřít P2.  Nic se nestane.</li><li>Došlo k pokusu o otevření tři úrovně.  Nemůžete.  (Nic se nestane nebo zavřete první dvě úrovně, v závislosti na tom, kde klikněte na.) Tyto případy (a další varianty) nyní fungovat podle očekávání.</li></ul>|
|Rozsah|Edge|
|Version|4.7.1|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|

