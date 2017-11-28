---
title: "Postupy: zápis dotaz, který vyhledá elementy na základě kontextu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b085290-ddc1-4126-aaa0-e4c95a3d9a09
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 635a8c06d5ad928e192b8cd15862aa02192f94d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-visual-basic"></a><span data-ttu-id="1034a-102">Postupy: zápis dotaz, který vyhledá elementy na základě kontextu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1034a-102">How to: Write a Query that Finds Elements Based on Context (Visual Basic)</span></span>
<span data-ttu-id="1034a-103">V některých případech můžete chtít vytvořit dotaz, který vybere elementy na základě jejich kontextu.</span><span class="sxs-lookup"><span data-stu-id="1034a-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="1034a-104">Můžete filtrovat na základě před nebo po prvků.</span><span class="sxs-lookup"><span data-stu-id="1034a-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="1034a-105">Můžete filtrovat na základě podřízené domény nebo nadřazenými prvky.</span><span class="sxs-lookup"><span data-stu-id="1034a-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="1034a-106">To provedete zadáním dotazu a použitím výsledků dotazu v `where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="1034a-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="1034a-107">Pokud musíte nejprve porovnat s hodnotou null a otestujte hodnota, je pohodlnější udělat dotazu `let` klauzule a pak použijte výsledky v `where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="1034a-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1034a-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="1034a-108">Example</span></span>  
 <span data-ttu-id="1034a-109">Následující příklad vybere všechny `p` prvky, které jsou bezprostředně následované `ul` elementu.</span><span class="sxs-lookup"><span data-stu-id="1034a-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
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
  
 <span data-ttu-id="1034a-110">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1034a-110">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="1034a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="1034a-111">Example</span></span>  
 <span data-ttu-id="1034a-112">Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1034a-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="1034a-113">Další informace najdete v tématu [práci s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="1034a-113">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="1034a-114">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1034a-114">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="1034a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="1034a-115">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Parse%2A>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A>  
 <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
 <xref:System.Linq.Enumerable.FirstOrDefault%2A>  
 [<span data-ttu-id="1034a-116">Základní dotazy (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1034a-116">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
