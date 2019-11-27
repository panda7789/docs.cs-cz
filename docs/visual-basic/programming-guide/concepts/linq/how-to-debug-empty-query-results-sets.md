---
title: 'Postupy: ladění prázdných sad výsledků dotazu'
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 21c161a702338c0c6943fa09212deaea7fdd72f9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353077"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="6aa96-102">Postupy: ladění prázdných sad výsledků dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6aa96-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>

<span data-ttu-id="6aa96-103">Jedním z nejběžnějších problémů při dotazování na stromy XML je, že pokud má strom XML výchozí obor názvů, vývojář někdy zapíše dotaz, jako by kód XML nebyl v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6aa96-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>

<span data-ttu-id="6aa96-104">První sada příkladů v tomto tématu ukazuje typický způsob, jakým je načten XML ve výchozím oboru názvů a je dotaz na něj nesprávně.</span><span class="sxs-lookup"><span data-stu-id="6aa96-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>

<span data-ttu-id="6aa96-105">Druhá sada příkladů ukazuje nezbytné opravy, aby bylo možné dotazovat XML v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6aa96-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>

<span data-ttu-id="6aa96-106">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6aa96-106">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>

## <a name="example"></a><span data-ttu-id="6aa96-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="6aa96-107">Example</span></span>

<span data-ttu-id="6aa96-108">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který vrací prázdnou sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="6aa96-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>

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

<span data-ttu-id="6aa96-109">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="6aa96-109">This example produces the following result:</span></span>

```console
Result set follows:
End of result set
```

## <a name="example"></a><span data-ttu-id="6aa96-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="6aa96-110">Example</span></span>

<span data-ttu-id="6aa96-111">Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je správně kódován.</span><span class="sxs-lookup"><span data-stu-id="6aa96-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>

<span data-ttu-id="6aa96-112">Řešením je deklarovat a inicializovat globální výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="6aa96-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="6aa96-113">Tím se umístí všechny vlastnosti XML ve výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6aa96-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="6aa96-114">V příkladu nejsou k dispozici žádné další úpravy, aby mohla správně fungovat.</span><span class="sxs-lookup"><span data-stu-id="6aa96-114">No other modifications are required to the example to make it work properly.</span></span>

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

<span data-ttu-id="6aa96-115">Tento příklad vytvoří následující výsledek:</span><span class="sxs-lookup"><span data-stu-id="6aa96-115">This example produces the following result:</span></span>

```console
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="6aa96-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6aa96-116">See also</span></span>

- [<span data-ttu-id="6aa96-117">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6aa96-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
