### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>Přístup k vybrané položky WPF DataGrid z obslužnou rutinu události v kolekci DataGrid UnloadingRow může způsobit výjimky NullReferenceException.

|   |   |
|---|---|
|Podrobnosti|Z důvodu chyby v rozhraní .NET Framework 4.5, obslužné rutiny události pro <xref:System.Windows.Controls.DataGrid> může způsobit události zahrnující odebrání řádek <xref:System.NullReferenceException?displayProperty=name> vyvolání, pokud chtějí získat přístup <xref:System.Windows.Controls.DataGrid>na <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> nebo <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> vlastnosti.|
|Návrh|Tento problém byl opraven v rozhraní .NET Framework 4.6 a může být kontaktována upgrade na tuto verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|

