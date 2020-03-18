---
title: Před rozprašování objektů XName (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 2fd754a352bd2988e52ec9c67a9915a8e587b107
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591492"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a>Před rozprašování objektů XName (LINQ to XML) (C#)
Jedním ze způsobů, jak zlepšit výkon v LINQ <xref:System.Xml.Linq.XName> na XML je pre-atomize objekty. Před rozprašováním znamená, že před <xref:System.Xml.Linq.XName> vytvořením stromu XML přiřadíte objektu <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> řetězec pomocí konstruktorů tříd a. Potom namísto předání řetězce konstruktoru, který by použil implicitní převod z řetězce do <xref:System.Xml.Linq.XName>, předáte inicializovaný <xref:System.Xml.Linq.XName> objekt.  
  
 To zlepšuje výkon při vytváření velkého stromu XML, ve kterém se opakují určité názvy. Chcete-li to provést, deklarujte a inicializovat <xref:System.Xml.Linq.XName> objekty před vytvořením stromu XML a potom použijte <xref:System.Xml.Linq.XName> objekty namísto určení řetězců pro názvy prvků a atributů. Tato technika může přinést významné zvýšení výkonu, pokud vytváříte velký počet prvků (nebo atributů) se stejným názvem.  
  
 Měli byste otestovat pre-rozprašování s vaším scénářem rozhodnout, zda byste měli použít.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 Následující příklad ukazuje stejnou techniku, kde je dokument XML v oboru názvů:  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 Následující příklad je více podobný tomu, co se pravděpodobně setkáte v reálném světě. V tomto příkladu je obsah prvku dodáván dotazem:  
  
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
  
 Předchozí příklad provádí lépe než v následujícím příkladu, ve kterém názvy nejsou pre-atomized:  
  
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

- [Atomized XName a XNamespace objekty (LINQ na XML) (C#)](./atomized-xname-and-xnamespace-objects-linq-to-xml.md)
