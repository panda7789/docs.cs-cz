---
title: 'Postupy: Napsat dotaz, který vyhledá elementy na základě kontextu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0b085290-ddc1-4126-aaa0-e4c95a3d9a09
ms.openlocfilehash: 0981da1e35f2c0b6023c009d4f62c95a612d8971
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814260"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-visual-basic"></a><span data-ttu-id="c6b17-102">Postupy: Napsat dotaz, který vyhledá elementy na základě kontextu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6b17-102">How to: Write a Query that Finds Elements Based on Context (Visual Basic)</span></span>
<span data-ttu-id="c6b17-103">V některých případech budete muset vytvořit dotaz, který vybere elementy podle jejich kontextu.</span><span class="sxs-lookup"><span data-stu-id="c6b17-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="c6b17-104">Můžete filtrovat na základě před nebo za tímto elementů na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="c6b17-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="c6b17-105">Můžete filtrovat na základě podřízeného nebo nadřazeného elementy.</span><span class="sxs-lookup"><span data-stu-id="c6b17-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="c6b17-106">To lze provést zadáním dotazu a pomocí výsledků dotazu v `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c6b17-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="c6b17-107">Pokud je nutné nejprve otestovat s hodnotou null a pak testování hodnot, je pohodlnější provést dotaz `let` klauzule a pak použít výsledky v `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c6b17-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6b17-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6b17-108">Example</span></span>  
 <span data-ttu-id="c6b17-109">V následujícím příkladu vybere všechny `p` prvky, které jsou okamžitě následovat `ul` elementu.</span><span class="sxs-lookup"><span data-stu-id="c6b17-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
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
  
 <span data-ttu-id="c6b17-110">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c6b17-110">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="c6b17-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6b17-111">Example</span></span>  
 <span data-ttu-id="c6b17-112">Následující příklad ukazuje stejný dotaz pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c6b17-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="c6b17-113">Další informace najdete v tématu [práce s názvovými prostory XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="c6b17-113">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="c6b17-114">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c6b17-114">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6b17-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6b17-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
- [<span data-ttu-id="c6b17-116">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6b17-116">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
