---
ms.openlocfilehash: 1f5bc43dcba15c28c179b23352558411f511c82f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981612"
---
### <a name="xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>Rozšíření entity XmlTextReader DTD je omezeno na 10 000 000 znaků

|   |   |
|---|---|
|Podrobnosti|Rozšíření entity DTD je omezeno na 10 000 000 znaků. Načítání souborů XML bez rozšíření entity DTD nebo s omezeným rozšířením entity DTD není ovlivněno. Soubory s entitami DTD s rozsahem více než 10 000 000 znaků se nezdaří načíst a vyvolají výjimku.|
|Doporučení|Pokud limit rozšíření entity DTD je příliš nízká 10 000 000, monitorconfigurationoverride lze přepsat hodnotu <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities> vlastnost. <xref:System.Xml.XmlReaderSettings?displayProperty=name> Správné <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=name> hodnota může být předán <code>XmlReader.Create</code> , která přebírá <xref:System.Xml.XmlReaderSettings?displayProperty=name> (tj. <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>)|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Xml.XmlTextReader?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.Xml.XmlNameTable)?displayProperty=nameWithType></li></ul>|
