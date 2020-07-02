---
ms.openlocfilehash: 5c27e8acdf30533036546ba4cca9e06877bde362
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620117"
---
### <a name="xslt-style-sheet-exception-message-changed"></a>Došlo ke změně zprávy o výjimce šablony stylů XSLT.

#### <a name="details"></a>Podrobnosti

V .NET Framework 4,5 text chybové zprávy, pokud je soubor XSLT příliš složitý, je &quot; Šablona stylů příliš složitá. &quot; V předchozích verzích byla chybová zpráva &quot; chybou kompilace XSLT. &quot; Kód aplikace, který závisí na textu chybové zprávy, již nebude fungovat. Typy výjimek však zůstanou stejné, takže tato změna by neměla mít žádný skutečný dopad.

#### <a name="suggestion"></a>Návrh

Aktualizujte jakýkoli kód aplikace v závislosti na zprávě výjimky z tohoto chybové podmínky, abyste očekávali novou zprávu, nebo (ještě lepší) aktualizovat kód tak, aby byl závislý jenom na typu výjimky ( <xref:System.Xml.Xsl.XsltException?displayProperty=fullName> ), který se nezměnil.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li></ul>|
