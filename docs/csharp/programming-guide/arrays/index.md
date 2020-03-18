---
title: Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: bbabc84c144e5b3415c19f346b890782e251662c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715059"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="b44e5-102">Pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b44e5-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="b44e5-103">Do datové struktury pole můžete uložit více proměnných stejného typu.</span><span class="sxs-lookup"><span data-stu-id="b44e5-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="b44e5-104">Deklarujete pole zadáním typu jeho prvků.</span><span class="sxs-lookup"><span data-stu-id="b44e5-104">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="b44e5-105">Pokud chcete, aby pole uklánělo prvky libovolného typu, můžete zadat `object` jako jeho typ.</span><span class="sxs-lookup"><span data-stu-id="b44e5-105">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="b44e5-106">V systému sjednoceného typu jazyka C# všechny typy, předdefinované a uživatelem definované, <xref:System.Object>typy odkazů a typy hodnot, dědí přímo nebo nepřímo z .</span><span class="sxs-lookup"><span data-stu-id="b44e5-106">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="b44e5-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b44e5-107">Example</span></span>

<span data-ttu-id="b44e5-108">Následující příklad vytvoří jednorozměrná, vícerozměrná a zubatá pole:</span><span class="sxs-lookup"><span data-stu-id="b44e5-108">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="b44e5-109">Přehled pole</span><span class="sxs-lookup"><span data-stu-id="b44e5-109">Array overview</span></span>

<span data-ttu-id="b44e5-110">Pole má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="b44e5-110">An array has the following properties:</span></span>

- <span data-ttu-id="b44e5-111">Pole může být [jednorozměrné](single-dimensional-arrays.md), [vícerozměrné](multidimensional-arrays.md) nebo [zubaté](jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="b44e5-111">An array can be [Single-Dimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) or [Jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="b44e5-112">Počet dimenzí a délka každé dimenze jsou stanoveny při vytvoření instance pole.</span><span class="sxs-lookup"><span data-stu-id="b44e5-112">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="b44e5-113">Tyto hodnoty nelze změnit během životnosti instance.</span><span class="sxs-lookup"><span data-stu-id="b44e5-113">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="b44e5-114">Výchozí hodnoty číselných prvků pole jsou nastaveny na nulu a referenční prvky jsou nastaveny na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b44e5-114">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="b44e5-115">Zubaté pole je pole polí, a proto jeho prvky jsou `null`typy odkazů a jsou inicializovány na .</span><span class="sxs-lookup"><span data-stu-id="b44e5-115">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="b44e5-116">Pole jsou indexována bez `n` indexu: pole `0` s `n-1`prvky je indexováno z do .</span><span class="sxs-lookup"><span data-stu-id="b44e5-116">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="b44e5-117">Prvky pole mohou být libovolného typu, včetně typu pole.</span><span class="sxs-lookup"><span data-stu-id="b44e5-117">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="b44e5-118">Typy polí jsou [typy odkazů](../../language-reference/keywords/reference-types.md) odvozené <xref:System.Array>z abstraktního základního typu .</span><span class="sxs-lookup"><span data-stu-id="b44e5-118">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="b44e5-119">Vzhledem k <xref:System.Collections.IEnumerable> tomu, že tento typ implementuje a <xref:System.Collections.Generic.IEnumerable%601>, můžete použít [foreach](../../language-reference/keywords/foreach-in.md) iteraci na všech polích v C#.</span><span class="sxs-lookup"><span data-stu-id="b44e5-119">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

## <a name="related-sections"></a><span data-ttu-id="b44e5-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b44e5-120">Related sections</span></span>

- [<span data-ttu-id="b44e5-121">Pole jako objekty</span><span class="sxs-lookup"><span data-stu-id="b44e5-121">Arrays as Objects</span></span>](arrays-as-objects.md)
- [<span data-ttu-id="b44e5-122">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="b44e5-122">Using foreach with Arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="b44e5-123">Předávání polí jako argumentů</span><span class="sxs-lookup"><span data-stu-id="b44e5-123">Passing Arrays as Arguments</span></span>](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a><span data-ttu-id="b44e5-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b44e5-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b44e5-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="b44e5-125">See also</span></span>

- [<span data-ttu-id="b44e5-126">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b44e5-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b44e5-127">Kolekce</span><span class="sxs-lookup"><span data-stu-id="b44e5-127">Collections</span></span>](../concepts/collections.md)
