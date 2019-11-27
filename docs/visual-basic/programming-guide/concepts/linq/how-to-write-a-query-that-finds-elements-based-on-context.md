---
title: 'Postupy: zápis dotazu, který vyhledává elementy na základě kontextu'
ms.date: 07/20/2015
ms.assetid: 0b085290-ddc1-4126-aaa0-e4c95a3d9a09
ms.openlocfilehash: d25c6d47eee2ae092c84c3db3c08c3e21e7d98d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346206"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-visual-basic"></a><span data-ttu-id="03eb4-102">Postupy: zápis dotazu, který vyhledává elementy na základě kontextu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03eb4-102">How to: Write a Query that Finds Elements Based on Context (Visual Basic)</span></span>
<span data-ttu-id="03eb4-103">Někdy může být nutné napsat dotaz, který vybere prvky na základě jejich kontextu.</span><span class="sxs-lookup"><span data-stu-id="03eb4-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="03eb4-104">Je možné, že budete chtít filtrovat na základě předchozích nebo následujících prvků na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="03eb4-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="03eb4-105">Je možné, že budete chtít filtrovat na základě podřízených nebo nadřazených prvků.</span><span class="sxs-lookup"><span data-stu-id="03eb4-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="03eb4-106">To můžete provést tak, že zapíšete dotaz a použijete výsledky dotazu v klauzuli `where`.</span><span class="sxs-lookup"><span data-stu-id="03eb4-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="03eb4-107">Pokud je nutné nejprve otestovat proti hodnotě null a potom otestovat hodnotu, je vhodnější provést dotaz v klauzuli `let` a potom použít výsledky v klauzuli `where`.</span><span class="sxs-lookup"><span data-stu-id="03eb4-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03eb4-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="03eb4-108">Example</span></span>  
 <span data-ttu-id="03eb4-109">Následující příklad vybere všechny `p` prvky, které bezprostředně následuje `ul` element.</span><span class="sxs-lookup"><span data-stu-id="03eb4-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
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
  
 <span data-ttu-id="03eb4-110">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="03eb4-110">This code produces the following output:</span></span>  
  
```console  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="03eb4-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="03eb4-111">Example</span></span>  
 <span data-ttu-id="03eb4-112">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="03eb4-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="03eb4-113">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="03eb4-113">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="03eb4-114">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="03eb4-114">This code produces the following output:</span></span>  
  
```console  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="03eb4-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03eb4-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
- [<span data-ttu-id="03eb4-116">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03eb4-116">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
