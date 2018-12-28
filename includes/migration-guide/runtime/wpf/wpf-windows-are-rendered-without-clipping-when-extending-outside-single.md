### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>Vykreslení WPF windows bez oříznutí při rozšiřování mimo jednoho monitoru

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6 spuštěné v systému Windows 8 a vyšším, je vykreslen celé okno bez oříznutí při rozšiřuje mimo jednotné zobrazení v případě více monitorů. Tím se liší od předchozích verzí rozhraní .NET Framework, které by oříznout WPF windows, které rozšířit nad rámec jednoho zobrazení.|
|Doporučení|Toto chování (jestli se má oříznout nebo ne) lze explicitně nastavit pomocí <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> prvek <code>&lt;appSettings&gt;</code> v konfiguračním souboru aplikace nebo tím, že nastavíte <code>EnableMultiMonitorDisplayClipping</code> vlastnost při spuštění aplikace.|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Modul runtime|

