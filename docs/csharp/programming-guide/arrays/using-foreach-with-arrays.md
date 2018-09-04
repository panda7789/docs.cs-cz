---
title: Použití příkazu foreach s poli (Průvodce programováním v C#)
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: 298ee915bbe11313f3b33ea7dae9353ef956a231
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509532"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="15bfe-102">Použití příkazu foreach s poli (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="15bfe-102">Using foreach with Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="15bfe-103">[Foreach](../../language-reference/keywords/foreach-in.md) příkaz umožňuje jednoduchý a přímý způsob iterace prvků pole.</span><span class="sxs-lookup"><span data-stu-id="15bfe-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="15bfe-104">Pro jednorozměrné pole `foreach` příkaz zpracovává prvky ve vzestupném pořadí index, od indexu 0 a končí index `Length - 1`:</span><span class="sxs-lookup"><span data-stu-id="15bfe-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

<span data-ttu-id="15bfe-105">Pro vícerozměrná pole je provázán prvků tak, že indexy rozměr nejvíce vpravo se zvýšenou první pak dimenzi a tak dále zleva další vlevo:</span><span class="sxs-lookup"><span data-stu-id="15bfe-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

<span data-ttu-id="15bfe-106">Však s multidimenzionálními poli použijete [pro](../../language-reference/keywords/for.md) smyčky vám dává větší kontrolu nad pořadí, ve které se má zpracovat prvky pole.</span><span class="sxs-lookup"><span data-stu-id="15bfe-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="15bfe-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="15bfe-107">See Also</span></span>

- <xref:System.Array>  
- [<span data-ttu-id="15bfe-108">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="15bfe-108">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="15bfe-109">Pole</span><span class="sxs-lookup"><span data-stu-id="15bfe-109">Arrays</span></span>](index.md)  
- [<span data-ttu-id="15bfe-110">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="15bfe-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)  
- [<span data-ttu-id="15bfe-111">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="15bfe-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)  
- [<span data-ttu-id="15bfe-112">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="15bfe-112">Jagged Arrays</span></span>](jagged-arrays.md)
