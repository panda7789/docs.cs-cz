### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>ObjectDisposedException vyvolané WPF kontrola pravopisu

|   |   |
|---|---|
|Podrobnosti|Aplikace WPF někdy dojít k chybě při ukončení aplikace s <xref:System.ObjectDisposedException?displayProperty=name> vyvolané kontroly pravopisu. To je opraven v rozhraní .NET 4.7 WPF pohodlné zpracování výjimek a tím zajistíte, že aplikace jsou už negativní vliv. Je potřeba poznamenat, že má být dodržen v aplikacích spuštěných v rámci ladicího by pokračovat příležitostně první možnosti výjimky.|
|Návrh|Upgrade na rozhraní .NET 4.7|
|Rozsah|Edge|
|Version|4.6.1|
|Typ|Modul runtime|

