---
title: Příklad odloženého provedení
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 863b018b6047d61f6fb4a5c1ac68151ed69d24a1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410796"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="ef841-102">Příklad odloženého provedení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef841-102">Deferred Execution Example (Visual Basic)</span></span>

<span data-ttu-id="ef841-103">Toto téma ukazuje, jak odložené provádění a opožděné vyhodnocení ovlivní spuštění dotazů LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="ef841-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>

## <a name="example"></a><span data-ttu-id="ef841-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef841-104">Example</span></span>

<span data-ttu-id="ef841-105">Následující příklad ukazuje pořadí spouštění při použití metody rozšíření, která používá odložené provádění.</span><span class="sxs-lookup"><span data-stu-id="ef841-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="ef841-106">Příklad deklaruje pole tří řetězců.</span><span class="sxs-lookup"><span data-stu-id="ef841-106">The example declares an array of three strings.</span></span> <span data-ttu-id="ef841-107">Poté provede iteraci kolekcí vrácenou `ConvertCollectionToUpperCase` .</span><span class="sxs-lookup"><span data-stu-id="ef841-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module Module1

    <Extension()>
    Private Iterator Function ConvertCollectionToUpperCase(
    ByVal source As IEnumerable(Of String)) _
    As IEnumerable(Of String)
        For Each str As String In source
            Console.WriteLine("ToUpper: source {0}", str)
            Yield str.ToUpper()
        Next
    End Function

    Sub Main()
        Dim stringArray = New String() {"abc", "def", "ghi"}

        Dim q = From str In stringArray.ConvertCollectionToUpperCase()
                Select str

        For Each Str As String In q
            Console.WriteLine("Main: str {0}", Str)
        Next
    End Sub

End Module
```

<span data-ttu-id="ef841-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ef841-108">This example produces the following output:</span></span>

```console
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

<span data-ttu-id="ef841-109">Všimněte si, že při iteraci v kolekci `ConvertCollectionToUpperCase` , kterou vrátí, každá položka je načtena ze zdrojového pole řetězce a převedena na velká písmena před načtením další položky ze zdrojového pole řetězce.</span><span class="sxs-lookup"><span data-stu-id="ef841-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>

<span data-ttu-id="ef841-110">Můžete vidět, že celé pole řetězců není převedeno na velká písmena před tím, než se každá položka v vrácené kolekci zpracuje ve `foreach` smyčce v `Main` .</span><span class="sxs-lookup"><span data-stu-id="ef841-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef841-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef841-111">See also</span></span>

- [<span data-ttu-id="ef841-112">Kurz: odložené provádění (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef841-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](tutorial-deferred-execution.md)
