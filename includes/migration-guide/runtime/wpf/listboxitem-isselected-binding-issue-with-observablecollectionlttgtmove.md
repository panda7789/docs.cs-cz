### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>IsSelected – ListBoxItem vazby problém s ObservableCollection&lt;T&gt;. Přesunutí

|   |   |
|---|---|
|Podrobnosti|Volání metody <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> nebo <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> na kolekci vázána <xref:System.Windows.Controls.ListBox?displayProperty=name> s položek vybraných může způsobit nestabilní chování budoucí výběru nebo unselection z <xref:System.Windows.Controls.ListBox?displayProperty=name> položky.|
|Návrh|Volání metody <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> a <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> místo <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> se tento problém obejít. Případně se tento problém byl opraven v rozhraní .NET Framework 4.6 a může být kontaktována upgrade na tuto verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

