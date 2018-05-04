### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView vyvolá výjimka ArgumentOutOfRangeException

|   |   |
|---|---|
|Podrobnosti|<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> bude fungovat asynchronně, když je povolena virtualizace sloupec, ale nebyly dosud stanoveny šířku sloupců.  Pokud sloupce jsou odebrány, než se stane asynchronní práce, <xref:System.ArgumentOutOfRangeException?displayProperty=name> situace může nastat.|
|Návrh|Kterákoli z následujících akcí:<ol><li>Upgrade na rozhraní .NET Framework 4.7.</li><li>Nainstalujte nejnovější údržby opravy pro rozhraní .NET Framework 4.6.2.</li><li>Nedošlo k odebrání sloupce dokud asynchronní odpověď na <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> byla dokončena.</li></ol>|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|

