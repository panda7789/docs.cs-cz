### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>Ve výchozím nastavení vypnutá metodu nahraďte v adresách URL OData

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5, metoda nahraďte v adresách URL OData ve výchozím nastavení vypnutá. Pokud je zakázáno nahradit OData (nyní ve výchozím nastavení), veškeré žádosti uživatelů, včetně funkcí nahradit, (které nejsou běžné) se nezdaří.|
|Návrh|Pokud se vyžaduje metoda nahrazení (což neobvyklé), může být znovu zapnout pomocí nastavení konfigurace (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>). Metodu povoleno nahradit však můžete otevřít bezpečnostní zranitelná místa a musí být použit pouze po pečlivě zkontrolujte.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|

