### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>Ověření schématu XSD nyní správně rozpozná porušení jedinečné omezení, pokud složené klíče se používají a jeden klíč je prázdná

|   |   |
|---|---|
|Podrobnosti|Verze rozhraní .NET Framework 4.6 obsahovala chybu, která způsobila ověření XSD není detekuje jedinečné omezení složené klíče, pokud jeden z klíčů byla prázdná. V rozhraní .NET Framework 4.6 je tento problém vyřešen. To bude mít za následek více správné ověření, ale také to může způsobit v některé XML není ověřování, které dříve by mít.|
|Návrh|V případě potřeby Čím větší ověřování rozhraní .NET Framework 4.0 ověřování aplikace, můžete vybrat verzi 4.5 (nebo starší) rozhraní .NET Framework. Při přesměrování na rozhraní .NET 4.6, ale revize kódu potřeba zajistit, že duplicitní složené klíče (jak je popsáno v popisu tento problém) nejsou očekávané k ověření.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Změna orientace|

