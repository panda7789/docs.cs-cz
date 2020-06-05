---
title: 'Postupy: Filtrování volitelného elementu'
ms.date: 07/20/2015
ms.assetid: a74b76ad-6889-4185-a189-d6ef2c63841e
ms.openlocfilehash: 9f03eee479e7c47e528a145d370472de6dfddd39
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394360"
---
# <a name="how-to-filter-on-an-optional-element-visual-basic"></a>Postupy: filtrování volitelného prvku (Visual Basic)
Někdy je vhodné vyfiltrovat element, i když si nejste jistí, že existuje v dokumentu XML. Hledání by mělo být provedeno, aby v případě, že konkrétní prvek nemá podřízený element, neaktivovali výjimku odkazu s hodnotou null filtrováním. V následujícím příkladu `Child5` element nemá `Type` podřízený element, ale dotaz se stále provede správně.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá <xref:System.Xml.Linq.Extensions.Elements%2A> metoda rozšíření.  
  
```vb  
Dim root As XElement = _
    <Root>  
        <Child1>  
            <Text>Child One Text</Text>  
            <Type Value="Yes"/>  
        </Child1>  
        <Child2>  
            <Text>Child Two Text</Text>  
            <Type Value="Yes"/>  
        </Child2>  
        <Child3>  
            <Text>Child Three Text</Text>  
            <Type Value="No"/>  
        </Child3>  
        <Child4>  
            <Text>Child Four Text</Text>  
            <Type Value="Yes"/>  
        </Child4>  
        <Child5>  
            <Text>Child Five Text</Text>  
        </Child5>  
    </Root>  
Dim cList As IEnumerable(Of String) = _  
    From typeElement In root.Elements().<Type> _  
    Where typeElement.@Value = "Yes" _  
    Select typeElement.Parent.<Text>.Value  
Dim str As String  
For Each str In cList  
    Console.WriteLine(str)  
Next  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```console  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child1>  
                    <Text>Child One Text</Text>  
                    <Type Value="Yes"/>  
                </Child1>  
                <Child2>  
                    <Text>Child Two Text</Text>  
                    <Type Value="Yes"/>  
                </Child2>  
                <Child3>  
                    <Text>Child Three Text</Text>  
                    <Type Value="No"/>  
                </Child3>  
                <Child4>  
                    <Text>Child Four Text</Text>  
                    <Type Value="Yes"/>  
                </Child4>  
                <Child5>  
                    <Text>Child Five Text</Text>  
                </Child5>  
            </Root>  
        Dim cList As IEnumerable(Of String) = _  
            From typeElement In root.Elements().<Type> _  
            Where typeElement.@Value = "Yes" _  
            Select typeElement.Parent.<Text>.Value  
        Dim str As String  
        For Each str In cList  
            Console.WriteLine(str)  
        Next  
    End Sub  
End Module  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```console  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [Základní dotazy (LINQ to XML) (Visual Basic)](basic-queries-linq-to-xml.md)
- [Vlastnost osy podřízeného XML](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [Vlastnost osy atributu XML](../../../language-reference/xml-axis/xml-attribute-axis-property.md)
- [Vlastnost hodnoty XML](../../../language-reference/xml-axis/xml-value-property.md)
- [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md)
- [Operace projekce (Visual Basic)](projection-operations.md)
