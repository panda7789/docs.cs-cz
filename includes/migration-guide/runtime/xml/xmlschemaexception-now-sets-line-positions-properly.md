### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>Xmlschemaexception – správně teď nastavuje pozice řádků

|   |   |
|---|---|
|Podrobnosti|Pokud <xref:System.Xml.Linq.LoadOptions.SetLineInfo> hodnota je předaný metodě zatížení a dojde k chybě ověření, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> a <xref:System.Xml.Schema.XmlSchemaException.LinePosition> vlastnosti teď obsahují informace o řádku.|
|Návrh|Zpracování výjimek kód, který předpokládá <xref:System.Xml.Schema.XmlSchemaException.LineNumber> a <xref:System.Xml.Schema.XmlSchemaException.LinePosition> nebude sada by měl aktualizovat, protože tyto vlastnosti, bude nastavena správně při SetLineInfo se používá při načítání XML.|
|Rozsah|Edge|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|

