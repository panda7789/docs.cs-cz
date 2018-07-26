### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>Xmlschemaexception – správně teď nastavuje pozice řádků

|   |   |
|---|---|
|Podrobnosti|Pokud <xref:System.Xml.Linq.LoadOptions.SetLineInfo> hodnota se předá metodě načíst a dojde k chybě ověření, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> a <xref:System.Xml.Schema.XmlSchemaException.LinePosition> vlastnosti nyní obsahují informace řádku.|
|Návrh|Kód zpracování výjimek, který předpokládá <xref:System.Xml.Schema.XmlSchemaException.LineNumber> a <xref:System.Xml.Schema.XmlSchemaException.LinePosition> nebude sada by měl aktualizovat, protože tyto vlastnosti budou nyní nastavit správně při použití SetLineInfo při načítání XML.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|

