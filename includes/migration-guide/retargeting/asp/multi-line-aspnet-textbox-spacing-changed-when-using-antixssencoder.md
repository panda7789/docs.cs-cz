### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>Změnit mezery víceřádkové textové pole ASP.Net při použití AntiXSSEncoder

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.0, nadbytečné řádky vložily mezi řádky víceřádkové textové pole na zpětné volání, pokud se používá <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name>. V rozhraní .NET Framework 4.5 tyto zalomení řádku navíc nejsou zahrnuty, ale pouze v případě webové aplikace je cílen na verzi rozhraní .NET Framework 4.5|
|Návrh|Mějte na paměti, že 4.0 webové aplikace změnilo na rozhraní .NET Framework 4.5 může mít víceřádkových textových polí se už vložit zalomení řádku navíc. Pokud to není žádoucí, může aplikace přimět staré chování při spuštění v rozhraní .NET Framework 4.5 pomocí cílení na rozhraní .NET Framework 4.0.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Mění se cílení|

