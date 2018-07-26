### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a>IPad by neměl v souboru vlastní možnosti použít, protože je nyní schopnostech prohlížeče

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5, iPad je identifikátor v výchozí prohlížeč možnosti souboru ASP.NET, proto by neměl být použít v souboru vlastní funkce|
|Návrh|Pokud funkce specifické pro iPad, je potřeba změnit chování iPad nastavením možnosti na předem definované brány refID &quot;IPad&quot; místo generováním nového &quot;IPad&quot; ID podle uživatelského agenta porovnávání.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|

