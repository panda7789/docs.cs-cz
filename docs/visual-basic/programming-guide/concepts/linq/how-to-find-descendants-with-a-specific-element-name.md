---
title: 'Postupy: Vyhledání potomků s určitým názvem elementu'
ms.date: 07/20/2015
ms.assetid: 78915518-0d25-4051-ab55-929779989510
ms.openlocfilehash: 1a8aa07a79d05e62e0d5517c1675bc715e87de42
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344407"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-visual-basic"></a>Postupy: Vyhledání potomků s konkrétním názvem elementu (Visual Basic)
Někdy budete chtít najít všechny následníky s určitým názvem. Můžete napsat kód pro iterování všemi následníky, ale je snazší použít <xref:System.Xml.Linq.XContainer.Descendants%2A> osu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak najít následníky na základě názvu elementu.  
  
```vb  
Dim root As XElement = _  
    <root>  
        <para>  
            <r>  
                <t>Some text </t>  
            </r>  
            <n>  
                <r>  
                    <t>that is broken up into </t>  
                </r>  
            </n>  
            <n>  
                <r>  
                    <t>multiple segments.</t>  
                </r>  
            </n>  
        </para>  
    </root>  
  
Dim textSegs As IEnumerable(Of String) = _  
    From seg In root...<t> _  
    Select seg.Value  
  
Dim str As String = textSegs.Aggregate( _  
    New StringBuilder, _  
    Function(sb, i) sb.Append(i), _  
    Function(sb) sb.ToString)  
  
Console.WriteLine(str)  
```  
  
 Tento kód generuje následující výstup:  
  
```console  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <root>  
                <para>  
                    <r>  
                        <t>Some text </t>  
                    </r>  
                    <n>  
                        <r>  
                            <t>that is broken up into </t>  
                        </r>  
                    </n>  
                    <n>  
                        <r>  
                            <t>multiple segments.</t>  
                        </r>  
                    </n>  
                </para>  
            </root>  
  
        Dim textSegs As IEnumerable(Of String) = _  
            From seg In root...<t> _  
            Select seg.Value  
  
        Dim str As String = textSegs.Aggregate( _  
            New StringBuilder, _  
            Function(sb, i) sb.Append(i), _  
            Function(sb) sb.ToString)  
  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 Tento kód generuje následující výstup:  
  
```console  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- [Základní dotazy (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
