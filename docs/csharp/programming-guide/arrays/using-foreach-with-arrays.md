---
title: "Použití příkazu foreach s poli (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 797cb9a63a5e1009b170b2afda8634bd21a50035
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="dfbcf-102">Použití příkazu foreach s poli (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="dfbcf-102">Using foreach with Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="dfbcf-103">C# také poskytuje [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="dfbcf-103">C# also provides the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="dfbcf-104">Tento příkaz umožňuje jednoduchý a přímý způsob iterace prvků jakéhokoli pole nebo vyčíslitelné kolekce.</span><span class="sxs-lookup"><span data-stu-id="dfbcf-104">This statement provides a simple, clean way to iterate through the elements of an array or any enumerable collection.</span></span> <span data-ttu-id="dfbcf-105">`foreach` Příkaz zpracovává prvky v pořadí vrácených typu pole nebo kolekce enumerátor, který je obvykle z 0-té element na poslední.</span><span class="sxs-lookup"><span data-stu-id="dfbcf-105">The `foreach` statement processes elements in the order returned by the array or collection type’s enumerator, which is usually from the 0th element to the last.</span></span> <span data-ttu-id="dfbcf-106">Například následující kód vytvoří pole s názvem `numbers` a její iteruje `foreach` příkaz:</span><span class="sxs-lookup"><span data-stu-id="dfbcf-106">For example, the following code creates an array called `numbers` and iterates through it with the `foreach` statement:</span></span>  
  
 [!code-csharp[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 <span data-ttu-id="dfbcf-107">S multidimenzionálními poli můžete použít stejnou metodu pro iteraci skrz prvky, například:</span><span class="sxs-lookup"><span data-stu-id="dfbcf-107">With multidimensional arrays, you can use the same method to iterate through the elements, for example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 <span data-ttu-id="dfbcf-108">Nicméně s vícerozměrná pole pomocí vnořený [pro](../../../csharp/language-reference/keywords/for.md) smyčky vám dává větší kontrolu nad prvků pole.</span><span class="sxs-lookup"><span data-stu-id="dfbcf-108">However, with multidimensional arrays, using a nested [for](../../../csharp/language-reference/keywords/for.md) loop gives you more control over the array elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfbcf-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="dfbcf-109">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="dfbcf-110">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="dfbcf-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="dfbcf-111">Pole</span><span class="sxs-lookup"><span data-stu-id="dfbcf-111">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="dfbcf-112">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="dfbcf-112">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="dfbcf-113">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="dfbcf-113">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="dfbcf-114">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="dfbcf-114">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
