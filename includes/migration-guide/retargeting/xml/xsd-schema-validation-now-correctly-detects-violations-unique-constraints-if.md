### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>Ověření schématu XSD nyní správně rozpozná porušení unikátních omezení, pokud složené klíče se používají a jeden klíč je prázdný

|   |   |
|---|---|
|Podrobnosti|Verze rozhraní .NET Framework 4.6 měl chybu, která způsobila ověření XSD není zjistit unikátních omezení na složených klíčích, pokud jeden z klíčů byla prázdná. V rozhraní .NET Framework 4.6 je tento problém vyřešen. Výsledkem bude více správné ověření, ale může také vést některé XML není ověřování, který už má.|
|Návrh|V případě potřeby volnější ověřování rozhraní .NET Framework 4.0 ověřování aplikace může cílit verzi 4.5 (nebo starší) rozhraní .NET Framework. Když mění se cílení na rozhraní .NET Framework 4.6, ale revize kódu se má počítat ujistit se, že duplicitní složených klíčů (jak je popsáno v popisu tento problém) se nepředpokládá ověření.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Mění se cílení|

