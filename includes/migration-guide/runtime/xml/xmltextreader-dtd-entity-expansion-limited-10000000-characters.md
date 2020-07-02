---
ms.openlocfilehash: fdec6671cbf2dae0d72dfaec07f162058b38cf9d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620113"
---
### <a name="xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>Rozšíření entity DTD třídy XmlTextReader je omezeno na 10 000 000 znaků.

#### <a name="details"></a>Podrobnosti

Rozšíření entity DTD je teď omezené na 10 000 000 znaků. Načítání souborů XML bez rozšíření entity DTD nebo s omezeným rozšířením entity DTD není ovlivněno. Soubory s entitami DTD s rozsahem více než 10 000 000 znaků se nezdaří načíst a vyvolají výjimku.

#### <a name="suggestion"></a>Návrh

Pokud je limit rozšíření entity DTD příliš nízký 10 000 000, hodnota může být přepsána <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities> vlastností. <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName> Do této rutiny je možné předat se správnou hodnotou <code>XmlReader.Create</code> <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> (IE). <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Xml.XmlTextReader?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.Xml.XmlNameTable)></li></ul>|
