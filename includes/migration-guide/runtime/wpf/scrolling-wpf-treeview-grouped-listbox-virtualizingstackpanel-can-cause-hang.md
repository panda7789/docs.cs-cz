### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>Posouvání prvku WPF TreeView nebo seskupené ListBox v VirtualizingStackPanel může způsobit zablokování

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework v4.5, posouvání WPF <xref:System.Windows.Controls.TreeView?displayProperty=name> ve virtualizovaných zásobníku panelu způsobit. program přestane reagovat, pokud nejsou okraje v zobrazení (mezi položkami v <xref:System.Windows.Controls.TreeView?displayProperty=name>, například, nebo v elementu ItemsPresenter). Kromě toho v některých případech různé velikosti položky v zobrazení může způsobit nestabilitu i v případě, že neexistují žádné okraje.|
|Návrh|Upgradem na rozhraní .NET Framework 4.5.1 se lze vyvarovat této chyby. Okraje Alternativně je možné odebrat ze zobrazení kolekce (jako je <xref:System.Windows.Controls.TreeView?displayProperty=name>s) v rámci zásobníku virtualizované panelů, je-li všechny obsažené položky mají stejnou velikost.|
|Rozsah|Hlavní|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|

