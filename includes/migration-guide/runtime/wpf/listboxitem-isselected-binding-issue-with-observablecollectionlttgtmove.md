### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>IsSelected objektu ListBoxItem vazby problém s kolekci ObservableCollection&lt;T&gt;. Přesunutí

|   |   |
|---|---|
|Podrobnosti|Volání <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> nebo <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> na vázán na kolekci <xref:System.Windows.Controls.ListBox?displayProperty=name> s vybraných položek může vést k nepředvídatelnému chování budoucí výběru nebo unselection z <xref:System.Windows.Controls.ListBox?displayProperty=name> položky.|
|Návrh|Volání <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> a <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> místo <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> bude tento problém obejít. Tento problém nebo chyba byla opravena v rozhraní .NET Framework 4.6 a může vyřešit upgradem na verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

