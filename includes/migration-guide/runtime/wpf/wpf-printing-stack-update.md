### <a name="wpf-printing-stack-update"></a>Aktualizace zásobníku tisk WPF

|   |   |
|---|---|
|Podrobnosti|Pomocí rozhraní API pro tisk na WPF <xref:System.Printing.PrintQueue?displayProperty=name> nyní volání rozhraní API k uživatele systému Windows tisk dokumentu balíčku považuje nyní zastaralé API tisk XPS. Změny s použitelnost pamatovat; uživatelé ani vývojáři měli vidět všechny změny v chování nebo využití rozhraní API. Spouštění v systému Windows 10 Creators aktualizace se ve výchozím nastavení zapnutá novým zásobníkem tisku. Původní zásobníku tisku bude nadále fungovat stejně jako předtím ve starších verzích systému Windows.|
|Návrh|Použít staré zásobníku v systému Windows 10 Creators aktualizace, nastavte <code>UseXpsOMPrinting</code> REG_DWORD hodnotu <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> klíč registru <code>1</code>.|
|Rozsah|Edge|
|Version|4.7|
|Typ|modul runtime|

