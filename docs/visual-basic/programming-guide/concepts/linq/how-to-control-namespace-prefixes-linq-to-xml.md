---
title: 'Postupy: řízení Namespace předpony (Visual Basic) (technologie LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: f60f90ef6742dfd725f51ff7e760436117346e85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641677"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a>Postupy: řízení Namespace předpony (Visual Basic) (technologie LINQ to XML)
Toto téma popisuje, jak můžete řídit předpony oboru názvů.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Tento příklad deklaruje dva obory názvů. Určuje, že `http://www.adventure-works.com` obor názvů se předponou `aw`a že `www.fourthcoffee.com` má předponu oboru názvů `fc`.  
  
### <a name="code"></a>Kód  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
### <a name="comments"></a>Komentáře  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Viz také  
 [Práce s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
