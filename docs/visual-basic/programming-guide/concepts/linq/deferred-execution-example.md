---
title: Příklad odloženého provedení (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 29f118b3e6d49840b94277f17858f1339f2fb08c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838923"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="ffe17-102">Příklad odloženého provedení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ffe17-102">Deferred Execution Example (Visual Basic)</span></span>
<span data-ttu-id="ffe17-103">Toto téma ukazuje, jak odložené provedení a opožděné vyhodnocení vliv na spuštění vašich dotazech LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="ffe17-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffe17-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ffe17-104">Example</span></span>  
 <span data-ttu-id="ffe17-105">Následující příklad ukazuje pořadí provádění, když použijete metodu rozšíření, která používá odloženého provedení.</span><span class="sxs-lookup"><span data-stu-id="ffe17-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="ffe17-106">V příkladu deklaruje pole tří řetězců.</span><span class="sxs-lookup"><span data-stu-id="ffe17-106">The example declares an array of three strings.</span></span> <span data-ttu-id="ffe17-107">Pak Iteruje přes kolekci vrácené poskytovatelem `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="ffe17-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="ffe17-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ffe17-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="ffe17-109">Všimněte si, že při procházení kolekci vrácené poskytovatelem `ConvertCollectionToUpperCase`, každá položka je načten z řetězcového pole zdroje a převedený na velká písmena před další položky se načtou ze zdrojového pole řetězce.</span><span class="sxs-lookup"><span data-stu-id="ffe17-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="ffe17-110">Uvidíte, že celého pole řetězce není před každou položku v kolekci vrácené, jsou zpracovávána v převedený na velká písmena `foreach` smyčky v `Main`.</span><span class="sxs-lookup"><span data-stu-id="ffe17-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffe17-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ffe17-111">See also</span></span>

- [<span data-ttu-id="ffe17-112">Kurz: Odložené provedení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ffe17-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
