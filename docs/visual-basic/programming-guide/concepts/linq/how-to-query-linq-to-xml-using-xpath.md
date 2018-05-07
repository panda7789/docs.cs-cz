---
title: 'Postupy: dotazování technologie LINQ to XML s použitím XPath (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: d8f23bd8417c3f59377e5e677b08e403ecc1122d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a>Postupy: dotazování technologie LINQ to XML s použitím XPath (Visual Basic)
Toto téma představuje rozšiřující metody, které vám umožní zadat dotaz strom XML s použitím XPath. Podrobné informace o použití těchto metod rozšíření najdete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
 Pokud nemáte velmi konkrétní důvod, proč pro dotazování pomocí jazyka XPath, jako je například rozsáhlé používání starší verze kódu, pomocí technologie LINQ to XML XPath se nedoporučuje. Nebude provádět dotazy XPath a také [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří malé stromu XML a používá <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> pro výběr sady elementů.  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child1>2</Child1>  
        <Child1>3</Child1>  
        <Child2>4</Child2>  
        <Child2>5</Child2>  
        <Child2>6</Child2>  
    </Root>  
  
Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")  
For Each el As XElement In list  
    Console.WriteLine(el)  
Next  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé techniky dotazu (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
