---
title: Pole jako objekty – Průvodce programováním v C#
description: Pole v jazyce C# jsou objekty abstraktního základního typu pole. Můžete použít vlastnosti a další členy třídy Array, jako je například vlastnost length.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 984def3ef74b07d7099fae6cae6d6f8ce7e03e12
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474719"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="1308d-104">Pole jako objekty (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1308d-104">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="1308d-105">V jazyce C# jsou pole vlastně objekty a nikoli pouze adresovatelné oblasti souvislé paměti jako v jazyce C a C++.</span><span class="sxs-lookup"><span data-stu-id="1308d-105">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="1308d-106"><xref:System.Array>je abstraktní základní typ pro všechny typy polí.</span><span class="sxs-lookup"><span data-stu-id="1308d-106"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="1308d-107">Můžete použít vlastnosti a další členy třídy, které <xref:System.Array> mají.</span><span class="sxs-lookup"><span data-stu-id="1308d-107">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="1308d-108">Příkladem je použití <xref:System.Array.Length%2A> Vlastnosti k získání délky pole.</span><span class="sxs-lookup"><span data-stu-id="1308d-108">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="1308d-109">Následující kód přiřadí délku `numbers` pole, tj `5` . proměnné s názvem `lengthOfNumbers` :</span><span class="sxs-lookup"><span data-stu-id="1308d-109">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="1308d-110"><xref:System.Array>Třída poskytuje mnoho dalších užitečných metod a vlastností pro řazení, vyhledávání a kopírování polí.</span><span class="sxs-lookup"><span data-stu-id="1308d-110">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>

## <a name="example"></a><span data-ttu-id="1308d-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="1308d-111">Example</span></span>

<span data-ttu-id="1308d-112">Tento příklad používá <xref:System.Array.Rank%2A> vlastnost k zobrazení počtu rozměrů pole.</span><span class="sxs-lookup"><span data-stu-id="1308d-112">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="1308d-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="1308d-113">See also</span></span>

- [<span data-ttu-id="1308d-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="1308d-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1308d-115">Pole</span><span class="sxs-lookup"><span data-stu-id="1308d-115">Arrays</span></span>](./index.md)
- [<span data-ttu-id="1308d-116">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="1308d-116">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="1308d-117">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="1308d-117">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="1308d-118">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="1308d-118">Jagged Arrays</span></span>](./jagged-arrays.md)
