---
title: 'Postupy: Filtrování volitelného elementu'
ms.date: 07/20/2015
ms.assetid: a74b76ad-6889-4185-a189-d6ef2c63841e
ms.openlocfilehash: 6db377ae30582ef010d5af467e88c52b008483ed
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78267051"
---
# <a name="how-to-filter-on-an-optional-element-visual-basic"></a><span data-ttu-id="392cd-102">Postup: Filtrování volitelného prvku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="392cd-102">How to: Filter on an Optional Element (Visual Basic)</span></span>
<span data-ttu-id="392cd-103">Někdy chcete filtrovat prvek, i když si nejste jisti, že existuje v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="392cd-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="392cd-104">Hledání by měla být provedena tak, aby pokud konkrétní prvek nemá podřízený prvek, nespustíte výjimku nulového odkazu filtrováním pro něj.</span><span class="sxs-lookup"><span data-stu-id="392cd-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="392cd-105">V následujícím příkladu `Child5` prvek nemá `Type` podřízený prvek, ale dotaz se stále provádí správně.</span><span class="sxs-lookup"><span data-stu-id="392cd-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="392cd-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="392cd-106">Example</span></span>  
 <span data-ttu-id="392cd-107">Tento příklad <xref:System.Xml.Linq.Extensions.Elements%2A> používá metodu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="392cd-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
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
  
 <span data-ttu-id="392cd-108">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="392cd-108">This code produces the following output:</span></span>  
  
```console  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="392cd-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="392cd-109">Example</span></span>  
 <span data-ttu-id="392cd-110">Následující příklad ukazuje stejný dotaz pro jazyk XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="392cd-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="392cd-111">Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (Visual Basic).](namespaces-overview-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="392cd-111">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="392cd-112">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="392cd-112">This code produces the following output:</span></span>  
  
```console  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="392cd-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="392cd-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="392cd-114">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="392cd-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="392cd-115">Vlastnost osy podřízeného XML</span><span class="sxs-lookup"><span data-stu-id="392cd-115">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="392cd-116">Vlastnost osy atributu XML</span><span class="sxs-lookup"><span data-stu-id="392cd-116">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="392cd-117">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="392cd-117">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="392cd-118">Standardní operátory dotazů – přehled (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="392cd-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="392cd-119">Projekční operace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="392cd-119">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
