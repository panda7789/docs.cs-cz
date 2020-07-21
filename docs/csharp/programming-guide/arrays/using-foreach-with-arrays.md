---
title: Použití příkazu foreach s poli – Průvodce programováním v C#
description: Příkaz foreach v jazyce C# prochází prvky pole. Pro jednorozměrná pole zpracovávají foreach prvky ve vzestupném pořadí indexu.
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: d924a3ef3351cbb30b809a1542f35314ee721852
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474537"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="d8d5a-104">Použití příkazu foreach s poli (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d8d5a-104">Using foreach with arrays (C# Programming Guide)</span></span>

<span data-ttu-id="d8d5a-105">Příkaz [foreach](../../language-reference/keywords/foreach-in.md) poskytuje jednoduchý a čistě způsob, jak iterovat prvky pole.</span><span class="sxs-lookup"><span data-stu-id="d8d5a-105">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="d8d5a-106">Pro jednorozměrná pole `foreach` zpracuje příkaz prvky ve vzestupném pořadí indexu, počínaje indexem 0 a končící indexem `Length - 1` :</span><span class="sxs-lookup"><span data-stu-id="d8d5a-106">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

<span data-ttu-id="d8d5a-107">U multidimenzionálních polí jsou elementy procházeny tak, že jsou nejprve zvyšovány indexy pravého rozměru, potom následující levá dimenze atd. vlevo:</span><span class="sxs-lookup"><span data-stu-id="d8d5a-107">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

<span data-ttu-id="d8d5a-108">Nicméně s multidimenzionálními poli, pomocí vnořené smyčky [for](../../language-reference/keywords/for.md) , získáte větší kontrolu nad pořadím, ve kterém mají být zpracovány prvky pole.</span><span class="sxs-lookup"><span data-stu-id="d8d5a-108">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8d5a-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8d5a-109">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="d8d5a-110">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="d8d5a-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d8d5a-111">Pole</span><span class="sxs-lookup"><span data-stu-id="d8d5a-111">Arrays</span></span>](index.md)
- [<span data-ttu-id="d8d5a-112">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="d8d5a-112">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="d8d5a-113">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="d8d5a-113">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="d8d5a-114">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="d8d5a-114">Jagged Arrays</span></span>](jagged-arrays.md)
