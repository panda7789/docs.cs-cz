---
title: "Postupy: Řazení pole v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 310c2dacb384de49c80073840c6c58d37f3937d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="f2a2b-102">Postupy: Řazení pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f2a2b-102">How to: Sort An Array in Visual Basic</span></span>
<span data-ttu-id="f2a2b-103">Tento příklad deklaruje pole `String` objektů s názvem `zooAnimals`, naplní jej a abecedně seřadí.</span><span class="sxs-lookup"><span data-stu-id="f2a2b-103">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2a2b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2a2b-104">Example</span></span>  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f2a2b-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f2a2b-105">Compiling the Code</span></span>  
 <span data-ttu-id="f2a2b-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f2a2b-106">This example requires:</span></span>  
  
-   <span data-ttu-id="f2a2b-107">Přístup k Mscorlib.dll a <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f2a2b-107">Access to Mscorlib.dll and the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f2a2b-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="f2a2b-108">Robust Programming</span></span>  
 <span data-ttu-id="f2a2b-109">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="f2a2b-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f2a2b-110">Pole je prázdné (<xref:System.ArgumentNullException> třídy)</span><span class="sxs-lookup"><span data-stu-id="f2a2b-110">Array is empty (<xref:System.ArgumentNullException> class)</span></span>  
  
-   <span data-ttu-id="f2a2b-111">Pole je multidimenzionální (<xref:System.RankException> třídy)</span><span class="sxs-lookup"><span data-stu-id="f2a2b-111">Array is multidimensional (<xref:System.RankException> class)</span></span>  
  
-   <span data-ttu-id="f2a2b-112">Jeden či více elementů pole neimplementují <xref:System.IComparable> rozhraní (<xref:System.InvalidOperationException> třídy)</span><span class="sxs-lookup"><span data-stu-id="f2a2b-112">One or more elements of the array do not implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a2b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2a2b-113">See Also</span></span>  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="f2a2b-114">Pole</span><span class="sxs-lookup"><span data-stu-id="f2a2b-114">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="f2a2b-115">Řešení potíží s poli</span><span class="sxs-lookup"><span data-stu-id="f2a2b-115">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [<span data-ttu-id="f2a2b-116">Kolekce</span><span class="sxs-lookup"><span data-stu-id="f2a2b-116">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [<span data-ttu-id="f2a2b-117">Pro každou... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="f2a2b-117">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
