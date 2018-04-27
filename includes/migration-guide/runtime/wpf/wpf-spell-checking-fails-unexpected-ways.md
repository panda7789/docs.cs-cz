### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>Kontrola pravopisu WPF selže neočekávané způsoby

|   |   |
|---|---|
|Podrobnosti|To zahrnuje několik kontrola pravopisu WPF problémy:<ul><li>Kontrola pravopisu WPF někdy vyvolá. <xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>Kontrola pravopisu WPF selže s <xref:System.UnauthorizedAccessException> při spouštění aplikací pomocí "Spustit jako jiný uživatel.</li><li>Kontrola pravopisu WPF nesprávně identifikován pravopisné chyby ve složených slov jako 'Hausnummer' v němčině.</li></ul>|
|Návrh|Problém #1 – to byl vyřešen v rozhraní .NET Framework 4.6.2 problém č. 2 - Kontrola pravopisu WPF již není podporován při spouštění aplikací pomocí 'spustit jako jiný uživatel'. Spouštění rozhraní .NET Framework 4.6.2, aplikace spustit tímto způsobem už havárií neočekávaně – místo toho bude kontrola pravopisu bezobslužně zakázáno. Problém #3 – to je v rozhraní .NET Framework 4.6.2 bylo opraveno.|
|Rozsah|Edge|
|Version|4.6.1|
|Typ|Modul runtime|

