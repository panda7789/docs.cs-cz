### <a name="wpf-spawns-a-wisptisexe-process-which-can-freeze-the-mouse"></a>WPF vytvoří wisptis.exe proces, který může zablokovat myši

|   |   |
|---|---|
|Podrobnosti|Problém byl zaveden ve verzi 4.5.2, který způsobí, že <code>wisptis.exe</code> k se vytvoří podřízený proces, který může zablokovat vstup z myši.|
|Návrh|Oprava tohoto problému je k dispozici v servisní verze rozhraní .NET Framework 4.5.2 (kumulativní opravu hotfix 3026376) nebo upgradem na rozhraní .NET Framework 4.6|
|Rozsah|Hlavní|
|Version|4.5.2|
|Typ|Modul runtime|

