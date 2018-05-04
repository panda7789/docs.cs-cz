### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Položka posouvání jako plochý seznam s položkami různých výšky pixelů

|   |   |
|---|---|
|Podrobnosti|Když <xref:System.Windows.Controls.ItemsControl?displayProperty=name> zobrazí kolekci pomocí virtualizace (<code>IsVirtualizing=true</code>) a položku - posouvání (<code>ScrollUnit=Item</code>), a potom, co ovládací prvek posune zobrazíte položky se liší od své okolí, jejichž výška v pixelech <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> iteruje nad všechny položky v kolekci. Uživatelské rozhraní je reagovat během této iterace; Pokud je kolekce velký, to může být považována za zablokování. Iterace dojde za jiných okolností, a to i v předchozích verzích rozhraní .NET Framework. Například nastane při posouvání pixelů (<code>ScrollUnit=Pixel</code>) při zjištění položku s jinou výšku a při posouvání položky hierarchické data (, jako <xref:System.Windows.Controls.TreeView?displayProperty=name> nebo <xref:System.Windows.Controls.ItemsControl?displayProperty=name> s seskupení povoleno) při zjištění položku se jiný počet následné položek než své okolí. Pro případ výška položky posouvání a jiné pixelů iterace byla zavedena v rozhraní .NET Framework 4.6.1 opravit chyby v rozložení hierarchické data.  Není potřeba, pokud jsou data s plochou (žádná hierarchie) a jeho rozhraní .NET Framework 4.6.2 v takovém případě neprovádí.|
|Návrh|Pokud iterace dojde v rozhraní .NET Framework 4.6.1, ale není v dřívějších verzích – to znamená, pokud <xref:System.Windows.Controls.ItemsControl?displayProperty=name> je položka-posouvání jako plochý seznam s položkami různých pixelů výšky - existují dvě náhrad:<ol><li>Nainstalujte rozhraní .NET Framework 4.6.2.</li><li>Nainstalujte opravu hotfix HR 1605 pro rozhraní .NET Framework 4.6.1.</li></ol>|
|Rozsah|Vedlejší|
|Version|4.6.1|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|

