---
title: Pole (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 1469336bf034fd22c9d7355b2f8dd8be32721fdf
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510635"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="842f2-102">Pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="842f2-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="842f2-103">Ve struktuře dat pole lze uložit více proměnných stejného typu.</span><span class="sxs-lookup"><span data-stu-id="842f2-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="842f2-104">Deklarujete pole zadáním typu jeho elementů.</span><span class="sxs-lookup"><span data-stu-id="842f2-104">You declare an array by specifying the type of its elements.</span></span>  
  
 `type[] arrayName;`  
  
 <span data-ttu-id="842f2-105">Následující příklady vytváří jedno/dvoudimenzionální a vícenásobná pole:</span><span class="sxs-lookup"><span data-stu-id="842f2-105">The following examples create single-dimensional, multidimensional, and jagged arrays:</span></span>  
  
 [!code-csharp[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
## <a name="array-overview"></a><span data-ttu-id="842f2-106">Pole – přehled</span><span class="sxs-lookup"><span data-stu-id="842f2-106">Array Overview</span></span>

 <span data-ttu-id="842f2-107">Pole má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="842f2-107">An array has the following properties:</span></span>  
  
-   <span data-ttu-id="842f2-108">Pole může být [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [multidimenzionální](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) nebo [vícenásobné](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="842f2-108">An array can be [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) or [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span></span>  
  
-   <span data-ttu-id="842f2-109">Počet rozměrů a délka každé dimenze jsou vytvořeny při vytvoření instance pole.</span><span class="sxs-lookup"><span data-stu-id="842f2-109">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="842f2-110">Tyto hodnoty nelze změnit během životnosti instance.</span><span class="sxs-lookup"><span data-stu-id="842f2-110">These values can't be changed during the lifetime of the instance.</span></span>  
  
-   <span data-ttu-id="842f2-111">Výchozí hodnoty prvků číselného pole jsou nastaveny na nulu a prvky odkazu jsou nastaveny na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="842f2-111">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>  
  
-   <span data-ttu-id="842f2-112">Vícenásobné pole je pole polí, a proto jeho prvky jsou odkazové typy a jsou inicializovány na hodnotu `null`.</span><span class="sxs-lookup"><span data-stu-id="842f2-112">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
-   <span data-ttu-id="842f2-113">Pole jsou indexována nula: pole s `n` prvky je indexováno od `0` k `n-1`.</span><span class="sxs-lookup"><span data-stu-id="842f2-113">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>  
  
-   <span data-ttu-id="842f2-114">Prvky pole mohou být libovolného typu, včetně typu pole.</span><span class="sxs-lookup"><span data-stu-id="842f2-114">Array elements can be of any type, including an array type.</span></span>  
  
-   <span data-ttu-id="842f2-115">Typy pole jsou [referenční typy](../../../csharp/language-reference/keywords/reference-types.md) odvozené z abstraktního základního typu <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="842f2-115">Array types are [reference types](../../../csharp/language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="842f2-116">Protože tento typ implementuje <xref:System.Collections.IEnumerable> a <xref:System.Collections.Generic.IEnumerable%601>, můžete použít [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iterace pro všechna pole v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="842f2-116">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="842f2-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="842f2-117">Related Sections</span></span>  
  
-   [<span data-ttu-id="842f2-118">Pole jako objekty</span><span class="sxs-lookup"><span data-stu-id="842f2-118">Arrays as Objects</span></span>](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [<span data-ttu-id="842f2-119">Použití příkazu foreach s poli</span><span class="sxs-lookup"><span data-stu-id="842f2-119">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [<span data-ttu-id="842f2-120">Předávání polí jako argumentů</span><span class="sxs-lookup"><span data-stu-id="842f2-120">Passing Arrays as Arguments</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [<span data-ttu-id="842f2-121">Předávání polí pomocí parametrů ref a out</span><span class="sxs-lookup"><span data-stu-id="842f2-121">Passing Arrays Using ref and out</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
  
## <a name="c-language-specification"></a><span data-ttu-id="842f2-122">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="842f2-122">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="842f2-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="842f2-123">See Also</span></span>

- [<span data-ttu-id="842f2-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="842f2-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="842f2-125">Kolekce</span><span class="sxs-lookup"><span data-stu-id="842f2-125">Collections</span></span>](https://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
- [<span data-ttu-id="842f2-126">Array – typ kolekce</span><span class="sxs-lookup"><span data-stu-id="842f2-126">Array Collection Type</span></span>](https://msdn.microsoft.com/library/8a9964de-8941-47b1-a3cf-a01bc88db9e8)
