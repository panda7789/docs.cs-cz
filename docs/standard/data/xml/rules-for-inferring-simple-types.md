---
title: Pravidla pro jednoduché typy odvození
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 394624d6-4da0-430a-8a88-46efe40f14de
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d265d9247d00a20770d401d62fd1e065e2ef1627
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="rules-for-inferring-simple-types"></a>Pravidla pro jednoduché typy odvození
Popisuje, jak <xref:System.Xml.Schema.XmlSchemaInference> třída odvodí datový typ pro atributy a elementy.  
  
 <xref:System.Xml.Schema.XmlSchemaInference> Třída odvodí datový typ pro atributy a elementy jako jednoduché typy. Tato část popisuje potenciální odvozené typy, jak více odlišné hodnoty jsou sloučeny do jednoho typu a jak definování schématu `xsi` atributy jsou zpracovány.  
  
## <a name="inferred-types"></a>Odvozené typy  
 <xref:System.Xml.Schema.XmlSchemaInference> Třída odvodí elementu a atributu hodnoty jako jednoduché typy a obsahuje atribut typu ve schématu výsledné. Všechny odvozené typy jsou jednoduché typy. Žádné základní typy nebo omezující vlastnosti jsou zahrnuty jako součást výsledné schématu.  
  
 Jak se vyskytují v dokumentu XML se jednotlivě zkontrolují hodnoty. Typ je v době, kdy je zkontrolován odvodit pro hodnotu. Pokud byla vyvozena typu pro element nebo atribut a je zjištěna hodnota elementu nebo atributu, který neodpovídá typ aktuálně odvozené <xref:System.Xml.Schema.XmlSchemaInference> třída podporuje typ pro každou sadu pravidel. Tato pravidla jsou popsané v části Typ povýšení později v tomto tématu.  
  
 Následující tabulka uvádí možné typy odvozené pro výsledný schématu.  
  
|Jednoduchý typ|Popis|  
|-----------------|-----------------|  
|Logická hodnota|Hodnota TRUE, false, 0, 1.|  
|byte|Celá čísla v rozsahu – 128 127 znaků.|  
|unsignedByte|Celá čísla v rozsahu od 0 do 255.|  
|short|Celá čísla v rozsahu –32768 do 32767.|  
|unsignedShort|Celá čísla v rozsahu 0 až 65535.|  
|int|Celá čísla v rozsahu –2147483648 do 2147483647.|  
|celé číslo bez znaménka|Celá čísla v rozsahu od 0 do 4294967295.|  
|long|Celá čísla v rozsahu –9223372036854775808 k 9223372036854775807.|  
|unsignedLong|Celá čísla v rozsahu od 0 do 18446744073709551615.|  
|integer|Konečný počet číslic, které by mohly mít předponu "-".|  
|decimal|Číselné hodnoty, které obsahují od 0 do 28 platných číslic.|  
|float|Může volitelně následovat "E" nebo "e" a celočíselnou hodnotu představující exponent desetinných míst. Desetinná čísla může být v rozsahu-16777216 k 16777216. Exponentu hodnoty mohou být v rozsahu –149 k 104.<br /><br /> Float umožňuje speciální hodnoty k reprezentaci infinity a jiné než číselné hodnoty. Float speciální hodnoty jsou: 0, - 0, INF, -INF, NaN.|  
|double|Stejné jako float kromě desetinných míst může být v rozsahu-9007199254740992 k 9007199254740992 a exponentu hodnoty mohou být v rozsahu –1075 k 970.<br /><br /> Dvojitý umožňuje speciální hodnoty k reprezentaci infinity a jiné než číselné hodnoty. Float speciální hodnoty jsou: 0, - 0, INF, -INF, NaN.|  
|doba trvání|Doba trvání formátu W3C.|  
|data a času.|Formát data a času W3C.|  
|čas|Formát času W3C.|  
|Datum|Rok hodnoty jsou omezeny z 0001 až 9999.|  
|gYearMonth|W3C gregoriánský měsíci a roce formát.|  
|odkazy řetězců|Jeden nebo více znaků Unicode.|  
  
## <a name="type-promotion"></a>Propagace typu  
 <xref:System.Xml.Schema.XmlSchemaInference> Třída prozkoumá hodnoty elementu a atributu jeden najednou. Jako hodnoty jsou došlo, je odvodit typ nejvíc omezující bez znaménka. Pokud byla vyvozena typu pro element nebo atribut a je došlo novou hodnotu, která neodpovídá aktuálně odvozeném typu, je odvozeném typu povýšit na nový typ, který se vztahují na aktuálně odvozeném typu a nová hodnota. <xref:System.Xml.Schema.XmlSchemaInference> Třída zvažte předchozí hodnoty, při povýšení odvozeném typu.  
  
 Zvažte například následující fragmenty XML z dva dokumenty XML:  
  
 `<MyElement1 attr1="12" />`  
  
 `<MyElement1 attr1="52344" />`  
  
 Při první `attr1` je zjištěna hodnota, typ `attr1` je odvodit jako `unsignedByte` na základě hodnoty `12`. Když druhý `attr1` je došlo, typ je propagována do `unsignedShort` na základě aktuálně odvozené typu `unsignedByte` a že je aktuální hodnota `52344`.  
  
 Nyní zvažte následující kód XML z dva dokumenty XML:  
  
 `<MyElement2 attr2="0" />`  
  
 `<MyElement2 attr2="true" />`  
  
 Při první `attr2` je zjištěna hodnota, typ `attr2` je odvodit jako `unsignedByte` na základě hodnoty `0`. Při druhý `attr2` je došlo, typ je propagována do `string` na základě aktuálně odvozené typu `unsignedByte` a že je aktuální hodnota `true` protože <xref:System.Xml.Schema.XmlSchemaInference> třída zvažte předchozí hodnoty, při povýšení odvodit typ. Ale pokud obě instance `attr2` byly zjištěny ve stejném dokumentu XML a není ve dvou různých dokumentů XML, jak je popsáno výše, `attr2` by byla vyvozena jako `boolean`.  
  
### <a name="ignored-attributes-from-the-httpwwww3org2001xmlschema-instance-namespace"></a>Ignorovat atributů z http://www.w3.org/2001/XMLSchema-instance Namespace  
 Následují definice schématu atributů, které během odvození schématu jsou ignorovány.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`xsi:type`|Pokud je element s `xsi:type` zadána, `xsi:type` je ignorována.|  
|`xsi:nil`|Pokud element s `xsi:nil` zjištěn atribut, jeho deklaraci elementu v odvozené schématu má hodnotu `nillable="true"`. Element s `xsi:nil` atribut nastaven na `true` nemohou mít podřízené elementy.|  
|`xsi:schemaLocation`|Pokud `xsi:schemaLocation` je došlo, je ignorováno.|  
|`xsi:noNamespaceSchemaLocation`|Pokud `xsi:noNamespaceSchemaLocation` je došlo, je ignorováno.|  
  
## <a name="see-also"></a>Viz také  
 [Model objektu schématu (SOM) XML](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 [Odvození schémat z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)  
 [Pravidla pro odvození typů a struktury uzlů schémat](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
