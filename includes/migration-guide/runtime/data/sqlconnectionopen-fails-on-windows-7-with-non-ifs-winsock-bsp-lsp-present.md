### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection.Open selže na systému Windows 7 s IFS Winsock BSP nebo LSP přítomen

|   |   |
|---|---|
|Podrobnosti|<xref:System.Data.SqlClient.SqlConnection.Open> a <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> selhat v rozhraní .NET Framework 4.5, pokud se systémem Windows 7 počítač s IFS Winsock BSP nebo LSP jsou k dispozici v počítači. K určení, zda je nainstalována IFS BSP nebo LSP, použijte <code>netsh WinSock Show Catalog</code> příkaz a zkontrolujte všechny <code>Winsock Catalog Provider Entry</code> položku, která je vrácena. Pokud má služba příznaky hodnot <code>0x20000</code> nastaveným bitem, zprostředkovatel používá IFS obslužné rutiny a nebude pracovat správně. Pokud <code>0x20000</code> je bit clear (nenastavena), protože je IFS BSP nebo LSP.|
|Návrh|Tato chyba byl opraven v rozhraní .NET Framework 4.5.2, takže ho předejít upgrade rozhraní .NET Framework. Alternativně můžete se vyhnout tím, že odebere všechny nainstalované jiný - IFS služeb vrstvy rozhraní Winsock.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|

