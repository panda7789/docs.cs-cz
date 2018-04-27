### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>Změna vlastnosti hodnotu IsEnabled nadřazeného ovládacího prvku TextBlock ovlivňuje všechny podřízené ovládací prvky

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6.2, změna <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> vlastnost nadřazeného <xref:System.Windows.Controls.TextBlock?displayProperty=name> řízení ovlivňuje všechny podřízené ovládací prvky (například hypertextové odkazy a tlačítka) <xref:System.Windows.Controls.TextBlock?displayProperty=name> ovládacího prvku. V rozhraní .NET Framework 4.6.1 a dřívějších verzí, ovládací prvky uvnitř <xref:System.Windows.Controls.TextBlock?displayProperty=name> vždy neodrážejí stav <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> vlastnost <xref:System.Windows.Controls.TextBlock?displayProperty=name> nadřazené.|
|Návrh|Žádné Tato změna vyhovuje očekávané chování u ovládacích prvků <xref:System.Windows.Controls.TextBlock?displayProperty=name> ovládacího prvku.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|

