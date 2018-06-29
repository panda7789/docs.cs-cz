### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>Volání DataGrid.CommitEdit z obslužnou rutinu CellEditEnding zahodí fokusu

|   |   |
|---|---|
|Podrobnosti|Volání metody <xref:System.Windows.Controls.DataGrid.CommitEdit> z jednoho z <xref:System.Windows.Controls.DataGrid?displayProperty=name>na <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> způsobí, že obslužné rutiny událostí <xref:System.Windows.Controls.DataGrid?displayProperty=name> ztratí fokus.|
|Návrh|Tato chyba byl opraven v rozhraní .NET Framework 4.5.2, takže ho předejít upgrade rozhraní .NET Framework. Alternativně můžete vyhnout tak, že explicitně znovu vyberete <xref:System.Windows.Controls.DataGrid?displayProperty=name> po volání <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.|
|Rozsah|Edge|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|

