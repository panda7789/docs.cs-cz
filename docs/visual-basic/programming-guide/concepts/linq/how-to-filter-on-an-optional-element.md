---
title: 'How to: Filter on an Optional Element'
ms.date: 07/20/2015
ms.assetid: a74b76ad-6889-4185-a189-d6ef2c63841e
ms.openlocfilehash: e67cb58710d49a19f322b3555efa96ac69b9f654
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353042"
---
# <a name="how-to-filter-on-an-optional-element-visual-basic"></a><span data-ttu-id="9fd57-102">How to: Filter on an Optional Element (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fd57-102">How to: Filter on an Optional Element (Visual Basic)</span></span>
<span data-ttu-id="9fd57-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span><span class="sxs-lookup"><span data-stu-id="9fd57-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="9fd57-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span><span class="sxs-lookup"><span data-stu-id="9fd57-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="9fd57-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span><span class="sxs-lookup"><span data-stu-id="9fd57-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fd57-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="9fd57-106">Example</span></span>  
 <span data-ttu-id="9fd57-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span><span class="sxs-lookup"><span data-stu-id="9fd57-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
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
  
 <span data-ttu-id="9fd57-108">This code produces the following output:</span><span class="sxs-lookup"><span data-stu-id="9fd57-108">This code produces the following output:</span></span>  
  
```console  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="9fd57-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="9fd57-109">Example</span></span>  
 <span data-ttu-id="9fd57-110">The following example shows the same query for XML that is in a namespace.</span><span class="sxs-lookup"><span data-stu-id="9fd57-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="9fd57-111">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9fd57-111">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="9fd57-112">This code produces the following output:</span><span class="sxs-lookup"><span data-stu-id="9fd57-112">This code produces the following output:</span></span>  
  
```console  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fd57-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fd57-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9fd57-114">Basic Queries (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fd57-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="9fd57-115">Vlastnost osy podřízeného XML</span><span class="sxs-lookup"><span data-stu-id="9fd57-115">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="9fd57-116">Vlastnost osy atributu XML</span><span class="sxs-lookup"><span data-stu-id="9fd57-116">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="9fd57-117">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="9fd57-117">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="9fd57-118">Standard Query Operators Overview (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fd57-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="9fd57-119">Projection Operations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fd57-119">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
