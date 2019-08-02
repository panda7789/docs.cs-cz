---
title: 'Postupy: Napsat dotaz, který najde elementy na základě kontextu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0b085290-ddc1-4126-aaa0-e4c95a3d9a09
ms.openlocfilehash: 1743a0793a8b572cb212d45a31924fe8eb93bf45
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710406"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-visual-basic"></a><span data-ttu-id="06bfa-102">Postupy: Napsat dotaz, který najde elementy na základě kontextu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06bfa-102">How to: Write a Query that Finds Elements Based on Context (Visual Basic)</span></span>
<span data-ttu-id="06bfa-103">Někdy může být nutné napsat dotaz, který vybere prvky na základě jejich kontextu.</span><span class="sxs-lookup"><span data-stu-id="06bfa-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="06bfa-104">Je možné, že budete chtít filtrovat na základě předchozích nebo následujících prvků na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="06bfa-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="06bfa-105">Je možné, že budete chtít filtrovat na základě podřízených nebo nadřazených prvků.</span><span class="sxs-lookup"><span data-stu-id="06bfa-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="06bfa-106">To můžete provést vytvořením dotazu a použitím výsledků dotazu v `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="06bfa-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="06bfa-107">Pokud je třeba otestovat proti hodnotě null a potom otestovat hodnotu, je vhodnější provést dotaz v `let` klauzuli a potom použít výsledky `where` v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="06bfa-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06bfa-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="06bfa-108">Example</span></span>  
 <span data-ttu-id="06bfa-109">Následující příklad vybere všechny `p` prvky, které jsou bezprostředně následovány `ul` elementem.</span><span class="sxs-lookup"><span data-stu-id="06bfa-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
```vb  
Dim doc As XElement = _  
    <Root>  
        <p id='1'/>  
        <ul>abc</ul>  
        <Child>  
            <p id='2'/>  
            <notul/>  
            <p id='3'/>  
            <ul>def</ul>  
            <p id='4'/>  
        </Child>  
        <Child>  
            <p id='5'/>  
            <notul/>  
            <p id='6'/>  
            <ul>abc</ul>  
            <p id='7'/>  
        </Child>  
    </Root>  
  
Dim items As IEnumerable(Of XElement) = _  
    From e In doc...<p> _  
    Let z = e.ElementsAfterSelf().FirstOrDefault() _  
    Where z IsNot Nothing AndAlso z.Name.LocalName = "ul" _  
    Select e  
  
For Each e As XElement In items  
    Console.WriteLine("id = {0}", e.@<id>)  
Next  
```  
  
 <span data-ttu-id="06bfa-110">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="06bfa-110">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="06bfa-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="06bfa-111">Example</span></span>  
 <span data-ttu-id="06bfa-112">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="06bfa-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="06bfa-113">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="06bfa-113">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim doc As XElement = _  
            <Root>  
                <p id='1'/>  
                <ul>abc</ul>  
                <Child>  
                    <p id='2'/>  
                    <notul/>  
                    <p id='3'/>  
                    <ul>def</ul>  
                    <p id='4'/>  
                </Child>  
                <Child>  
                    <p id='5'/>  
                    <notul/>  
                    <p id='6'/>  
                    <ul>abc</ul>  
                    <p id='7'/>  
                </Child>  
            </Root>  
  
        Dim items As IEnumerable(Of XElement) = _  
            From e In doc...<p> _  
            Let z = e.ElementsAfterSelf().FirstOrDefault() _  
            Where z IsNot Nothing AndAlso z.Name = GetXmlNamespace().GetName("ul") _  
            Select e  
  
        For Each e As XElement In items  
            Console.WriteLine("id = {0}", e.@<id>)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="06bfa-114">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="06bfa-114">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="06bfa-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06bfa-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
- [<span data-ttu-id="06bfa-116">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06bfa-116">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
