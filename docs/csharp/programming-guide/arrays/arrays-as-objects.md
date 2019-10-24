---
title: Pole jako objekty – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 9905168662496c46d20f191c04f21d8630d02fa2
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772113"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="42144-102">Pole jako objekty (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="42144-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="42144-103">V C#jsou pole vlastně objekty a nikoli pouze adresovatelné oblasti souvislé paměti jako v jazyce C a C++.</span><span class="sxs-lookup"><span data-stu-id="42144-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="42144-104"><xref:System.Array> je abstraktní základní typ pro všechny typy polí.</span><span class="sxs-lookup"><span data-stu-id="42144-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="42144-105">Můžete použít vlastnosti a jiné členy třídy, které <xref:System.Array> má.</span><span class="sxs-lookup"><span data-stu-id="42144-105">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="42144-106">Příkladem je použití vlastnosti <xref:System.Array.Length%2A> k získání délky pole.</span><span class="sxs-lookup"><span data-stu-id="42144-106">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="42144-107">Následující kód přiřadí délku `numbers` pole, které je `5`, do proměnné s názvem `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="42144-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="42144-108">Třída <xref:System.Array> poskytuje mnoho dalších užitečných metod a vlastností pro řazení, vyhledávání a kopírování polí.</span><span class="sxs-lookup"><span data-stu-id="42144-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>

## <a name="example"></a><span data-ttu-id="42144-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="42144-109">Example</span></span>

<span data-ttu-id="42144-110">V tomto příkladu se používá vlastnost <xref:System.Array.Rank%2A> k zobrazení počtu rozměrů pole.</span><span class="sxs-lookup"><span data-stu-id="42144-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="42144-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42144-111">See also</span></span>

- [<span data-ttu-id="42144-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="42144-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="42144-113">Pole</span><span class="sxs-lookup"><span data-stu-id="42144-113">Arrays</span></span>](./index.md)
- [<span data-ttu-id="42144-114">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="42144-114">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="42144-115">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="42144-115">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="42144-116">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="42144-116">Jagged Arrays</span></span>](./jagged-arrays.md)
