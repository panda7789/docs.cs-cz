### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView vyvolá ArgumentOutOfRangeException

|   |   |
|---|---|
|Podrobnosti|<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> bude fungovat asynchronně, když je povolena virtualizace sloupec, ale ještě nebyly byla určena šířku sloupců.  Pokud se předtím, než se asynchronní práce se stane, jsou odebrány sloupce <xref:System.ArgumentOutOfRangeException?displayProperty=name> situace může nastat.|
|Doporučení|Některou z následujících akcí:<ol><li>Upgrade na rozhraní .NET Framework 4.7.</li><li>Nainstalujte nejnovější údržby opravy pro rozhraní .NET Framework 4.6.2.</li><li>-Li zabránit odebrání sloupce do asynchronní odpověď <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> byla dokončena.</li></ol>|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|

