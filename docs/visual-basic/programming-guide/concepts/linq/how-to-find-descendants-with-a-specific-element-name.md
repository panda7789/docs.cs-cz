---
title: 'Postupy: Vyhledání potomků s konkrétním názvem elementu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 78915518-0d25-4051-ab55-929779989510
ms.openlocfilehash: 4311eb0a4062c01b2c8e1c19355c5284298e39dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557156"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-visual-basic"></a><span data-ttu-id="4fb5c-102">Postupy: Vyhledání potomků s konkrétním názvem elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fb5c-102">How to: Find Descendants with a Specific Element Name (Visual Basic)</span></span>
<span data-ttu-id="4fb5c-103">Někdy budete chtít vyhledání všech potomků s konkrétním názvem.</span><span class="sxs-lookup"><span data-stu-id="4fb5c-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="4fb5c-104">Můžete napsat kód k iteraci v rámci všechny následníky, ale je jednodušší použít <xref:System.Xml.Linq.XContainer.Descendants%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="4fb5c-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fb5c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="4fb5c-105">Example</span></span>  
 <span data-ttu-id="4fb5c-106">Následující příklad ukazuje, jak vyhledání potomků vycházet z názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="4fb5c-106">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="4fb5c-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4fb5c-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="4fb5c-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="4fb5c-108">Example</span></span>  
 <span data-ttu-id="4fb5c-109">Následující příklad ukazuje stejný dotaz pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4fb5c-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="4fb5c-110">Další informace najdete v tématu [práce s názvovými prostory XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="4fb5c-110">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="4fb5c-111">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4fb5c-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="4fb5c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4fb5c-112">See also</span></span>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- [<span data-ttu-id="4fb5c-113">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fb5c-113">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
