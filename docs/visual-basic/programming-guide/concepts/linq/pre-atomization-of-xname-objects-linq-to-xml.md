---
title: Předběžná atomizace objektů XName (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: a87a37c5fe2fc29ca980c77d9c775b2b1e909cc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353106"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>Předběžná Atomace objektů XName (LINQ to XML) (Visual Basic)
Jedním ze způsobů, jak zlepšit výkon v LINQ to XML, je atomizovat <xref:System.Xml.Linq.XName> objektů. Před vytvořením stromu XML pomocí konstruktorů tříd <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> je třeba před vytvořením stromu XML přiřadit řetězec <xref:System.Xml.Linq.XName> objektu. Místo předání řetězce konstruktoru, který by použil implicitní převod z řetězce na <xref:System.Xml.Linq.XName>, předáte inicializovaný objekt <xref:System.Xml.Linq.XName>.  
  
 To zlepšuje výkon při vytváření velkého stromu XML, ve kterém se konkrétní názvy opakují. Chcete-li to provést, deklarujete a inicializujete <xref:System.Xml.Linq.XName> objektů před vytvořením stromu XML a poté místo určení řetězců pro element a atributy atributu použít objekty <xref:System.Xml.Linq.XName>. Tato technika může přinést výrazné zvýšení výkonu, pokud vytváříte velký počet prvků (nebo atributů) se stejným názvem.  
  
 Před tím, než se rozhodnete, jestli ho chcete použít, byste měli testovat předběžnou atomaci ve svém scénáři.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje to.  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
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
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
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
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 Předchozí příklad provede lepší, než následující příklad, ve kterém názvy nejsou předběžně atomované:  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>Viz také:

- [Výkon (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
- [Atomované XName a objekty XNamespace (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
