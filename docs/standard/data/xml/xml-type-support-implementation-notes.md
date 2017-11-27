---
title: "Poznámky k implementaci XML typu podpory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5e99573fc3a82db7798426172a13a78e10c65636
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xml-type-support-implementation-notes"></a>Poznámky k implementaci XML typu podpory
Toto téma popisuje některé podrobnosti implementace, které chcete mít na paměti.  
  
## <a name="list-mappings"></a>Seznam mapování  
 <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Zadejte []**, a <xref:System.String> typy se používají k vyjádření schématu XML definition language (XSD) seznamu typů.  
  
## <a name="union-mappings"></a>Union mapování  
 Union typy jsou reprezentované pomocí <xref:System.Xml.Schema.XmlAtomicValue> nebo <xref:System.String> typu. Typ zdroje nebo typ cílového proto musí být vždy buď <xref:System.String> nebo <xref:System.Xml.Schema.XmlAtomicValue>.  
  
 Pokud <xref:System.Xml.Schema.XmlSchemaDatatype> objekt představuje typ seznamu převede objekt vstupní řetězec hodnotu na seznam jeden nebo více objektů. Pokud <xref:System.Xml.Schema.XmlSchemaDatatype> představuje typu union, pak je proveden pokus o vstupní hodnotu analyzovat jako typ člena unie. Pokud se nezdaří pokus o analýzy pak převod je k pokusu o dalšího člena sjednocení a tak dále dokud převod je úspěšné, nebo nejsou žádné jiné typy člena a zkuste to, v takovém případě je vyvolána výjimka.  
  
## <a name="differences-between-clr-and-xml-data-types"></a>Rozdíly mezi datové typy XML a CLR  
 Následující část popisuje některé problémy, o kterých může proběhnout mezi typy CLR a datové typy XML a jak jsou zpracovávány.  
  
> [!NOTE]
>  `xs` Předpona je namapována na http://www.w3.org/2001/XMLSchema a identifikátor URI oboru názvů.  
  
### <a name="systemtimespan-and-xsduration"></a>System.TimeSpan a xs  
 `xs:duration` Typ je částečně pořadí, v tom, že existují ale ekvivalentní určité hodnoty doby trvání, které se liší. To znamená, že pro `xs:duration` hodnota typu, například 1 měsíc (P1M) je menší než 32 dní (P32D) větší než 27 dní (P27D), odpovídající 28, 29 nebo 30 dnů.  
  
 <xref:System.TimeSpan> Třída nepodporuje toto částečné řazení. Místo toho se vybere určitý počet dní pro 1 rok a 1 měsíce; 365 dnů a 30 dní v uvedeném pořadí.  
  
 Další informace o `xs:duration` zadejte najdete v tématu W3C XML schéma část 2: datové typy doporučení v http://www.w3.org/TR/xmlschema-2/.  
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>: Time, typy Datum gregoriánského a System.DateTime  
 Při `xs:time` hodnota je namapována na <xref:System.DateTime> objekt, <xref:System.DateTime.MinValue> pole slouží k inicializaci vlastnosti kalendářních dat u <xref:System.DateTime> objektu (například <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, a <xref:System.DateTime.Day%2A>) na nejmenší možné <xref:System.DateTime> hodnotu.  
  
 Podobně instancí `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` a `xs:gMonthDay` taky namapovaný na <xref:System.DateTime> objektu. Nepoužívané vlastnosti <xref:System.DateTime> objekt jsou inicializovány na ty z <xref:System.DateTime.MinValue>.  
  
> [!NOTE]
>  Nelze spoléhat na <xref:System.DateTime.Year%2A?displayProperty=nameWithType> hodnotu, pokud je obsah typu `xs:gMonthDay`. <xref:System.DateTime.Year%2A?displayProperty=nameWithType> Hodnota je vždycky nastavený na 1904 v tomto případě.  
  
### <a name="xsanyuri-and-systemuri"></a>xs:anyURI a System.Uri  
 Pokud instance `xs:anyURI` představuje relativní identifikátor URI je namapována na <xref:System.Uri>, <xref:System.Uri> objekt nemá základní identifikátor URI.  
  
## <a name="see-also"></a>Viz také  
 [Podpora typu v System.Xml třídy](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
