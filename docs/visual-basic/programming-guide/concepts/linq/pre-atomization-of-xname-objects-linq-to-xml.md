---
title: Předběžná atomizace objektů XName (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: 250b7aa8060c8196c28725fded090e2a63a0ee54
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819291"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>Předběžná atomizace objektů XName (LINQ to XML) (Visual Basic)
Jedním ze způsobů ke zlepšení výkonu v technologii LINQ to XML je předem atomizovat <xref:System.Xml.Linq.XName> objekty. Předběžná atomizace znamená, že přiřadíte řetězec na <xref:System.Xml.Linq.XName> objektu před vytvořením stromu XML pomocí konstruktory <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> třídy. Pak namísto předáním řetězce do konstruktoru, který byste použili implicitní převod z řetězce na <xref:System.Xml.Linq.XName>, předáte inicializovaná zpráva <xref:System.Xml.Linq.XName> objektu.  
  
 To zlepšuje výkon při vytváření velké stromu XML, ve které se opakují konkrétní názvy. K tomuto účelu deklarujete a inicializujete <xref:System.Xml.Linq.XName> objekty před vytvoření stromu XML a pak použít <xref:System.Xml.Linq.XName> objekty místo zadávání řetězců pro názvy prvků a atributů. Tato technika může přinést výrazné zvýšení výkonu při vytváření velký počet elementů (nebo atributy) se stejným názvem.  
  
 Předběžná atomizace byste měli testovat s váš scénář se rozhodnout, pokud byste ji měli používat.  
  
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
  
 Následující příklad ukazuje stejný postup, pokud dokument XML je v oboru názvů:  
  
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
  
 Následující příklad je podobné co se pravděpodobně setkáte v reálném světě. V tomto příkladu obsah elementu, který je poskytnut pomocí dotazu:  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 V předchozím příkladu vrací lepší výsledky než následující příklad, ve kterém názvy nejsou předem atomizované objekty:  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>Viz také:

- [Výkon (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
- [Atomizované objekty XName a Xnamespace (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
