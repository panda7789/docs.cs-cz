---
title: Pole – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: e31cff94c51c626c4b8f0e08df270c45a9cc1316
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772101"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="59ac1-102">Pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="59ac1-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="59ac1-103">V datové struktuře pole můžete uložit více proměnných stejného typu.</span><span class="sxs-lookup"><span data-stu-id="59ac1-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="59ac1-104">Deklarujete pole zadáním typu jeho prvků.</span><span class="sxs-lookup"><span data-stu-id="59ac1-104">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="59ac1-105">Chcete-li, aby pole ukládalo prvky libovolného typu, můžete jako typ zadat `object`.</span><span class="sxs-lookup"><span data-stu-id="59ac1-105">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="59ac1-106">V rámci sjednoceného typu systému C#jsou všechny typy, předdefinované a uživatelsky definované typy odkazů a typy hodnot děděny přímo nebo nepřímo z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="59ac1-106">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="59ac1-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="59ac1-107">Example</span></span>

<span data-ttu-id="59ac1-108">Následující příklad vytvoří jednorozměrná, multidimenzionální a vícenásobná pole:</span><span class="sxs-lookup"><span data-stu-id="59ac1-108">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="59ac1-109">Přehled pole</span><span class="sxs-lookup"><span data-stu-id="59ac1-109">Array overview</span></span>

<span data-ttu-id="59ac1-110">Pole má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="59ac1-110">An array has the following properties:</span></span>

- <span data-ttu-id="59ac1-111">Pole [může být jednorozměrné](single-dimensional-arrays.md), [multidimenzionální](multidimensional-arrays.md) nebo [vícenásobné](jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="59ac1-111">An array can be [Single-Dimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) or [Jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="59ac1-112">Počet rozměrů a délka každé dimenze jsou vytvořeny při vytvoření instance pole.</span><span class="sxs-lookup"><span data-stu-id="59ac1-112">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="59ac1-113">Tyto hodnoty nejde během životnosti instance změnit.</span><span class="sxs-lookup"><span data-stu-id="59ac1-113">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="59ac1-114">Výchozí hodnoty prvků číselného pole jsou nastaveny na nulu a referenční prvky jsou nastaveny na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="59ac1-114">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="59ac1-115">Vícenásobné pole je pole polí, a proto jeho prvky jsou odkazové typy a jsou inicializovány na `null`.</span><span class="sxs-lookup"><span data-stu-id="59ac1-115">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="59ac1-116">Pole jsou indexována nulou: pole s `n` elementy je indexováno z `0` na `n-1`.</span><span class="sxs-lookup"><span data-stu-id="59ac1-116">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="59ac1-117">Prvky pole mohou být libovolného typu, včetně typu pole.</span><span class="sxs-lookup"><span data-stu-id="59ac1-117">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="59ac1-118">Typy polí jsou [odkazové typy](../../language-reference/keywords/reference-types.md) odvozené od abstraktního základního typu <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="59ac1-118">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="59ac1-119">Vzhledem k tomu, že tento typ implementuje <xref:System.Collections.IEnumerable> a <xref:System.Collections.Generic.IEnumerable%601>[](../../language-reference/keywords/foreach-in.md) , můžete použít iteraci ForEach C#pro všechna pole v.</span><span class="sxs-lookup"><span data-stu-id="59ac1-119">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

## <a name="related-sections"></a><span data-ttu-id="59ac1-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="59ac1-120">Related sections</span></span>

- [<span data-ttu-id="59ac1-121">Pole jako objekty</span><span class="sxs-lookup"><span data-stu-id="59ac1-121">Arrays as Objects</span></span>](arrays-as-objects.md)
- [<span data-ttu-id="59ac1-122">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="59ac1-122">Using foreach with Arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="59ac1-123">Předávání polí jako argumentů</span><span class="sxs-lookup"><span data-stu-id="59ac1-123">Passing Arrays as Arguments</span></span>](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a><span data-ttu-id="59ac1-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="59ac1-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="59ac1-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59ac1-125">See also</span></span>

- [<span data-ttu-id="59ac1-126">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="59ac1-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="59ac1-127">Kolekce</span><span class="sxs-lookup"><span data-stu-id="59ac1-127">Collections</span></span>](../concepts/collections.md)
