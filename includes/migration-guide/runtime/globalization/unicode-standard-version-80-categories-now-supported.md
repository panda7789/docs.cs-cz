### <a name="unicode-standard-version-80-categories-now-supported"></a>Kategorie Unicode standardní verzi 8.0, teď podporuje

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 Unicode data upgradována z standardu Unicode verze 6.3 verzi 8.0.  Při žádosti kategorií znaků Unicode v rozhraní .NET Framework 4.6.2, nemusí odpovídat některé výsledky výsledky v předchozích verzích rozhraní .NET Framework.  Tato změna většinou má vliv Čerokí slabik a nové značky samohlásky Tai Lue a styl podání znaky.|
|Návrh|Zkontrolujte kód a odebrat nebo změnit logiku, která závisí na pevně kategorií znaků Unicode.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

