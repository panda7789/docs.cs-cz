### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>Volání z obslužné rutiny CellEditEnding DataGrid.CommitEdit zahodí fokus

|   |   |
|---|---|
|Podrobnosti|Volání <xref:System.Windows.Controls.DataGrid.CommitEdit> z jednoho z <xref:System.Windows.Controls.DataGrid?displayProperty=name>společnosti <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> způsobí, že obslužné rutiny událostí <xref:System.Windows.Controls.DataGrid?displayProperty=name> ztratí fokus.|
|Návrh|Tato chyba byla opravena v rozhraní .NET Framework 4.5.2, takže lze se vyhnout upgradem rozhraní .NET Framework. Alternativně můžete se vyhnout výběrem explicitně znovu <xref:System.Windows.Controls.DataGrid?displayProperty=name> po volání <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|

