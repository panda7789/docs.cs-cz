### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a>IPad nesmí použít v souboru vlastní možnosti, protože je nyní funkce prohlížeče

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET 4.5, iPad je identifikátor v souboru možnosti výchozí ASP.NET prohlížeče, takže nesmí být použita v souboru vlastní možnosti|
|Návrh|Pokud funkce specifické pro iPad je potřeba, je potřeba změnit chování iPad nastavením možnosti na refID předdefinovaných gateway &quot;IPad&quot; místo vygenerováním novou &quot;IPad&quot; ID agentem uživatele odpovídající.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|

