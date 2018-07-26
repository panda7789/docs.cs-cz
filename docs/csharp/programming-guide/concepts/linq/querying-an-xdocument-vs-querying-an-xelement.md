---
title: Dotazování na XDocument vs. Dotazování na XElement (C#)
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 61d8c70b9cbaeeb487059e4acfc88dc165c45d65
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960131"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a>Dotazování na XDocument vs. Dotazování na XElement (C#)
Při načtení dokumentu prostřednictvím <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, všimnete si, že budete muset psát dotazy trochu jinak než při načtení prostřednictvím <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>Porovnání XDocument.Load a XElement.Load  
 Při načtení dokumentu XML do <xref:System.Xml.Linq.XElement> prostřednictvím <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement> v kořenovém adresáři XML stromu obsahuje kořenový element načtený dokument. Ale při načtení stejný dokument XML do <xref:System.Xml.Linq.XDocument> prostřednictvím <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, je kořen stromu <xref:System.Xml.Linq.XDocument> uzel a kořenový element načtený dokument je jeden podřízený prvek povolený <xref:System.Xml.Linq.XElement> uzlu <xref:System.Xml.Linq.XDocument>. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Osy pracovat vzhledem k kořenového uzlu.  
  
 Tento první příklad načte stromu XML pomocí <xref:System.Xml.Linq.XElement.Load%2A>. Následně dotazy pro podřízené prvky kořen stromu.  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XElement.Load");  
Console.WriteLine("----");  
XElement doc = XElement.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Podle očekávání, tento příklad vytvoří následující výstup:  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 Následující příklad je stejný jako ten výše, s tím rozdílem, který je načten stromu XML do <xref:System.Xml.Linq.XDocument> místo <xref:System.Xml.Linq.XElement>.  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Všimněte si, že stejný dotaz vrátil ten `Root` uzlu namísto tří podřízených uzlů.  
  
 Jedním z přístupů k práci s tímto je použít <xref:System.Xml.Linq.XDocument.Root%2A> vlastnost před použitím metody osy následujícím způsobem:  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Root.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Tento dotaz teď provádí stejným způsobem jako dotazu ve stromové struktuře integrován <xref:System.Xml.Linq.XElement>. Tento příklad vytvoří následující výstup:  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a>Viz také  
 [Základní dotazy (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
