---
title: Poznámky k implementaci podpory typů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
ms.openlocfilehash: 40ab0f746ef82ccd195fc6b873f5c8edb255f868
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709865"
---
# <a name="xml-type-support-implementation-notes"></a>Poznámky k implementaci podpory typů XML
Toto téma popisuje některé podrobnosti implementace, o kterých chcete vědět.  
  
## <a name="list-mappings"></a>Seznam mapování  
 <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type []** a typy <xref:System.String> slouží k reprezentaci typů seznamů schématu definice jazyka XML (XSD).  
  
## <a name="union-mappings"></a>Mapování sjednocení  
 Typy sjednocení jsou reprezentovány pomocí <xref:System.Xml.Schema.XmlAtomicValue> nebo <xref:System.String>ho typu. Typ zdroje nebo cílový typ musí proto vždy být buď <xref:System.String>, nebo <xref:System.Xml.Schema.XmlAtomicValue>.  
  
 Pokud objekt <xref:System.Xml.Schema.XmlSchemaDatatype> představuje typ seznamu, objekt převede hodnotu vstupního řetězce na seznam jednoho nebo více objektů. Pokud <xref:System.Xml.Schema.XmlSchemaDatatype> představuje typ sjednocení, provede se pokus o analýzu vstupní hodnoty jako typu členu sjednocení. Pokud pokus o analýzu neproběhne úspěšně, je proveden pokus o převod s dalším členem sjednocení a tak dále, dokud převod není úspěšný nebo pokud nejsou k dispozici žádné jiné typy členů k vyzkoušení, v takovém případě je vyvolána výjimka.  
  
## <a name="differences-between-clr-and-xml-data-types"></a>Rozdíly mezi datovými typy CLR a XML  
 Následující popis popisuje určité neshody, ke kterým může dojít mezi typy CLR a datovými typy XML a způsob jejich zpracování.  
  
> [!NOTE]
> Předpona `xs` je namapována na <https://www.w3.org/2001/XMLSchema> a identifikátor URI oboru názvů.
  
### <a name="systemtimespan-and-xsduration"></a>System. TimeSpan a xs: Duration  
 Typ `xs:duration` je částečně seřazen v tom, že existují určité hodnoty doby trvání, které jsou odlišné, ale mají ekvivalent. To znamená, že pro `xs:duration` hodnota typu, jako je například 1 měsíc (P1M), je menší než 32 dní (P32D), více než 27 dní (P27D) a odpovídá 28, 29 nebo 30 dní.  
  
 Třída <xref:System.TimeSpan> nepodporuje toto částečné řazení. Místo toho vybere určitý počet dní po dobu 1 roku a 1 měsíc. 365 dní a 30 dnů v uvedeném pořadí.  
  
 Další informace o typu `xs:duration` naleznete v [části 2 W3C XML schématu: doporučení k datatypeům](https://www.w3.org/TR/xmlschema-2/).
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>xs: Time, gregoriánský datový typ a System. DateTime  
 Pokud je hodnota `xs:time` namapována na objekt <xref:System.DateTime>, pole <xref:System.DateTime.MinValue> slouží k inicializaci vlastností data objektu <xref:System.DateTime> (například <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>a <xref:System.DateTime.Day%2A>) na nejmenší možno <xref:System.DateTime> hodnotu.  
  
 Podobně jsou instance `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` a `xs:gMonthDay` namapovány také na objekt <xref:System.DateTime>. Nepoužité vlastnosti objektu <xref:System.DateTime> jsou inicializovány do těch z <xref:System.DateTime.MinValue>.  
  
> [!NOTE]
> Pokud je obsah zadán jako `xs:gMonthDay`, nelze spoléhat na hodnotu <xref:System.DateTime.Year%2A?displayProperty=nameWithType>. V tomto případě je hodnota <xref:System.DateTime.Year%2A?displayProperty=nameWithType> vždy nastavená na 1904.  
  
### <a name="xsanyuri-and-systemuri"></a>xs: anyURI a System. URI  
 Když je instance `xs:anyURI` představující relativní identifikátor URI namapována na <xref:System.Uri>, objekt <xref:System.Uri> nemá základní identifikátor URI.  
  
## <a name="see-also"></a>Viz také:

- [Podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
