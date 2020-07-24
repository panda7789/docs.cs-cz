---
title: Jak najít bezprostřední předchozí položku na stejné úrovni (XPath-LINQ to XML) (C#)
description: Tento příklad v jazyce C# porovnává XPath s LINQ to XML pro nalezení stejné úrovně, která bezprostředně předchází uzlu.
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: eaee7f1205ce0d0b2a9c2c41d96ba532573a1384
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105200"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a>Jak najít bezprostřední předchozí položku na stejné úrovni (XPath-LINQ to XML) (C#)
Někdy chcete najít bezprostřední předchozí položku na stejné úrovni jako uzel. Z důvodu rozdílu v sémantikě pozičních predikátů pro předchozí osy na stejné úrovni ve výrazu XPath, na rozdíl od [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , jde o jedno z zajímavějších porovnání.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotaz pomocí <xref:System.Linq.Enumerable.Last%2A> operátoru najde poslední uzel v kolekci, kterou vrátí <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> . Naopak výraz XPath používá predikát s hodnotou 1 pro nalezení bezprostředně předcházejícího prvku.  
  
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
  
 Tento příklad vytvoří následující výstup:  
  
```output  
Results are identical  
<Child3 />  
```  
