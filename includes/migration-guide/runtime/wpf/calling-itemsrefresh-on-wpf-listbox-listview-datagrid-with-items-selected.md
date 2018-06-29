### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>Volání Items.Refresh na WPF ListBox, ListView nebo DataGrid s položek vybraných může způsobit duplicitní položky se objeví v elementu.

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5, když je vybraných položek v volání ListBox.Items.Refresh z kódu <xref:System.Windows.Controls.ListBox?displayProperty=name> může způsobit zkopírovat do seznamu vybrané položky. Podobné problém se vyskytuje v <xref:System.Windows.Controls.ListView?displayProperty=name> a <xref:System.Windows.Controls.DataGrid?displayProperty=name>. Tento problém je vyřešený v rozhraní .NET Framework 4.6.|
|Návrh|Tento problém může být odpracovaných kolem programově unselecting položky před <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> se označuje jako a potom znovu je vyberete po dokončení volání. Případně se tento problém byl opraven v rozhraní .NET Framework 4.6 a může být kontaktována upgrade na tuto verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|

