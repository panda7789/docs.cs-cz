### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>Posouvání WPF TreeView nebo seskupené ListBox v VirtualizingStackPanel může dojít zablokování

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework v4.5, posouvání WPF <xref:System.Windows.Controls.TreeView?displayProperty=name> v virtualizované zásobníku panely způsobit zablokování, pokud jsou v zobrazení okraje (mezi položkami v <xref:System.Windows.Controls.TreeView?displayProperty=name>, například, nebo v elementu ItemsPresenter). Kromě toho v některých případech různé velikosti položky v zobrazení může způsobit nestabilitu i v případě, že neexistují žádné okraje.|
|Návrh|Tato chyba může zabránit upgrade rozhraní .NET Framework 4.5.1. Alternativně můžete z kolekce zobrazení odebrat okraje (jako je <xref:System.Windows.Controls.TreeView?displayProperty=name>s) v rámci virtualizovaného zásobníku panelů, pokud všechny obsažené položek se stejnou velikost.|
|Rozsah|Hlavní|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|

