---
title: 'Postupy: načtení hodnoty elementu (technologie LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: ff2a1712a79bdedd74fe51391f01dd900ae585e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643832"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a>Postupy: načtení hodnoty elementu (technologie LINQ to XML) (Visual Basic)
Toto téma ukazuje, jak má být získána hodnota elementů. Chcete-li to provést dvěma způsoby. Jedním ze způsobů je přetypovat <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> na požadovaný typ. Explicitní převod operátor potom převede obsah elementu nebo atributu na zadaný typ a přiřadí ji k vaše proměnná. Alternativně můžete použít <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnost nebo <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> vlastnost.  
  
 V jazyce Visual Basic, je nejlepším postupem je použití <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="example"></a>Příklad  
 K načtení hodnoty elementu, je právě přetypovat <xref:System.Xml.Linq.XElement> objekt, který má požadovaný typ. Element na řetězec, můžete vždy přetypovat následujícím způsobem:  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Příklad  
 Můžete také přetypování elementy na typy jiné než řetězec. Například pokud máte elementu, který obsahuje celé číslo, vám může vysílat `int`, jak je znázorněno v následujícím kódu:  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje operátory explicitní přetypování pro následující typy dat: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?` , `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, a `GUID?`.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje stejné operátory přetypování pro <xref:System.Xml.Linq.XAttribute> objekty.  
  
## <a name="example"></a>Příklad  
 Můžete použít <xref:System.Xml.Linq.XElement.Value%2A> vlastnost můžete načíst obsah elementu:  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Příklad  
 Někdy pokusu načíst hodnotu elementu, i když si nejste jisti, že existuje. V takovém případě přiřadíte-li převedena element na typ s možnou hodnotou Null (buď `string` nebo jeden z typů s povolenou hodnotou Null v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), pokud element neexistuje přiřazená proměnná je nastavená pouze na `Nothing`. Následující kód ukazuje, že pokud element může nebo nemusí existovat, je jednodušší použít přetypování než k použijte <xref:System.Xml.Linq.XElement.Value%2A> vlastnost.  
  
```vb  
Dim root As XElement = <Root>  
                           <Child1>child 1 content</Child1>  
                           <Child2>2</Child2>  
                       </Root>  
  
' The following assignments show why it is easier to use  
' casting when the element might or might not exist.  
  
Dim c1 As String = CStr(root.Element("Child1"))  
Console.WriteLine("c1:{0}", IIf(c1 Is Nothing, "element does not exist", c1))  
  
Dim c2 As Nullable(Of Integer) = CType(root.Element("Child2"), Nullable(Of Integer))  
Console.WriteLine("c2:{0}", IIf(Not (c2.HasValue), "element does not exist", c2.ToString()))  
  
Dim c3 As String = CStr(root.Element("Child3"))  
Console.WriteLine("c3:{0}", IIf(c3 Is Nothing, "element does not exist", c3))  
  
Dim c4 As Nullable(Of Integer) = CType(root.Element("Child4"), Nullable(Of Integer))  
Console.WriteLine("c4:{0}", IIf(Not (c4.HasValue), "element does not exist", c4.ToString()))  
  
Console.WriteLine()  
  
' The following assignments show the required code when using  
' the Value property when the attribute might or might not exist.  
' Notice that this is more difficult than the casting approach.  
  
Dim e1 As XElement = root.Element("Child1")  
Dim v1 As String  
If (e1 Is Nothing) Then  
    v1 = Nothing  
Else  
    v1 = e1.Value  
End If  
Console.WriteLine("v1:{0}", IIf(v1 Is Nothing, "element does not exist", v1))  
  
Dim e2 As XElement = root.Element("Child2")  
Dim v2 As Nullable(Of Integer)  
If (e2 Is Nothing) Then  
    v2 = Nothing  
Else  
    v2 = e2.Value  
End If  
Console.WriteLine("v2:{0}", IIf(Not (v2.HasValue), "element does not exist", v2))  
  
Dim e3 As XElement = root.Element("Child3")  
Dim v3 As String  
If (e3 Is Nothing) Then  
    v3 = Nothing  
Else  
    v3 = e3.Value  
End If  
Console.WriteLine("v3:{0}", IIf(v3 Is Nothing, "element does not exist", v3))  
  
Dim e4 As XElement = root.Element("Child4")  
Dim v4 As Nullable(Of Integer)  
If (e4 Is Nothing) Then  
    v4 = Nothing  
Else  
    v4 = e4.Value  
End If  
Console.WriteLine("v4:{0}", IIf(Not (v4.HasValue), "element does not exist", v4))  
```  
  
 Tento kód vytvoří následující výstup:  
  
```  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 Obecně platí můžete napsat kód jednodušší při použití přetypování můžete načíst obsah elementů a atributů.  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to XML osy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
