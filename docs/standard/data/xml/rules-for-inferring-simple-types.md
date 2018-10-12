---
title: Pravidla pro odvození jednoduchých typů
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 394624d6-4da0-430a-8a88-46efe40f14de
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2477b55f38167cc3497979d073f74d441a06f96d
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123576"
---
# <a name="rules-for-inferring-simple-types"></a>Pravidla pro odvození jednoduchých typů
Popisuje, jak <xref:System.Xml.Schema.XmlSchemaInference> třídy odvodí typ dat pro atributy a elementy.  
  
 <xref:System.Xml.Schema.XmlSchemaInference> Třídy odvodí typ dat pro atributy a prvky jako jednoduché typy. Tato část popisuje potenciální odvozené typy, jak několika rozdílné hodnoty jsou sloučeny do jednoho typu a jak definovat schéma `xsi` atributy jsou zpracovány.  
  
## <a name="inferred-types"></a>Odvozené typy  
 <xref:System.Xml.Schema.XmlSchemaInference> Třídy odvodí elementu a atribut hodnoty jako jednoduché typy a obsahuje atribut typu v výsledný schéma. Odvodit všechny typy jsou jednoduché typy. Žádné základní typy nebo omezující vlastnosti jsou zahrnuty jako součást výsledný schéma.  
  
 Hodnoty jsou zkoumány samostatně, jak se vyskytují v dokumentu XML. Typ je odvozen pro hodnoty v době, kdy je zkontrolován. Pokud se pro atribut nebo element byl odvozen typ a hodnotu pro atribut nebo element, který neodpovídá aktuálně odvozený typ, dochází <xref:System.Xml.Schema.XmlSchemaInference> třídy podporuje typ pro každou sadu pravidel. Tato pravidla jsou popsány v části Typ povýšení později v tomto tématu.  
  
 Následující tabulka uvádí možné typy odvozené pro výsledný schéma.  
  
|Jednoduchý typ.|Popis|  
|-----------------|-----------------|  
|Logická hodnota|Hodnota TRUE, false, 0, 1.|  
|byte|Celá čísla v rozsahu od – 128 do 127.|  
|unsignedByte|Celá čísla v rozsahu od 0 do 255.|  
|short|Celá čísla v rozsahu –32768 do 32767.|  
|unsignedShort|Celá čísla v rozsahu 0 až 65535.|  
|int|Celá čísla v rozsahu –2147483648 do 2147483647.|  
|celé číslo bez znaménka|Celá čísla v rozsahu od 0 do 4294967295.|  
|long|Celá čísla v rozsahu –9223372036854775808 k 9223372036854775807.|  
|unsignedLong|Celá čísla v rozsahu 0 – 18446744073709551615.|  
|integer|Konečný počet číslic, případně s předponou "-".|  
|decimal|Číselné hodnoty, které se skládat z 0 až 28 platných číslic.|  
|float|Desetinná místa může volitelně následovat "E" nebo "e" následované celočíselnou hodnotu představující exponent. Desetinné hodnoty mohou být v rozsahu-16777216 k 16777216. Exponent hodnoty mohou být v rozsahu –149 na 104.<br /><br /> Plovoucí desetinnou čárkou umožňuje pro zvláštní hodnoty k reprezentování nekonečna a jiné než číselné hodnoty. Speciální hodnoty typu float: 0, - 0, INF, -INF, NaN.|  
|double|Stejné jako plovoucí desetinnou čárkou s výjimkou desetinné hodnoty můžou být v rozsahu-9007199254740992 k 9007199254740992 a exponentu hodnoty mohou být v rozsahu –1075 k 970.<br /><br /> Double umožňuje pro zvláštní hodnoty k reprezentování nekonečna a jiné než číselné hodnoty. Speciální hodnoty typu float: 0, - 0, INF, -INF, NaN.|  
|doba trvání|Formát doby trvání W3C.|  
|data a času.|Formát data a času ve formátu W3C.|  
|čas|Formát času W3C.|  
|Datum|Hodnoty roku zakázáno 0001 až 9999.|  
|gYearMonth|W3C gregoriánský měsíc a rok formátu.|  
|odkazy řetězců|Jeden nebo více znaků Unicode.|  
  
## <a name="type-promotion"></a>Propagace typu  
 <xref:System.Xml.Schema.XmlSchemaInference> Třída zkontroluje hodnoty elementu a atributu jeden po druhém. Podle výskytu hodnoty nejvíce omezující bez znaménka typ je odvozen. Pokud byl odvozen typ pro atribut nebo element a novou hodnotu, která se neshoduje s aktuálně odvozený typ narazí, odvozený typ je povýšen na nový typ, který se vztahuje na aktuálně odvozený typ a nová hodnota. <xref:System.Xml.Schema.XmlSchemaInference> Třídy při zvyšování úrovně odvozený typ zvažte předchozí hodnoty.  
  
 Představte si třeba následující fragmentů XML ze dvou dokumentů XML:  
  
 `<MyElement1 attr1="12" />`  
  
 `<MyElement1 attr1="52344" />`  
  
 Při první `attr1` zjištěna hodnota je typu `attr1` je odvozený jako `unsignedByte` na základě hodnoty `12`. Při druhém `attr1` je nalezen, typ je povýšen na `unsignedShort` podle aktuálně odvozený typ `unsignedByte` a aktuální hodnotou `52344`.  
  
 Nyní zvažte následující kód XML ze dvou dokumentů XML:  
  
 `<MyElement2 attr2="0" />`  
  
 `<MyElement2 attr2="true" />`  
  
 Při první `attr2` zjištěna hodnota je typu `attr2` je odvozený jako `unsignedByte` na základě hodnoty `0`. Při druhý `attr2` je zjištěna, typ je povýšen na `string` podle aktuálně odvozený typ `unsignedByte` a aktuální hodnotou `true` protože <xref:System.Xml.Schema.XmlSchemaInference> třídy zvažte předchozí hodnoty, při zvyšování úrovně odvození typu. Nicméně pokud obě instance `attr2` byly zjištěny ve stejném dokumentu XML a nejsou ve dvou různých dokumentů XML, jak je znázorněno výše, `attr2` by byl odvozen jako `boolean`.  
  
### <a name="ignored-attributes-from-the-httpswwww3org2001xmlschema-instance-namespace"></a>Ignorovat atributů z <https://www.w3.org/2001/XMLSchema-instance> obor názvů

Definování schématu jsou následující atributy, které jsou ignorovány při odvozování schématu.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`xsi:type`|Pokud je element s `xsi:type` zadán, `xsi:type` se ignoruje.|  
|`xsi:nil`|Pokud element s `xsi:nil` zjištěn atribut, jeho deklaraci elementu ve schématu odvozené má hodnotu `nillable="true"`. Element s `xsi:nil` atribut nastaven na `true` nemůže mít podřízené elementy.|  
|`xsi:schemaLocation`|Pokud `xsi:schemaLocation` je nalezen, je ignorována.|  
|`xsi:noNamespaceSchemaLocation`|Pokud `xsi:noNamespaceSchemaLocation` je nalezen, je ignorována.|  
  
## <a name="see-also"></a>Viz také:

- [Model objektu schématu (SOM) XML](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
- [Odvození schémat z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)  
- [Pravidla pro odvození typů a struktury uzlů schémat](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
