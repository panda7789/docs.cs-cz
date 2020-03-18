---
title: Jak najít bezprostřední předchozí na stejné úrovni (XPath-LINQ na XML) (C#)
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 1e5aece41021642d43b7f6f7b78bb105156ee4ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141000"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a>Jak najít bezprostřední předchozí na stejné úrovni (XPath-LINQ na XML) (C#)
Někdy chcete najít bezprostřední předchozí na stejné úrovni na uzlu. Vzhledem k rozdílu v sémantice poziční predikáty pro předchozí na [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]stejné úrovni osy v XPath na rozdíl od , to je jeden z více zajímavých srovnání.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotaz <xref:System.Linq.Enumerable.Last%2A> používá operátor najít poslední uzel v <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>kolekci vrácené . Naproti tomu výraz XPath používá predikát s hodnotou 1 k nalezení bezprostředně předcházejícího prvku.  
  
```csharp  
XElement root = XElement.Parse(  
    @"<Root>  
    <Child1/>  
    <Child2/>  
    <Child3/>  
    <Child4/>  
</Root>");  
XElement child4 = root.Element("Child4");  
  
// LINQ to XML query  
XElement el1 =  
    child4  
    .ElementsBeforeSelf()  
    .Last();  
  
// XPath expression  
XElement el2 =  
    ((IEnumerable)child4  
                 .XPathEvaluate("preceding-sibling::*[1]"))  
                 .Cast<XElement>()  
                 .First();  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```output  
Results are identical  
<Child3 />  
```  
