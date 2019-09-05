---
title: Dotazování na XDocument vs. Dotazování na XElement (C#)
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 475c77934ad535bad9ef79ff58bbddf991dc8f5c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253128"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a>Dotazování na XDocument vs. Dotazování na XElement (C#)
Když načtete dokument prostřednictvím <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, všimnete si, že budete muset psát dotazy trochu jinak než při načítání prostřednictvím. <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>Porovnání XDocument. Load a XElement. Load  
 Když načtete dokument XML do <xref:System.Xml.Linq.XElement> Via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement> v kořenu stromu XML obsahuje kořenový prvek načteného dokumentu. Nicméně když načtete stejný dokument XML do <xref:System.Xml.Linq.XDocument> Via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, kořen stromové struktury je <xref:System.Xml.Linq.XDocument> uzel a kořenový prvek načteného dokumentu <xref:System.Xml.Linq.XDocument>je jeden povolený podřízený <xref:System.Xml.Linq.XElement> uzel. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Osy pracují relativně ke kořenovému uzlu.  
  
 Tento první příklad načte strom XML pomocí <xref:System.Xml.Linq.XElement.Load%2A>. Pak se dotazuje na podřízené prvky kořenového adresáře stromu.  
  
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
  
 Jak je očekáváno, tento příklad vytvoří následující výstup:  
  
```output  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 Následující příklad je stejný jako ten výše, s výjimkou, že je strom XML načten do <xref:System.Xml.Linq.XDocument> namísto. <xref:System.Xml.Linq.XElement>  
  
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
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Všimněte si, že stejný dotaz vrátil jeden `Root` uzel místo tří podřízených uzlů.  
  
 Jedním z přístupů k tomu, abyste se s ním mohli <xref:System.Xml.Linq.XDocument.Root%2A> pracovat, je použít vlastnost před přístupem k metodám OS následujícím způsobem:  
  
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
  
 Tento dotaz teď funguje stejným způsobem jako dotaz na stromové struktuře, ve <xref:System.Xml.Linq.XElement>které se nachází root. Tento příklad vytvoří následující výstup:  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  