---
title: 'Postupy: vyhledání jednoho následníka pomocí metody Descendants (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0c03468c-efc8-4140-98f3-fb67acd9e8e1
ms.openlocfilehash: dbde5686d1b7670290d434c0a04515cbc10622fd
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249966"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-visual-basic"></a>Postupy: vyhledání jednoho následníka pomocí metody Descendants (Visual Basic)
Můžete použít metodu <xref:System.Xml.Linq.XContainer.Descendants%2A> k rychlému psaní kódu pro nalezení jednoho jednoznačně pojmenovaného prvku. Tato technika je užitečná hlavně v případě, že chcete najít konkrétního následníka s konkrétním názvem. Můžete napsat kód pro přechod k požadovanému prvku, ale je často rychlejší a snazší psát kód pomocí osy <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá standardní operátor dotazu <xref:System.Linq.Enumerable.First%2A>.  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1>GC1 Value</GrandChild1>  
        </Child1>  
        <Child2>  
            <GrandChild2>GC2 Value</GrandChild2>  
        </Child2>  
        <Child3>  
            <GrandChild3>GC3 Value</GrandChild3>  
        </Child3>  
        <Child4>  
            <GrandChild4>GC4 Value</GrandChild4>  
        </Child4>  
    </Root>  
Dim grandChild3 As String = _  
    (From el In root...<GrandChild3> _  
    Select el).First()  
Console.WriteLine(grandChild3)  
```  
  
 Tento kód generuje následující výstup:  
  
```console  
GC3 Value  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child1>  
                    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
                </aw:Child1>  
                <aw:Child2>  
                    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
                </aw:Child2>  
                <aw:Child3>  
                    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
                </aw:Child3>  
                <aw:Child4>  
                    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
                </aw:Child4>  
            </aw:Root>  
        Dim grandChild3 As String = _  
            (From el In root...<aw:GrandChild3> _  
            Select el).First()  
        Console.WriteLine(grandChild3)  
    End Sub  
End Module  
```  
  
 Tento kód generuje následující výstup:  
  
```console  
GC3 Value  
```  
  
## <a name="see-also"></a>Související témata

- [Základní dotazy (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
