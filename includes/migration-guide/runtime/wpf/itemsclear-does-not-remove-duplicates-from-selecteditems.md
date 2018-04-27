### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear neodebere duplicitní položky ze SelectedItems

|   |   |
|---|---|
|Podrobnosti|Předpokládejme, že selektor (s vícenásobným výběrem povolené) má duplicitní položky v jeho <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> kolekce - stejnou položku vyskytuje více než jednou.  Odebrání těchto položek ze zdroje dat (např. při volání Items.Clear) nepodaří odeberte je ze <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>; pouze první instance je odebrána. Kromě toho následné použití <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> (například SelectedItems.Clear()) může dojít k problémům, jako <xref:System.ArgumentException?displayProperty=name>, protože <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> obsahuje položky, které již nejsou v datovém zdroji.|
|Návrh|Pokud je to možné upgradujte na rozhraní .NET 4.6.2.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|

