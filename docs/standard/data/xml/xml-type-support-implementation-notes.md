---
title: Poznámky k implementaci podpory typů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 73f786c8f1080d0046889958e8b3bd3165870569
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778752"
---
# <a name="xml-type-support-implementation-notes"></a>Poznámky k implementaci podpory typů XML
Toto téma popisuje některé podrobnosti implementace, které chcete mít na paměti.  
  
## <a name="list-mappings"></a>Seznam mapování  
 <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type []**, a <xref:System.String> typy se používají k vyjádření schématu XML definice jazyk (XSD) seznam typů.  
  
## <a name="union-mappings"></a>Mapování typu UNION  
 Typy sjednocení jsou reprezentovány pomocí <xref:System.Xml.Schema.XmlAtomicValue> nebo <xref:System.String> typu. Zdrojový typ nebo typ cíle musí proto vždy být buď <xref:System.String> nebo <xref:System.Xml.Schema.XmlAtomicValue>.  
  
 Pokud <xref:System.Xml.Schema.XmlSchemaDatatype> objekt představuje typ seznamu objektu převede vstupní řetězec hodnotu na seznam jednoho nebo více objektů. Pokud <xref:System.Xml.Schema.XmlSchemaDatatype> představuje typ sjednocení, pak pokusu parsovat vstupní hodnotu jako typ člena sjednocení. Pokud se nezdaří pokus o parsování pak převodu dojde k pokusu o s dalšího člena sjednocení a tak dále až převod je úspěšný, nebo nejsou žádné další členské typy chcete vyzkoušet, v takovém případě je vyvolána výjimka.  
  
## <a name="differences-between-clr-and-xml-data-types"></a>Rozdíly mezi typy dat XML a CLR  
 Následující část popisuje určité problémy, které se mohou vyskytnout mezi typy CLR a typy dat XML a jak se zpracovává.  
  
> [!NOTE]
> `xs` Předpona je namapována na <https://www.w3.org/2001/XMLSchema> a identifikátor URI oboru názvů.
  
### <a name="systemtimespan-and-xsduration"></a>Hodnota System.TimeSpan a značku xs: Duration  
 `xs:duration` Typ je částečně seřazených v, které existují ale ekvivalentní určité hodnoty typu duration, které se liší. To znamená, že pro `xs:duration` hodnota typu, jako je například 1 měsíc (P1M) je menší než 32 dní (P32D) větší než 27 dnů (P27D) a je ekvivalentní se 28, 29 nebo 30 dní.  
  
 <xref:System.TimeSpan> Třída nepodporuje částečné řazení. Místo toho použije určitý počet dní pro 1 rok a 1 měsíc; 365 dnů a 30 dnů v uvedeném pořadí.  
  
 Další informace o `xs:duration` zadejte naleznete v tématu W3C [XML schématu část 2: Datové typy doporučení](https://www.w3.org/TR/xmlschema-2/).
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>: Time gregoriánské datum typy a System.DateTime  
 Při `xs:time` hodnota je namapována na <xref:System.DateTime> objektu, <xref:System.DateTime.MinValue> pole slouží k inicializaci vlastnosti datum <xref:System.DateTime> objektu (, jako <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, a <xref:System.DateTime.Day%2A>) na nejmenší <xref:System.DateTime> hodnotu.  
  
 Obdobně instance `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` a `xs:gMonthDay` mapovaly na <xref:System.DateTime> objektu. Nepoužívané vlastnosti na <xref:System.DateTime> objektu jsou inicializovány na ty z <xref:System.DateTime.MinValue>.  
  
> [!NOTE]
>  Nelze spoléhat na <xref:System.DateTime.Year%2A?displayProperty=nameWithType> hodnotu, pokud je obsah typu `xs:gMonthDay`. <xref:System.DateTime.Year%2A?displayProperty=nameWithType> Hodnota je vždycky nastavený na 1904 v tomto případě.  
  
### <a name="xsanyuri-and-systemuri"></a>xs:anyURI a System.Uri  
 Pokud instance `xs:anyURI` představuje relativní identifikátor URI je namapována na <xref:System.Uri>, <xref:System.Uri> objekt nemá žádné základní identifikátor URI.  
  
## <a name="see-also"></a>Viz také:

- [Podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
