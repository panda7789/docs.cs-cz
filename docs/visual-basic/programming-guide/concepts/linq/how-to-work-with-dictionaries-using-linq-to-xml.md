---
title: 'Postupy: práce se slovníky pomocí LINQ to XML'
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: 12327be3c9d32d34866691b156f58fd1e8e40240
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332366"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a>Postupy: práce se slovníky pomocí LINQ to XML (Visual Basic)
Je často vhodné převést odrůdy datových struktur do XML a vrátit se do jiných datových struktur. Toto téma ukazuje konkrétní implementaci tohoto obecného přístupu převodem <xref:System.Collections.Generic.Dictionary%602> na XML a zpět.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá literály XML a dotaz ve vloženém výrazu. Dotaz projektuje nové objekty <xref:System.Xml.Linq.XElement>, které se pak stanou novým obsahem pro objekt `Root` <xref:System.Xml.Linq.XElement>.  
  
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
  
 Tento kód generuje následující výstup:  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří slovník z XML.  
  
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
  
 Tento kód generuje následující výstup:  
  
```console  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a>Viz také:

- [Projekce a transformace (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
