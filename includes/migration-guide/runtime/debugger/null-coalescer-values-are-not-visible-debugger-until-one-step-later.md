### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Hodnoty Null coalescer nejsou viditelné v ladicím programu až do jednoho kroku později

|   |   |
|---|---|
|Podrobnosti|Chyby v rozhraní .NET Framework 4.5 způsobí, že hodnotami nastavenými prostřednictvím prázdná operace slučování nebude viditelné v ladicím programu okamžitě po provedení operace přiřazení při spuštění v 64bitové verzi rozhraní.|
|Návrh|Krokování s jednou další v ladicím programu způsobí, že hodnotu místní nebo pole správně aktualizovat. Navíc tento problém byl opraven v rozhraní .NET Framework 4.6; upgrade na tuto verzi rozhraní by měla potíže vyřešit.|
|Rozsah|Edge|
|Version|4.5|
|Typ|modul runtime|

