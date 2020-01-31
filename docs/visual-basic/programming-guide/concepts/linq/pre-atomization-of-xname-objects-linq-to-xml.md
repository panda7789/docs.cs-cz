---
title: Předběžná atomizace objektů XName (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: c0e75afa797d2b20f32fc55e6c19d0c1593d174c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740794"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>Předběžná Atomace objektů XName (LINQ to XML) (Visual Basic)

Jedním ze způsobů, jak zlepšit výkon v LINQ to XML, je atomizovat <xref:System.Xml.Linq.XName> objektů. Před vytvořením stromu XML pomocí konstruktorů tříd <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> je třeba před vytvořením stromu XML přiřadit řetězec <xref:System.Xml.Linq.XName> objektu. Místo předání řetězce konstruktoru, který by použil implicitní převod z řetězce na <xref:System.Xml.Linq.XName>, předáte inicializovaný objekt <xref:System.Xml.Linq.XName>.

To zlepšuje výkon při vytváření velkého stromu XML, ve kterém se konkrétní názvy opakují. Chcete-li to provést, deklarujete a inicializujete <xref:System.Xml.Linq.XName> objektů před vytvořením stromu XML a poté místo určení řetězců pro element a atributy atributu použít objekty <xref:System.Xml.Linq.XName>. Tato technika může přinést výrazné zvýšení výkonu, pokud vytváříte velký počet prvků (nebo atributů) se stejným názvem.

Před tím, než se rozhodnete, jestli ho chcete použít, byste měli testovat předběžnou atomaci ve svém scénáři.

## <a name="example"></a>Příklad

Následující příklad ukazuje toto:

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

Tento příklad vytvoří následující výstup:

```xml
<Root>
  <Data ID="1">4,100,000</Data>
  <Data ID="2">3,700,000</Data>
  <Data ID="3">1,150,000</Data>
</Root>
```

Následující příklad ukazuje stejnou techniku, kde je dokument XML v oboru názvů:

```vb
Dim aw As XNamespace = "http://www.adventure-works.com"
Dim root1 As XName = aw + "Root"
Dim data As XName = aw + "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XAttribute(XNamespace.Xmlns + "aw", aw),
                          New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

Tento příklad vytvoří následující výstup:

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Data ID="1">4,100,000</aw:Data>
  <aw:Data ID="2">3,700,000</aw:Data>
  <aw:Data ID="3">1,150,000</aw:Data>
</aw:Root>
```

Následující příklad se podobá tomu, co se vám pravděpodobně setkáte v reálném světě. V tomto příkladu je obsah elementu dodán dotazem:

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"
  
Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root2 As New XElement(root1, From i In Enumerable.Range(1, 100000)
                                 Select New XElement(data, New XAttribute(ID, i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```  

Předchozí příklad provede lepší, než následující příklad, ve kterém názvy nejsou předběžně atomované:

```vb
Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root As New XElement("Root", From i In Enumerable.Range(1, 100000)
                                 Select New XElement("Data", New XAttribute("ID", i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```

## <a name="see-also"></a>Viz také:

- [Výkon (LINQ to XML) (Visual Basic)](performance-linq-to-xml.md)
- [Atomované XName a objekty XNamespace (LINQ to XML) (Visual Basic)](atomized-xname-and-xnamespace-objects-linq-to-xml.md)
