---
title: 'Postupy: Najde bezprostřední předchozí položku na stejné úrovni (XPath-LINQ to XMLC#) ().'
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: bc0a3250cf1f56ebf9a367f6472be8f3230cee5a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253631"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a>Postupy: Najde bezprostřední předchozí položku na stejné úrovni (XPath-LINQ to XMLC#) ().
Někdy chcete najít bezprostřední předchozí položku na stejné úrovni jako uzel. Z důvodu rozdílu v sémantikě pozičních predikátů pro předchozí osy na stejné úrovni ve výrazu XPath, na [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]rozdíl od, jde o jedno z zajímavějších porovnání.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotaz <xref:System.Linq.Enumerable.Last%2A> pomocí operátoru najde poslední uzel <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>v kolekci, kterou vrátí. Naopak výraz XPath používá predikát s hodnotou 1 pro nalezení bezprostředně předcházejícího prvku.  
  
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
