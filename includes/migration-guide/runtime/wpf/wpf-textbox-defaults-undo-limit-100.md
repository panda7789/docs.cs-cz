### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a>Výchozí hodnota je textové pole WPF zrušit limit 100

|   |   |
|---|---|
|Podrobnosti|Výchozí limit vrácení zpět pro textové pole s WPF v rozhraní .NET Framework 4.5, je 100 (na rozdíl od vrácení neomezený počet v rozhraní .NET Framework 4.0)|
|Návrh|Pokud zpět maximálně 100 je příliš nízké, limit lze nastavit explicitně pomocí <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

