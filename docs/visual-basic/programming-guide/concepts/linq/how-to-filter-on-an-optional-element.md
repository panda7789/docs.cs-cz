---
title: 'Postupy: Filtrování volitelného elementu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a74b76ad-6889-4185-a189-d6ef2c63841e
ms.openlocfilehash: f2a1c7d4091af80e79a6758bcede8f4ccc753f03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855384"
---
# <a name="how-to-filter-on-an-optional-element-visual-basic"></a><span data-ttu-id="c8fa1-102">Postupy: Filtrování volitelného elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8fa1-102">How to: Filter on an Optional Element (Visual Basic)</span></span>
<span data-ttu-id="c8fa1-103">Někdy budete chtít filtrovat pro element, i když si nejste jisti, že objekt že existuje v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c8fa1-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="c8fa1-104">Hledání by měl provádět tak, že pokud konkrétní element nemá podřízený element, pomocí filtrování pro něj nespouštějí výjimka nulového odkazu.</span><span class="sxs-lookup"><span data-stu-id="c8fa1-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="c8fa1-105">V následujícím příkladu `Child5` nemá element `Type` podřízený element, ale dotaz stále se provede správně.</span><span class="sxs-lookup"><span data-stu-id="c8fa1-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8fa1-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="c8fa1-106">Example</span></span>  
 <span data-ttu-id="c8fa1-107">V tomto příkladu <xref:System.Xml.Linq.Extensions.Elements%2A> – metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c8fa1-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
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
  
 <span data-ttu-id="c8fa1-108">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c8fa1-108">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="c8fa1-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="c8fa1-109">Example</span></span>  
 <span data-ttu-id="c8fa1-110">Následující příklad ukazuje stejný dotaz pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c8fa1-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="c8fa1-111">Další informace najdete v tématu [práce s názvovými prostory XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="c8fa1-111">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="c8fa1-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c8fa1-112">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8fa1-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8fa1-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c8fa1-114">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8fa1-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="c8fa1-115">Vlastnost osy podřízeného XML</span><span class="sxs-lookup"><span data-stu-id="c8fa1-115">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="c8fa1-116">Vlastnost osy atributu XML</span><span class="sxs-lookup"><span data-stu-id="c8fa1-116">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="c8fa1-117">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="c8fa1-117">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="c8fa1-118">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8fa1-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="c8fa1-119">Operace projekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8fa1-119">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
