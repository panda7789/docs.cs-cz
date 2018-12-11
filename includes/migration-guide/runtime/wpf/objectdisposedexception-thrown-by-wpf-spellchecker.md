### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>Objectdisposedexception – vyvolané kontrolu pravopisu WPF

|   |   |
|---|---|
|Podrobnosti|Aplikace WPF někdy dojít k chybě při ukončení aplikace se <xref:System.ObjectDisposedException?displayProperty=name> vyvolané kontrolu pravopisu. Tento problém je vyřešený v rozhraní .NET Framework 4.7 WPF řádně zpracování výjimek a zajistila, že aplikace jsou už nebude mít nepříznivý vliv. Je třeba poznamenat, že by má být dodržen v aplikacích spuštěných v ladicím programu pokračovat občasné výjimkách first-chance.|
|Doporučení|Upgrade na rozhraní .NET Framework 4.7|
|Rozsah|Edge|
|Version|4.6.1|
|Typ|Modul runtime|

