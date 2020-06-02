---
title: Poznámky k implementaci podpory typů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
ms.openlocfilehash: 91a685f122ff846217ea7a8677b29df430b65363
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290276"
---
# <a name="xml-type-support-implementation-notes"></a>Poznámky k implementaci podpory typů XML
Toto téma popisuje některé podrobnosti implementace, o kterých chcete vědět.  
  
## <a name="list-mappings"></a>Seznam mapování  
 <xref:System.Collections.IList>Typy, <xref:System.Collections.ICollection> , <xref:System.Collections.IEnumerable> , **Type []**, a <xref:System.String> slouží k reprezentaci typů seznamů schématu definice jazyka XML (XSD).  
  
## <a name="union-mappings"></a>Mapování sjednocení  
 Typy sjednocení jsou reprezentovány pomocí <xref:System.Xml.Schema.XmlAtomicValue> <xref:System.String> typu nebo. Typ zdroje nebo cílový typ musí být proto vždy buď <xref:System.String> nebo <xref:System.Xml.Schema.XmlAtomicValue> .  
  
 Pokud <xref:System.Xml.Schema.XmlSchemaDatatype> objekt představuje typ seznamu, objekt převede hodnotu vstupního řetězce na seznam jednoho nebo více objektů. Pokud <xref:System.Xml.Schema.XmlSchemaDatatype> představuje typ sjednocení, je proveden pokus o analýzu vstupní hodnoty jako člena typu sjednocení. Pokud pokus o analýzu neproběhne úspěšně, je proveden pokus o převod s dalším členem sjednocení a tak dále, dokud převod není úspěšný nebo pokud nejsou k dispozici žádné jiné typy členů k vyzkoušení, v takovém případě je vyvolána výjimka.  
  
## <a name="differences-between-clr-and-xml-data-types"></a>Rozdíly mezi datovými typy CLR a XML  
 Následující popis popisuje určité neshody, ke kterým může dojít mezi typy CLR a datovými typy XML a způsob jejich zpracování.  
  
> [!NOTE]
> `xs`Předpona je namapována na <https://www.w3.org/2001/XMLSchema> identifikátor URI oboru názvů a.
  
### <a name="systemtimespan-and-xsduration"></a>System. TimeSpan a xs: Duration  
 `xs:duration`Typ je částečně seřazen v tom, že existují určité hodnoty doby trvání, které jsou odlišné, ale mají ekvivalent. To znamená, že pro `xs:duration` hodnotu typu, jako je například 1 měsíc (P1M), je méně než 32 dní (P32d), více než 27 dní (P27D) a odpovídá 28, 29 nebo 30 dní.  
  
 <xref:System.TimeSpan>Třída nepodporuje toto částečné řazení. Místo toho vybere určitý počet dní po dobu 1 roku a 1 měsíc. 365 dní a 30 dnů v uvedeném pořadí.  
  
 Další informace o `xs:duration` typu naleznete v [části 2 W3C XML schématu: DataTypes doporučení](https://www.w3.org/TR/xmlschema-2/).
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>xs: Time, gregoriánský datový typ a System. DateTime  
 Pokud `xs:time` je hodnota mapována na <xref:System.DateTime> objekt, <xref:System.DateTime.MinValue> pole slouží k inicializaci vlastností data <xref:System.DateTime> objektu (například <xref:System.DateTime.Year%2A> , <xref:System.DateTime.Month%2A> , a <xref:System.DateTime.Day%2A> ) na nejmenší možnou <xref:System.DateTime> hodnotu.  
  
 Podobně instance,, `xs:gMonth` a `xs:gDay` `xs:gYear` `xs:gYearMonth` `xs:gMonthDay` jsou také mapovány na <xref:System.DateTime> objekt. Nepoužité vlastnosti <xref:System.DateTime> objektu jsou inicializovány do těch z <xref:System.DateTime.MinValue> .  
  
> [!NOTE]
> Nelze spoléhat na hodnotu, <xref:System.DateTime.Year%2A?displayProperty=nameWithType> když je obsah zadán jako `xs:gMonthDay` . <xref:System.DateTime.Year%2A?displayProperty=nameWithType>V tomto případě je hodnota vždy nastavená na 1904.  
  
### <a name="xsanyuri-and-systemuri"></a>xs: anyURI a System. URI  
 Když `xs:anyURI` je instance, která představuje relativní identifikátor URI, namapována na <xref:System.Uri> , <xref:System.Uri> objekt nemá základní identifikátor URI.  
  
## <a name="see-also"></a>Viz také

- [Podpora typu v třídách System.Xml](type-support-in-the-system-xml-classes.md)
