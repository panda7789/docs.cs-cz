---
title: Předběžná atomizace objektů XName (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 0ea45dbf0492491efac3560b7f1f04d36a787193
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660538"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a>Předběžná atomizace objektů XName (LINQ to XML) (C#)
Jedním ze způsobů ke zlepšení výkonu v technologii LINQ to XML je předem atomizovat <xref:System.Xml.Linq.XName> objekty. Předběžná atomizace znamená, že přiřadíte řetězec na <xref:System.Xml.Linq.XName> objektu před vytvořením stromu XML pomocí konstruktory <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> třídy. Pak namísto předáním řetězce do konstruktoru, který byste použili implicitní převod z řetězce na <xref:System.Xml.Linq.XName>, předáte inicializovaná zpráva <xref:System.Xml.Linq.XName> objektu.  
  
 To zlepšuje výkon při vytváření velké stromu XML, ve které se opakují konkrétní názvy. K tomuto účelu deklarujete a inicializujete <xref:System.Xml.Linq.XName> objekty před vytvoření stromu XML a pak použít <xref:System.Xml.Linq.XName> objekty místo zadávání řetězců pro názvy prvků a atributů. Tato technika může přinést výrazné zvýšení výkonu při vytváření velký počet elementů (nebo atributy) se stejným názvem.  
  
 Předběžná atomizace byste měli testovat s váš scénář se rozhodnout, pokud byste ji měli používat.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje to.  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
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
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XName Root = aw + "Root";  
XName Data = aw + "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XAttribute(XNamespace.Xmlns + "aw", aw),  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
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
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
DateTime t1 = DateTime.Now;  
XElement root = new XElement(Root,  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement(Data,  
        new XAttribute(ID, i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
 V předchozím příkladu vrací lepší výsledky než následující příklad, ve kterém názvy nejsou předem atomizované objekty:  
  
```csharp  
DateTime t1 = DateTime.Now;  
XElement root = new XElement("Root",  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement("Data",  
        new XAttribute("ID", i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
## <a name="see-also"></a>Viz také:

- [Výkon (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
- [Atomizované objekty XName a Xnamespace (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
