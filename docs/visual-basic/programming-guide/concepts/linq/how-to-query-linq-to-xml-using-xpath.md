---
title: 'Postupy: dotazování LINQ to XML pomocí jazyka XPath'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: 563756c019ddd458d46f47c843e32ddc7bbaacd1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347646"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a>Postupy: dotazování LINQ to XML pomocí XPath (Visual Basic)
Toto téma představuje rozšiřující metody, které umožňují dotazování stromu XML pomocí XPath. Podrobné informace o použití těchto rozšiřujících metod naleznete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
 Pokud nemáte konkrétní důvod pro dotazování pomocí XPath, jako je například rozsáhlé použití starší verze kódu, použití XPath s LINQ to XML se nedoporučuje. Dotazy XPath nebudou provedeny ani [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří malý strom XML a používá <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> pro výběr sady prvků.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Pokročilé techniky dotazů (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
