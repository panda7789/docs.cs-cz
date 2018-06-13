---
title: 'Postupy: práce s slovník pomocí technologie LINQ to XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: b6e41f61358563472f49b22df389df00e721503e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644820"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a>Postupy: práce s slovník pomocí technologie LINQ to XML (Visual Basic)
Často je vhodnější převést zpět na jiné datové struktury typy datové struktury XML a XML. Toto téma ukazuje na konkrétní implementace tento obecné přístup tím, že převedete <xref:System.Collections.Generic.Dictionary%602> do XML a zpět.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá ve výrazu vložených literálech XML a dotaz. Nový dotaz projekty <xref:System.Xml.Linq.XElement> objekty, které pak stane nový obsah `Root` <xref:System.Xml.Linq.XElement> objektu.  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Tento kód vytvoří následující výstup:  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří adresář ze souboru XML.  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 Tento kód vytvoří následující výstup:  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a>Viz také  
 [Projekce a transformace (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
