---
title: Poznámky k implementaci podpory typů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 817d48e15f3a1d370e1953ca9c9aa8e10baa7f29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916032"
---
# <a name="xml-type-support-implementation-notes"></a>Poznámky k implementaci podpory typů XML
Toto téma popisuje některé podrobnosti implementace, o kterých chcete vědět.  
  
## <a name="list-mappings"></a>Seznam mapování  
 <xref:System.String> Typy, <xref:System.Collections.ICollection>, ,<xref:System.Collections.IEnumerable> **Type []** , a slouží k reprezentaci typů seznamů schématu definice jazyka XML (XSD). <xref:System.Collections.IList>  
  
## <a name="union-mappings"></a>Mapování sjednocení  
 Typy sjednocení jsou reprezentovány <xref:System.String> pomocí <xref:System.Xml.Schema.XmlAtomicValue> typu nebo. Typ zdroje nebo cílový typ musí být proto vždy buď <xref:System.String> nebo. <xref:System.Xml.Schema.XmlAtomicValue>  
  
 <xref:System.Xml.Schema.XmlSchemaDatatype> Pokud objekt představuje typ seznamu, objekt převede hodnotu vstupního řetězce na seznam jednoho nebo více objektů. <xref:System.Xml.Schema.XmlSchemaDatatype> Pokud představuje typ sjednocení, je proveden pokus o analýzu vstupní hodnoty jako člena typu sjednocení. Pokud pokus o analýzu neproběhne úspěšně, je proveden pokus o převod s dalším členem sjednocení a tak dále, dokud převod není úspěšný nebo pokud nejsou k dispozici žádné jiné typy členů k vyzkoušení, v takovém případě je vyvolána výjimka.  
  
## <a name="differences-between-clr-and-xml-data-types"></a>Rozdíly mezi datovými typy CLR a XML  
 Následující popis popisuje určité neshody, ke kterým může dojít mezi typy CLR a datovými typy XML a způsob jejich zpracování.  
  
> [!NOTE]
> Předpona je namapována <https://www.w3.org/2001/XMLSchema> na identifikátor URI oboru názvů a. `xs`
  
### <a name="systemtimespan-and-xsduration"></a>System. TimeSpan a xs: Duration  
 `xs:duration` Typ je částečně seřazen v tom, že existují určité hodnoty doby trvání, které jsou odlišné, ale mají ekvivalent. To znamená, že pro `xs:duration` hodnotu typu, jako je například 1 měsíc (P1M), je méně než 32 dní (P32d), více než 27 dní (P27D) a odpovídá 28, 29 nebo 30 dní.  
  
 <xref:System.TimeSpan> Třída nepodporuje toto částečné řazení. Místo toho vybere určitý počet dní po dobu 1 roku a 1 měsíc. 365 dní a 30 dnů v uvedeném pořadí.  
  
 Další informace o `xs:duration` typu najdete v části 2 W3C [XML schématu: Doporučení](https://www.w3.org/TR/xmlschema-2/)pro DataTypes.
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>xs: Time, gregoriánský datový typ a System. DateTime  
 <xref:System.DateTime> <xref:System.DateTime.Day%2A> <xref:System.DateTime.Year%2A> <xref:System.DateTime.Month%2A>Pokud je <xref:System.DateTime> hodnota mapována na objekt, <xref:System.DateTime.MinValue> pole se používá k inicializaci vlastností data objektu (například,, a) na nejmenší možnou hodnotu. `xs:time` <xref:System.DateTime> hodnota.  
  
 Podobně `xs:gMonth`instance `xs:gDay` <xref:System.DateTime> ,, a jsoutakémapoványnaobjekt.`xs:gMonthDay` `xs:gYear` `xs:gYearMonth` Nepoužité vlastnosti <xref:System.DateTime> objektu jsou inicializovány do těch <xref:System.DateTime.MinValue>z.  
  
> [!NOTE]
> Nelze spoléhat na <xref:System.DateTime.Year%2A?displayProperty=nameWithType> hodnotu, když je obsah zadán jako `xs:gMonthDay`. V tomto případě je hodnotavždynastavenána1904.<xref:System.DateTime.Year%2A?displayProperty=nameWithType>  
  
### <a name="xsanyuri-and-systemuri"></a>xs: anyURI a System. URI  
 Když je instance `xs:anyURI` , která představuje relativní identifikátor URI <xref:System.Uri>, namapována na, <xref:System.Uri> objekt nemá základní identifikátor URI.  
  
## <a name="see-also"></a>Viz také:

- [Podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
