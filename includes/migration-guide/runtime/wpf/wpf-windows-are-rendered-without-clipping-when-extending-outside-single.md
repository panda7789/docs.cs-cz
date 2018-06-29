### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>WPF windows vykreslují bez výstřižek rozšíření mimo jednoho monitoru

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6 běžícím na systému Windows 8 a vyšší, vykreslením celé okno bez výstřižek, když ji rozšiřuje mimo jednoho zobrazení ve scénáři s více monitorování. To se liší od předchozích verzí rozhraní .NET Framework, které by v případě potřeby upraví WPF windows, které i po uplynutí jednoho zobrazení.|
|Návrh|Toto chování (ať už k oříznutí nebo ne) může být explicitně nastaveny pomocí <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element v <code>&lt;appSettings&gt;</code> v konfiguračním souboru aplikace, nebo nastavením <code>EnableMultiMonitorDisplayClipping</code> vlastnost při spuštění aplikace.|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|modul runtime|

