### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>Nahraďte metodu v adresách URL OData je ve výchozím nastavení zakázána.

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.5, nahraďte metodu v adresách URL OData je standardně zakázáno. Pokud nahradit OData je zakázáno (nyní ve výchozím nastavení), veškeré žádosti uživatelů, včetně funkcí nahradit, (které neobvyklé) se nezdaří.|
|Návrh|Pokud je potřeba nahradit – metoda (což je běžné), může být znovu zapnout pomocí nastavení konfigurace (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>). Metodu povoleno nahradit však můžete otevřít bezpečnostní zranitelná místa a by měla sloužit pouze po pečlivou revizi.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|

