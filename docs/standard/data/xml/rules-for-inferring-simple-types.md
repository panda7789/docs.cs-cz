---
title: Pravidla pro odvození jednoduchých typů
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 394624d6-4da0-430a-8a88-46efe40f14de
ms.openlocfilehash: 17429e77f7764873e607a8feaa62da1cc6e014a4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710229"
---
# <a name="rules-for-inferring-simple-types"></a>Pravidla pro odvození jednoduchých typů
Popisuje, jak třída <xref:System.Xml.Schema.XmlSchemaInference> odvodí datový typ pro atributy a elementy.  
  
 Třída <xref:System.Xml.Schema.XmlSchemaInference> odvodí datový typ pro atributy a elementy jako jednoduché typy. Tato část popisuje potenciální odvozené typy, způsob, jakým jsou více různých hodnot sloučeny na jeden typ a jak jsou zpracovávány atributy definující `xsi` schématu.  
  
## <a name="inferred-types"></a>Odvozené typy  
 Třída <xref:System.Xml.Schema.XmlSchemaInference> odvodí element a hodnoty atributu jako jednoduché typy a obsahuje atribut typu ve výsledném schématu. Všechny odvozené typy jsou jednoduché typy. Jako součást výsledného schématu nejsou zahrnuté žádné základní typy ani omezující vlastnosti.  
  
 Hodnoty jsou zkontrolovány jednotlivě, jak jsou zjištěny v dokumentu XML. Typ je odvozený pro hodnotu v okamžiku, kdy je vyhodnocena. Pokud byl typ odvozen pro atribut nebo element a byla zjištěna hodnota atributu nebo elementu, která neodpovídá aktuálně odvozenému typu, třída <xref:System.Xml.Schema.XmlSchemaInference> propaguje typ pro každou sadu pravidel. Tato pravidla jsou popsána v části propagace typů dále v tomto tématu.  
  
 V následující tabulce jsou uvedeny možné odvozené typy pro výsledné schéma.  
  
|Jednoduchý typ|Popis|  
|-----------------|-----------------|  
|Logická hodnota|True, false, 0, 1.|  
|byte|Celá čísla v rozsahu od – 128 do 127.|  
|unsignedByte|Celá čísla v rozsahu od 0 do 255.|  
|short|Celá čísla v rozsahu od – 32768 do 32767.|  
|unsignedShort|Celá čísla v rozsahu od 0 do 65535.|  
|int|Celá čísla v rozsahu od – 2147483648 do 2147483647.|  
|unsignedInt|Celá čísla v rozsahu od 0 do 4294967295.|  
|long|Celá čísla v rozsahu od – 9223372036854775808 do 9223372036854775807.|  
|unsignedLong|Celá čísla v rozsahu od 0 do 18446744073709551615.|  
|integer|Konečný počet číslic může být předponou "-".|  
|decimal|Číselné hodnoty, které obsahují 0 až 28 číslic přesnosti.|  
|float|Desetinná místa volitelně následované "E" nebo "e" následovaná celočíselnou hodnotou představující exponent. Desítkové hodnoty můžou být v rozsahu od-16777216 do 16777216. Hodnoty exponentu můžou být v rozsahu od – 149 do 104.<br /><br /> Float umožňuje, aby speciální hodnoty představovaly nekonečno a jiné než číselné hodnoty. Speciální hodnoty pro float jsou: 0,-0, INF,-INF, NaN.|  
|double|Stejné jako float s výjimkou desetinných hodnot můžou být v rozsahu-9007199254740992 až 9007199254740992 a hodnoty exponentu můžou být v rozsahu od – 1075 do 970.<br /><br /> Double umožňuje, aby speciální hodnoty představovaly nekonečno a jiné než číselné hodnoty. Speciální hodnoty pro float jsou: 0,-0, INF,-INF, NaN.|  
|doba trvání|Formát doby trvání W3C.|  
|data a času.|Formát data a času W3C.|  
|čas|Formát času W3C.|  
|Datum|Hodnoty roku jsou omezeny z 0001 na 9999.|  
|gYearMonth|Gregoriánský formát měsíce a roku W3C.|  
|odkazy řetězců|Jeden nebo více znaků Unicode.|  
  
## <a name="type-promotion"></a>Propagace typu  
 Třída <xref:System.Xml.Schema.XmlSchemaInference> kontroluje jednu po druhé hodnoty atributu a elementu. V případě, že jsou zjištěny hodnoty, je odvozeno nejvíce omezující typ bez znaménka. Pokud byl typ odvozen pro atribut nebo element a byla zjištěna nová hodnota, která neodpovídá aktuálně odvozenému typu, odvozený typ je povýšen na nový typ, který se vztahuje na aktuálně odvozený typ i na novou hodnotu. Třída <xref:System.Xml.Schema.XmlSchemaInference> při povýšení odvozeného typu zváží předchozí hodnoty.  
  
 Zvažte například následující fragmenty kódu XML ze dvou dokumentů XML:  
  
 `<MyElement1 attr1="12" />`  
  
 `<MyElement1 attr1="52344" />`  
  
 Při výskytu první `attr1` hodnoty je typ `attr1` odvozen jako `unsignedByte` na základě hodnoty `12`. Když se vyskytne druhý `attr1`, je typ povýšen na `unsignedShort` na základě aktuálně odvozeného typu `unsignedByte` a aktuální hodnoty `52344`.  
  
 Nyní zvažte následující XML ze dvou dokumentů XML:  
  
 `<MyElement2 attr2="0" />`  
  
 `<MyElement2 attr2="true" />`  
  
 Při výskytu první `attr2` hodnoty je typ `attr2` odvozen jako `unsignedByte` na základě hodnoty `0`. Když se vyskytne druhý `attr2`, je typ povýšen na `string` na základě aktuálně odvozeného typu `unsignedByte` a aktuální hodnoty `true`, protože třída <xref:System.Xml.Schema.XmlSchemaInference> při zvýšení úrovně odvozeného typu zváží předchozí hodnoty. Pokud však byly nalezeny obě instance `attr2` ve stejném dokumentu XML a nikoli ve dvou různých dokumentech XML, jak je znázorněno výše, `attr2` by bylo odvozeno jako `boolean`.  
  
### <a name="ignored-attributes-from-the-httpswwww3org2001xmlschema-instance-namespace"></a>Ignorované atributy z oboru názvů <https://www.w3.org/2001/XMLSchema-instance>

Níže jsou atributy definující schéma, které jsou ignorovány během odvození schématu.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`xsi:type`|Pokud je nalezen element se zadaným `xsi:type`, `xsi:type` je ignorováno.|  
|`xsi:nil`|Pokud je nalezen element s atributem `xsi:nil`, jeho deklarace elementu v odvozeném schématu má hodnotu `nillable="true"`. Element s atributem `xsi:nil` nastaveným na `true` nemůže mít podřízené prvky.|  
|`xsi:schemaLocation`|Pokud dojde k `xsi:schemaLocation`, ignoruje se.|  
|`xsi:noNamespaceSchemaLocation`|Pokud dojde k `xsi:noNamespaceSchemaLocation`, ignoruje se.|  
  
## <a name="see-also"></a>Viz také:

- [Model objektu schématu (SOM) XML](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
- [Odvození schémat z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)
- [Pravidla pro odvození typů a struktury uzlů schémat](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
