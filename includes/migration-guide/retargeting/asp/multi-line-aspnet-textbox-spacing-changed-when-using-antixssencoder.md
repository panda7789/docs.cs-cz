### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>Víceřádkový ASP.Net TextBox mezery změnit při použití AntiXSSEncoder

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.0, další řádky byly vloženy mezi řádky Víceřádkový textové pole na zpětné volání, pokud se používá <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name>. Rozhraní .NET Framework 4.5 tyto nadbytečné konce řádků nejsou zahrnuty, ale pouze v případě, že webová aplikace je cílení na rozhraní .NET 4.5|
|Návrh|Upozorňujeme, že změnit cíl na rozhraní .NET 4.5 necílené 4.0 webové aplikace může mít více řádků textová pole vylepšené už vložit nadbytečné konce řádků. Pokud to není žádoucí, aplikace může mít staré chování při spuštění v rozhraní .NET Framework 4.5 cílením rozhraní .NET Framework 4.0.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Změna orientace|

