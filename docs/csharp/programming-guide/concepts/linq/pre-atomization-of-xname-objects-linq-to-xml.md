---
title: "Předběžné atomizace XName objektů (technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 32613771da42b3e8260b1608f20ad6c195008faa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a>Předběžné atomizace XName objektů (technologie LINQ to XML) (C#)
Jeden způsob, jak zlepšit výkon v technologii LINQ to XML je předem atomizovat <xref:System.Xml.Linq.XName> objekty. Předběžné atomizace znamená, že přiřadíte řetězec tak, aby <xref:System.Xml.Linq.XName> objektu před vytvořením stromu XML pomocí konstruktorů systému <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> třídy. Potom neprochází řetězec konstruktoru, které byste použili implicitní převod z řetězce na <xref:System.Xml.Linq.XName>, předáte inicializovaná <xref:System.Xml.Linq.XName> objektu.  
  
 To zvyšuje výkon, když vytvoříte velké stromu XML, ve které se opakují konkrétní názvy. K tomuto účelu deklarace a inicializace <xref:System.Xml.Linq.XName> objekty předtím, než můžete vytvořit stromu XML a potom pomocí <xref:System.Xml.Linq.XName> objekty místo zadání řetězce pro název elementu a atributu. Tento postup mohou přinést výrazné zvýšení výkonu při vytváření velký počet elementů (nebo atributy) se stejným názvem.  
  
 Měli byste otestovat před atomizace s váš scénář se rozhodnout, pokud by ji použít.  
  
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
  
 Následující příklad ukazuje stejným způsobem, kde je v dokumentu XML v oboru názvů:  
  
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
  
 V následujícím příkladu je více podobná co pravděpodobně dojde v reálném světě. V tomto příkladu je obsah elementu poskytl dotazu:  
  
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
  
 Předchozí příklad provádí lépe než následující příklad, ve které nejsou předem atomized názvy:  
  
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
  
## <a name="see-also"></a>Viz také  
 [Výkon (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)  
 [Atomized XName a XNamespace objekty (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
