---
title: Použití foreach s poli - C# Programovací průvodce
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: bb121b0f5d990ef6e596b34a45606e2abde6811a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705675"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="8818f-102">Použití foreach s poli (C# Programovací průvodce)</span><span class="sxs-lookup"><span data-stu-id="8818f-102">Using foreach with arrays (C# Programming Guide)</span></span>

<span data-ttu-id="8818f-103">[Foreach](../../language-reference/keywords/foreach-in.md) prohlášení poskytuje jednoduchý, čistý způsob iterate prostřednictvím prvků pole.</span><span class="sxs-lookup"><span data-stu-id="8818f-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="8818f-104">U jednorozměrných polí `foreach` příkaz zpracovává prvky ve zvýšení pořadí indexu, `Length - 1`počínaje indexem 0 a konče indexem :</span><span class="sxs-lookup"><span data-stu-id="8818f-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

<span data-ttu-id="8818f-105">U vícerozměrných polí jsou prvky provázány tak, že indexy nejvýraznější ho vpravo jsou nejprve zvýšeny, pak další levý rozměr a tak dále doleva:</span><span class="sxs-lookup"><span data-stu-id="8818f-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

<span data-ttu-id="8818f-106">Však s vícerozměrných polí, pomocí vnořené [pro](../../language-reference/keywords/for.md) smyčky vám dává větší kontrolu nad pořadí, ve kterém chcete zpracovat prvky pole.</span><span class="sxs-lookup"><span data-stu-id="8818f-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="8818f-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="8818f-107">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="8818f-108">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8818f-108">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8818f-109">Pole</span><span class="sxs-lookup"><span data-stu-id="8818f-109">Arrays</span></span>](index.md)
- [<span data-ttu-id="8818f-110">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="8818f-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="8818f-111">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="8818f-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="8818f-112">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="8818f-112">Jagged Arrays</span></span>](jagged-arrays.md)
