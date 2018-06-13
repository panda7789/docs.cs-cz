---
title: Odložené provedení příklad (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: a9827b73ebc0df589a14032d99b32d1e1bc891ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642126"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="4d2f6-102">Odložené provedení příklad (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d2f6-102">Deferred Execution Example (Visual Basic)</span></span>
<span data-ttu-id="4d2f6-103">Toto téma ukazuje, jak odložené provedení a opožděné vyhodnocení ovlivnit provádění vaší technologie LINQ to XML dotazy.</span><span class="sxs-lookup"><span data-stu-id="4d2f6-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d2f6-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d2f6-104">Example</span></span>  
 <span data-ttu-id="4d2f6-105">Následující příklad ukazuje pořadí provádění při použití metody rozšíření, která používá odložené provedení.</span><span class="sxs-lookup"><span data-stu-id="4d2f6-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="4d2f6-106">V příkladu deklaruje pole tři řetězců.</span><span class="sxs-lookup"><span data-stu-id="4d2f6-106">The example declares an array of three strings.</span></span> <span data-ttu-id="4d2f6-107">Ji pak iteruje kolekcí vrácený `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="4d2f6-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="4d2f6-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4d2f6-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="4d2f6-109">Všimněte si, že když iterace v rámci kolekce vrácené `ConvertCollectionToUpperCase`, každé položky se načítají z pole řetězců zdroje a převeden na velká písmena před další položky se načítají z pole řetězců zdroje.</span><span class="sxs-lookup"><span data-stu-id="4d2f6-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="4d2f6-110">Uvidíte, že celé pole řetězce není převeden na velká písmena, před každou položku v kolekci vrácený při zpracování ve `foreach` smyčky v `Main`.</span><span class="sxs-lookup"><span data-stu-id="4d2f6-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d2f6-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d2f6-111">See Also</span></span>  
 [<span data-ttu-id="4d2f6-112">Kurz: Odložený provádění (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d2f6-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
