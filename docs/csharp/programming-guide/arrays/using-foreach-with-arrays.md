---
title: Použití příkazu foreach s poli C# – Průvodce programováním
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: bb121b0f5d990ef6e596b34a45606e2abde6811a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705675"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="60fab-102">Použití příkazu foreach s poliC# (Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="60fab-102">Using foreach with arrays (C# Programming Guide)</span></span>

<span data-ttu-id="60fab-103">Příkaz [foreach](../../language-reference/keywords/foreach-in.md) poskytuje jednoduchý a čistě způsob, jak iterovat prvky pole.</span><span class="sxs-lookup"><span data-stu-id="60fab-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="60fab-104">Pro jednorozměrná pole zpracovává příkaz `foreach` prvky ve vzestupném pořadí indexů počínaje indexem 0 a končí `Length - 1`indexu:</span><span class="sxs-lookup"><span data-stu-id="60fab-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

<span data-ttu-id="60fab-105">U multidimenzionálních polí jsou elementy procházeny tak, že jsou nejprve zvyšovány indexy pravého rozměru, potom následující levá dimenze atd. vlevo:</span><span class="sxs-lookup"><span data-stu-id="60fab-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

<span data-ttu-id="60fab-106">Nicméně s multidimenzionálními poli, pomocí vnořené smyčky [for](../../language-reference/keywords/for.md) , získáte větší kontrolu nad pořadím, ve kterém mají být zpracovány prvky pole.</span><span class="sxs-lookup"><span data-stu-id="60fab-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="60fab-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60fab-107">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="60fab-108">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="60fab-108">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="60fab-109">Pole</span><span class="sxs-lookup"><span data-stu-id="60fab-109">Arrays</span></span>](index.md)
- [<span data-ttu-id="60fab-110">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="60fab-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="60fab-111">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="60fab-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="60fab-112">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="60fab-112">Jagged Arrays</span></span>](jagged-arrays.md)
