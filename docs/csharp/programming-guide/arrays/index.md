---
title: Pole – Průvodce programováním v C#
description: Uložení více proměnných stejného typu v datové struktuře pole v jazyce C#. Deklarujte pole zadáním typu nebo zadáním objektu pro uložení libovolného typu.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: e302ff2e4c2488c4899c4eb99a666d2d322119ce
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474732"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="76c85-104">Pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="76c85-104">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="76c85-105">V datové struktuře pole můžete uložit více proměnných stejného typu.</span><span class="sxs-lookup"><span data-stu-id="76c85-105">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="76c85-106">Deklarujete pole zadáním typu jeho prvků.</span><span class="sxs-lookup"><span data-stu-id="76c85-106">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="76c85-107">Chcete-li, aby pole ukládalo prvky libovolného typu, můžete zadat `object` jako jeho typ.</span><span class="sxs-lookup"><span data-stu-id="76c85-107">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="76c85-108">V rámci sjednoceného typu systému C# všechny typy, předdefinované a uživatelsky definované typy odkazů a typy hodnot dědí přímo nebo nepřímo z <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="76c85-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="76c85-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="76c85-109">Example</span></span>

<span data-ttu-id="76c85-110">Následující příklad vytvoří jednorozměrná, multidimenzionální a vícenásobná pole:</span><span class="sxs-lookup"><span data-stu-id="76c85-110">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="76c85-111">Přehled pole</span><span class="sxs-lookup"><span data-stu-id="76c85-111">Array overview</span></span>

<span data-ttu-id="76c85-112">Pole má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="76c85-112">An array has the following properties:</span></span>

- <span data-ttu-id="76c85-113">Pole [může být jednorozměrné](single-dimensional-arrays.md), [multidimenzionální](multidimensional-arrays.md) nebo [vícenásobné](jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="76c85-113">An array can be [Single-Dimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) or [Jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="76c85-114">Počet rozměrů a délka každé dimenze jsou vytvořeny při vytvoření instance pole.</span><span class="sxs-lookup"><span data-stu-id="76c85-114">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="76c85-115">Tyto hodnoty nejde během životnosti instance změnit.</span><span class="sxs-lookup"><span data-stu-id="76c85-115">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="76c85-116">Výchozí hodnoty prvků číselného pole jsou nastaveny na nulu a referenční prvky jsou nastaveny na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="76c85-116">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="76c85-117">Vícenásobné pole je pole pole, a proto jeho prvky jsou odkazové typy a jsou inicializovány na `null` .</span><span class="sxs-lookup"><span data-stu-id="76c85-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="76c85-118">Pole jsou indexována nulou: pole s `n` elementy je indexováno z `0` do `n-1` .</span><span class="sxs-lookup"><span data-stu-id="76c85-118">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="76c85-119">Prvky pole mohou být libovolného typu, včetně typu pole.</span><span class="sxs-lookup"><span data-stu-id="76c85-119">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="76c85-120">Typy polí jsou [odkazové typy](../../language-reference/keywords/reference-types.md) odvozené od abstraktního základního typu <xref:System.Array> .</span><span class="sxs-lookup"><span data-stu-id="76c85-120">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="76c85-121">Vzhledem k tomu, že tento typ implementuje <xref:System.Collections.IEnumerable> a <xref:System.Collections.Generic.IEnumerable%601> , můžete použít iteraci [foreach](../../language-reference/keywords/foreach-in.md) pro všechna pole v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="76c85-121">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

## <a name="related-sections"></a><span data-ttu-id="76c85-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="76c85-122">Related sections</span></span>

- [<span data-ttu-id="76c85-123">Pole jako objekty</span><span class="sxs-lookup"><span data-stu-id="76c85-123">Arrays as Objects</span></span>](arrays-as-objects.md)
- [<span data-ttu-id="76c85-124">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="76c85-124">Using foreach with Arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="76c85-125">Předávání polí jako argumentů</span><span class="sxs-lookup"><span data-stu-id="76c85-125">Passing Arrays as Arguments</span></span>](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a><span data-ttu-id="76c85-126">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="76c85-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="76c85-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="76c85-127">See also</span></span>

- [<span data-ttu-id="76c85-128">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="76c85-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="76c85-129">Kolekce</span><span class="sxs-lookup"><span data-stu-id="76c85-129">Collections</span></span>](../concepts/collections.md)
