---
title: 'Postupy: vyhledání okamžité předcházející na stejné úrovni (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: c610ce4884e0760a03ec77aae4f38cf9c84a797a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507130"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a>Postupy: vyhledání okamžité předcházející na stejné úrovni (XPath – LINQ to XML) (C#)
Někdy budete chtít najít okamžité předcházející na stejné k uzlu. Z důvodu rozdíly v sémantice poziční predikáty. pro předchozí osy na stejné úrovni ve výrazu XPath, nikoli [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], to je jedna z zajímavější porovnání.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotaz používá <xref:System.Linq.Enumerable.Last%2A> operátor najít poslední uzel v kolekci vrácené poskytovatelem <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>. Výraz XPath naopak používá k nalezení prvku bezprostředně předcházející predikátu s hodnotou 1.  
  
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
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a>Viz také

- [LINQ to XML pro uživatele jazyka XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
