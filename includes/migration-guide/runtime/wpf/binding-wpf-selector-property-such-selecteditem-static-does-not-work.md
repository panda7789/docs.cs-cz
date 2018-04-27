### <a name="binding-a-wpf-selector-property-such-as-selecteditem-to-a-static-property-does-not-work"></a>Vytvoření vazby vlastnosti selektor grafického subsystému WPF (například "SelectedItem") na statickou vlastnost nefunguje

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5, WPF selektor vlastnosti (například &#39;SelectedItem&#39; na <xref:System.Windows.Controls.ListBox?displayProperty=name> nebo <xref:System.Windows.Controls.DataGrid?displayProperty=name>), jsou vázané na data statický vlastnosti neaktualizují správně při aktualizaci jejich vázané vlastnosti.|
|Návrh|Toto chování se vrátila v servisní aktualizace pro rozhraní .NET Framework 4.5. Aktualizujte prosím rozhraní .NET Framework 4.5, nebo upgradujte na verzi rozhraní .NET Framework 4.5.1 nebo novější, pokud chcete tento problém vyřešit.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|

