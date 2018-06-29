### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Nesprávné generování kódu při předávání a porovnávání hodnot UInt16

|   |   |
|---|---|
|Podrobnosti|Z důvodu změny uváděné ve 4.7 rozhraní .NET Framework, v některých případech kód vygenerovaný kompilátoru za běhu v aplikacích spuštěných na rozhraní .NET Framework 4.7 nesprávně porovná dvě <code>T:System.UInt16</code> hodnoty. Další informace najdete v tématu [problém #11508: bezobslužná nesprávná funkce codegen při předávání a porovnávání argumentů ushort](https://github.com/dotnet/coreclr/issues/11508) na webu GitHub.com.|
|Návrh|Pokud narazíte na problémy v porovnání 16bitové nepodepsané hodnot v 4.7 rozhraní .NET Framework, upgradujte na rozhraní .NET Framework 4.7.1.|
|Rozsah|Edge|
|Version|4.7|
|Typ|modul runtime|

