---
title: Použití příkazu foreach s poli (Průvodce programováním v C#)
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: b858f35167e24390a729769487ce98908a3d349f
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549452"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="1530b-102">Použití příkazu foreach s poli (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1530b-102">Using foreach with Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="1530b-103">[Foreach](../../language-reference/keywords/foreach-in.md) příkaz poskytuje jednoduché a vyčištění způsob k iteraci v rámci prvků pole.</span><span class="sxs-lookup"><span data-stu-id="1530b-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="1530b-104">Pro jednorozměrná pole `foreach` příkaz zpracovává prvky v roste pořadí index s indexem 0 počáteční a koncovou s indexem `Length - 1`:</span><span class="sxs-lookup"><span data-stu-id="1530b-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

<span data-ttu-id="1530b-105">Pro vícerozměrných polí je elementy provázán tak, aby indexy, které nejvíce vpravo dimenze jsou vyšší první a pak další levém dimenze, a tak dále na levé straně:</span><span class="sxs-lookup"><span data-stu-id="1530b-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

<span data-ttu-id="1530b-106">Nicméně s vícerozměrná pole pomocí vnořený [pro](../../language-reference/keywords/for.md) smyčky vám dává větší kontrolu nad pořadí, ve které se má zpracovat elementy pole.</span><span class="sxs-lookup"><span data-stu-id="1530b-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="1530b-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="1530b-107">See also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="1530b-108">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1530b-108">C# Programming Guide</span></span>](../index.md)  
 [<span data-ttu-id="1530b-109">Pole</span><span class="sxs-lookup"><span data-stu-id="1530b-109">Arrays</span></span>](index.md)  
 [<span data-ttu-id="1530b-110">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="1530b-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)  
 [<span data-ttu-id="1530b-111">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="1530b-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)  
 [<span data-ttu-id="1530b-112">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="1530b-112">Jagged Arrays</span></span>](jagged-arrays.md)
