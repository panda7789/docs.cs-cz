### <a name="xslt-style-sheet-exception-message-changed"></a>XSLT styl listu zpráva o výjimce změnit

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5 je text chybové zprávy, pokud je soubor XSLT příliš složitý &quot;šablona stylů je příliš složitý.&quot; V předchozích verzích, chybová zpráva byla &quot;Chyba kompilace XSLT.&quot; Kód aplikace, který závisí na textu chybové zprávy, již nebude fungovat. Ale typy výjimek zůstávají stejné, takže tato změna by neměla mít žádný reálný dopad.|
|Návrh|Aktualizovali veškerý kód aplikace podle toho, zpráva o výjimce z tohoto chybového stavu očekávat novou zprávu, nebo (ještě lepší) aktualizovat kód a závisí jenom na typ výjimky (<xref:System.Xml.Xsl.XsltException?displayProperty=name>), který se nezměnil.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li></ul>|

