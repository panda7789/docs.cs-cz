---
title: 'Postupy: ladění sady výsledků dotazu prázdný (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 33dcfe9b0c0ad41353ca845ed4d8e21ff77292df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642971"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="fc6c5-102">Postupy: ladění sady výsledků dotazu prázdný (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc6c5-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>
<span data-ttu-id="fc6c5-103">Jeden z nejběžnějších problémů při dotazování stromy XML je, že pokud stromu XML má výchozí obor názvů, vývojář někdy zapíše dotazu, jako by soubor XML není v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fc6c5-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="fc6c5-104">První sadu příklady v tomto tématu ukazuje obvyklým způsobem, že je načteno kód XML v výchozí obor názvů a je dotazován nesprávně.</span><span class="sxs-lookup"><span data-stu-id="fc6c5-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="fc6c5-105">Druhá sada příklady zobrazit potřebné opravy tak, aby v oboru názvů se můžete dotazovat XML.</span><span class="sxs-lookup"><span data-stu-id="fc6c5-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="fc6c5-106">Další informace najdete v tématu [práci s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="fc6c5-106">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc6c5-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="fc6c5-107">Example</span></span>  
 <span data-ttu-id="fc6c5-108">Tento příklad ukazuje vytvoření XML v oboru názvů a nastavte dotaz, který vrací prázdný výsledek.</span><span class="sxs-lookup"><span data-stu-id="fc6c5-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns='http://www.adventure-works.com'>  
        <Child>1</Child>  
        <Child>2</Child>  
        <Child>3</Child>  
        <AnotherChild>4</AnotherChild>  
        <AnotherChild>5</AnotherChild>  
        <AnotherChild>6</AnotherChild>  
    </Root>  
Dim c1 As IEnumerable(Of XElement) = _  
        From el In root.<Child> _  
        Select el  
Console.WriteLine("Result set follows:")  
For Each el As XElement In c1  
    Console.WriteLine(el.Value)  
Next  
Console.WriteLine("End of result set")  
```  
  
 <span data-ttu-id="fc6c5-109">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="fc6c5-109">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="fc6c5-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="fc6c5-110">Example</span></span>  
 <span data-ttu-id="fc6c5-111">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je zakódovaný správně.</span><span class="sxs-lookup"><span data-stu-id="fc6c5-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="fc6c5-112">Řešení je deklarace a inicializace globální výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="fc6c5-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="fc6c5-113">Tato výchozí obor názvů umístí všechny vlastnosti XML.</span><span class="sxs-lookup"><span data-stu-id="fc6c5-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="fc6c5-114">Žádné další úpravy jsou požadovány v příkladu, aby byla správně fungovat.</span><span class="sxs-lookup"><span data-stu-id="fc6c5-114">No other modifications are required to the example to make it work properly.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="fc6c5-115">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="fc6c5-115">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc6c5-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc6c5-116">See Also</span></span>  
 [<span data-ttu-id="fc6c5-117">Základní dotazy (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc6c5-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
