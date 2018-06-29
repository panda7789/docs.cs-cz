### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a>Výchozí hodnota je WPF TextBox vrátit zpět limit 100

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5 je výchozí limit vrácení zpět pro textové pole WPF 100 (na rozdíl od vrácení neomezená v rozhraní .NET Framework 4.0)|
|Návrh|Pokud limit 100 vrácení zpět je příliš nízké, může být explicitně nastavena limit s <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>|
|Rozsah|Edge|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

