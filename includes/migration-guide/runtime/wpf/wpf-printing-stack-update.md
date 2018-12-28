### <a name="wpf-printing-stack-update"></a>Aktualizace zásobníku tisk WPF

|   |   |
|---|---|
|Podrobnosti|Pomocí rozhraní API pro tisk na WPF <xref:System.Printing.PrintQueue?displayProperty=name> nyní volat okna Tisk dokumentu balíčku API ve prospěch teď zastaralé rozhraní API tisk XPS. Změny s použitelnost v úvahu; uživatelé ani vývojáři měli vidět všechny změny v chování nebo použití rozhraní API. Nový zásobník tisk je standardně povolená, když běží v systému Windows 10 Creators Update. Staré zásobníku tisku bude nadále fungovat stejně jako v minulosti ve starších verzích Windows.|
|Doporučení|Chcete-li použít staré zásobníku ve Windows 10 Creators Update, nastavte <code>UseXpsOMPrinting</code> hodnota REG_DWORD <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> klíč registru, který <code>1</code>.|
|Rozsah|Edge|
|Version|4.7|
|Typ|Modul runtime|

