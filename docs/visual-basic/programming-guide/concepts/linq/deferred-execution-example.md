---
title: "Odložené provedení příklad (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a4d2146901d9282b0df706b483afef79f714f660
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="de92a-102">Odložené provedení příklad (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de92a-102">Deferred Execution Example (Visual Basic)</span></span>
<span data-ttu-id="de92a-103">Toto téma ukazuje, jak odložené provedení a opožděné vyhodnocení ovlivnit provádění vaší technologie LINQ to XML dotazy.</span><span class="sxs-lookup"><span data-stu-id="de92a-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de92a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="de92a-104">Example</span></span>  
 <span data-ttu-id="de92a-105">Následující příklad ukazuje pořadí provádění při použití metody rozšíření, která používá odložené provedení.</span><span class="sxs-lookup"><span data-stu-id="de92a-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="de92a-106">V příkladu deklaruje pole tři řetězců.</span><span class="sxs-lookup"><span data-stu-id="de92a-106">The example declares an array of three strings.</span></span> <span data-ttu-id="de92a-107">Ji pak iteruje kolekcí vrácený `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="de92a-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="de92a-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="de92a-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="de92a-109">Všimněte si, že když iterace v rámci kolekce vrácené `ConvertCollectionToUpperCase`, každé položky se načítají z pole řetězců zdroje a převeden na velká písmena před další položky se načítají z pole řetězců zdroje.</span><span class="sxs-lookup"><span data-stu-id="de92a-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="de92a-110">Uvidíte, že celé pole řetězce není převeden na velká písmena, před každou položku v kolekci vrácený při zpracování ve `foreach` smyčky v `Main`.</span><span class="sxs-lookup"><span data-stu-id="de92a-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de92a-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="de92a-111">See Also</span></span>  
 [<span data-ttu-id="de92a-112">Kurz: Odložený provádění (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de92a-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
