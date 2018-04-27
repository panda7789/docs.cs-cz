### <a name="signedxml-and-encryptedxml-breaking-changes"></a>SignedXml a EncryptedXml nejnovější změny

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2, opravy zabezpečení v <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=name> a <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=name> vést k jiné chování běhu. Například<ul><li>Pokud má více prvků se stejným dokument <code>id</code> atribut a podpis cílem jeden z těchto elementů jako kořen podpis, dokument se teď být považovány za neplatné.</li><li>Dokumenty pomocí-kanonický algoritmy transformace XPath v odkazech na jsou nyní považovány za neplatné.</li><li>Dokumenty pomocí-kanonický algoritmy transformace XSLT v odkazech na jsou nyní považovat za neplatné.</li><li>Žádné program, které využijí externí prostředek odpojit podpisy nelze to učinit.</li></ul>|
|Návrh|Vývojáři chtít přečíst téma použití <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> a <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, stejně jako typy odvozené od <xref:System.Security.Cryptography.Xml.Transform> vzhledem k tomu, že dokument příjemce nemusí být možné zpracovat.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|

