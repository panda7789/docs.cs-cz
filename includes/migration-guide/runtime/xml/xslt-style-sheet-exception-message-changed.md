### <a name="xslt-style-sheet-exception-message-changed"></a>XSLT style sheet zpráva o výjimce změnit

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5, je text chybové zprávy, když soubor XSLT je příliš složitý &quot;šablony stylů je příliš složitý.&quot; V předchozích verzích se chybová zpráva byla &quot;Chyba kompilace XSLT.&quot; Kód aplikace, který závisí na textu chybové zprávy, již nebude fungovat. Ale typy výjimek zůstávají stejné, takže tato změna by měl mít žádný skutečný dopad.|
|Návrh|Aktualizovat kód aplikace, v závislosti na zpráva o výjimce z tento chybový stav očekávat novou zprávu, nebo (i lépe) aktualizovat kód, který závisí pouze na typ výjimky (<xref:System.Xml.Xsl.XsltException?displayProperty=name>), které nebylo změněno.|
|Rozsah|Edge|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li></ul>|

