---
title: Dotazování xdocument vs dotazování XElement (C#)
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 475c77934ad535bad9ef79ff58bbddf991dc8f5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253128"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a>Dotazování xdocument vs dotazování XElement (C#)
Při načítání dokumentu <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>prostřednictvím , zjistíte, že budete muset psát dotazy mírně <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>odlišně, než při načítání přes .  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>Porovnání XDocument.Load a XElement.Load  
 Když načtete dokument <xref:System.Xml.Linq.XElement> XML <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>do <xref:System.Xml.Linq.XElement> via , kořenový adresář stromu XML obsahuje kořenový prvek načteného dokumentu. Však při načtení stejného <xref:System.Xml.Linq.XDocument> dokumentu <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>XML do via , <xref:System.Xml.Linq.XDocument> kořen stromu je uzel a kořenový prvek <xref:System.Xml.Linq.XElement> načteného <xref:System.Xml.Linq.XDocument>dokumentu je jeden povolený podřízený uzel . Osy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pracují vzhledem ke kořenovému uzlu.  
  
 Tento první příklad načte <xref:System.Xml.Linq.XElement.Load%2A>strom XML pomocí . Potom dotazy na podřízené prvky kořene stromu.  
  
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
  
 Podle očekávání tento příklad vytvoří následující výstup:  
  
```output  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 Následující příklad je stejný jako výše uvedený, s výjimkou, že <xref:System.Xml.Linq.XDocument> strom XML <xref:System.Xml.Linq.XElement>je načten do místo .  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Všimněte si, že `Root` stejný dotaz vrátil jeden uzel namísto tří podřízených uzlů.  
  
 Jedním z přístupů k řešení <xref:System.Xml.Linq.XDocument.Root%2A> tohoto je použití vlastnosti před přístupem k osy metody, takto:  
  
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
  
 Tento dotaz nyní provádí stejným způsobem jako dotaz <xref:System.Xml.Linq.XElement>na stromu zakořeněné v . Příklad vytváří následující výstup:  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  