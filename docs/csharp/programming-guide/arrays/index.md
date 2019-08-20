---
title: Pole – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 24c6d54c3fe92ada661e732adec582e87ab62417
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597528"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="5e5c4-102">Pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5e5c4-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="5e5c4-103">V datové struktuře pole můžete uložit více proměnných stejného typu.</span><span class="sxs-lookup"><span data-stu-id="5e5c4-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="5e5c4-104">Deklarujete pole zadáním typu jeho prvků.</span><span class="sxs-lookup"><span data-stu-id="5e5c4-104">You declare an array by specifying the type of its elements.</span></span>  
  
 `type[] arrayName;`  
  
 <span data-ttu-id="5e5c4-105">Následující příklad vytvoří jednorozměrná, multidimenzionální a vícenásobná pole:</span><span class="sxs-lookup"><span data-stu-id="5e5c4-105">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>  
  
 [!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]  
  
## <a name="array-overview"></a><span data-ttu-id="5e5c4-106">Přehled pole</span><span class="sxs-lookup"><span data-stu-id="5e5c4-106">Array Overview</span></span>

 <span data-ttu-id="5e5c4-107">Pole má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="5e5c4-107">An array has the following properties:</span></span>  
  
- <span data-ttu-id="5e5c4-108">Pole může být jednorozměrné [](./single-dimensional-arrays.md), [multidimenzionální](./multidimensional-arrays.md) nebo vícenásobné. [](./jagged-arrays.md)</span><span class="sxs-lookup"><span data-stu-id="5e5c4-108">An array can be [Single-Dimensional](./single-dimensional-arrays.md), [Multidimensional](./multidimensional-arrays.md) or [Jagged](./jagged-arrays.md).</span></span>  
  
- <span data-ttu-id="5e5c4-109">Počet rozměrů a délka každé dimenze jsou vytvořeny při vytvoření instance pole.</span><span class="sxs-lookup"><span data-stu-id="5e5c4-109">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="5e5c4-110">Tyto hodnoty nejde během životnosti instance změnit.</span><span class="sxs-lookup"><span data-stu-id="5e5c4-110">These values can't be changed during the lifetime of the instance.</span></span>  
  
- <span data-ttu-id="5e5c4-111">Výchozí hodnoty prvků číselného pole jsou nastaveny na nulu a referenční prvky jsou nastaveny na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="5e5c4-111">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>  
  
- <span data-ttu-id="5e5c4-112">Vícenásobné pole je pole pole, a proto jeho prvky jsou odkazové typy a jsou inicializovány na `null`.</span><span class="sxs-lookup"><span data-stu-id="5e5c4-112">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
- <span data-ttu-id="5e5c4-113">Pole jsou indexována nulou: pole s `n` elementy je indexováno `0` z `n-1`do.</span><span class="sxs-lookup"><span data-stu-id="5e5c4-113">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>  
  
- <span data-ttu-id="5e5c4-114">Prvky pole mohou být libovolného typu, včetně typu pole.</span><span class="sxs-lookup"><span data-stu-id="5e5c4-114">Array elements can be of any type, including an array type.</span></span>  
  
- <span data-ttu-id="5e5c4-115">Typy polí jsou [odkazové typy](../../language-reference/keywords/reference-types.md) odvozené od abstraktního základního <xref:System.Array>typu.</span><span class="sxs-lookup"><span data-stu-id="5e5c4-115">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="5e5c4-116">Vzhledem k tomu, <xref:System.Collections.IEnumerable> že <xref:System.Collections.Generic.IEnumerable%601>tento typ implementuje a [](../../language-reference/keywords/foreach-in.md) , můžete použít iteraci ForEach C#pro všechna pole v.</span><span class="sxs-lookup"><span data-stu-id="5e5c4-116">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5e5c4-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="5e5c4-117">Related Sections</span></span>  
  
- [<span data-ttu-id="5e5c4-118">Pole jako objekty</span><span class="sxs-lookup"><span data-stu-id="5e5c4-118">Arrays as Objects</span></span>](./arrays-as-objects.md)  
  
- [<span data-ttu-id="5e5c4-119">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="5e5c4-119">Using foreach with Arrays</span></span>](./using-foreach-with-arrays.md)  
  
- [<span data-ttu-id="5e5c4-120">Předávání polí jako argumentů</span><span class="sxs-lookup"><span data-stu-id="5e5c4-120">Passing Arrays as Arguments</span></span>](./passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="5e5c4-121">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5e5c4-121">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5e5c4-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e5c4-122">See also</span></span>

- [<span data-ttu-id="5e5c4-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5e5c4-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5e5c4-124">Kolekce</span><span class="sxs-lookup"><span data-stu-id="5e5c4-124">Collections</span></span>](../concepts/collections.md)
