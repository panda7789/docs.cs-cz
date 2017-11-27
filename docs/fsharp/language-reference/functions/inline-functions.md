---
title: "Vložené funkce (F#)"
description: "Další informace o použití F # vložené funkce, které jsou integrovány přímo volající kód."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3fa31178-08f8-463d-9d41-d29220a90027
ms.openlocfilehash: 8293a73e9468d3bc3eb51cd99860e52c48121ae3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="inline-functions"></a><span data-ttu-id="ff9d7-104">Vložené funkce</span><span class="sxs-lookup"><span data-stu-id="ff9d7-104">Inline Functions</span></span>

<span data-ttu-id="ff9d7-105">*Vložené funkce* jsou funkce, které jsou integrovány přímo volající kód.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-105">*Inline functions* are functions that are integrated directly into the calling code.</span></span>


## <a name="using-inline-functions"></a><span data-ttu-id="ff9d7-106">Pomocí vložené funkce</span><span class="sxs-lookup"><span data-stu-id="ff9d7-106">Using Inline Functions</span></span>
<span data-ttu-id="ff9d7-107">Použijete-li parametry statické typu, musí být všechny funkce, které jsou parametry podle parametrů typu vložené.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-107">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="ff9d7-108">Zaručí se tím, která kompilátor může vyřešit tyto parametry typu.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-108">This guarantees that that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="ff9d7-109">Při použití parametrů obyčejnou obecného typu neexistuje žádné takových omezení.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-109">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="ff9d7-110">Než povolíte využití člen omezení, může být užitečné v optimalizace kódu vložené funkce.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-110">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="ff9d7-111">Nadměrné vložené funkce však může způsobit kódu méně odolné na změny v kompilátoru optimalizace a provádění – funkce knihovny.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-111">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="ff9d7-112">Z tohoto důvodu byste neměli používat vložené funkce optimalizace, pokud Pokusili jste se všechny ostatní techniky optimalizace.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-112">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="ff9d7-113">Provedení vnořené funkce nebo metoda může někdy zlepšit výkon, ale není, vždy.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-113">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="ff9d7-114">Proto byste měli použít také měření výkonu k ověření, že provedení jakékoli dané funkce vložené ve skutečnosti mít kladný vliv.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-114">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="ff9d7-115">`inline` Modifikátor lze použít pro funkce na nejvyšší úrovni, na úrovni modulu nebo na úrovni metody ve třídě.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-115">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="ff9d7-116">Následující příklad kódu ukazuje vložená funkce na nejvyšší úrovni, metodu instance vloženého a statickou metodu vložené.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-116">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="ff9d7-117">Vložené funkce a odvození typu</span><span class="sxs-lookup"><span data-stu-id="ff9d7-117">Inline Functions and Type Inference</span></span>
<span data-ttu-id="ff9d7-118">Přítomnost `inline` ovlivňuje odvození typu.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-118">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="ff9d7-119">To je proto vložené funkce mohou být statisticky vyřešené parametry typu, zatímco jiné vložené funkce nelze.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-119">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="ff9d7-120">Následující příklad kódu ukazuje případu kde `inline` je užitečné, protože používáte funkci, která má parametr typu určené statisticky `float` operátor převodu.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-120">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="ff9d7-121">Bez `inline` modifikátor, vynutí odvození typu funkce se má provést konkrétního typu, v takovém případě `int`.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-121">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="ff9d7-122">Ale `inline` modifikátor, funkce je také odvodit tak, aby měl parametr typu určené statisticky.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-122">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="ff9d7-123">Pomocí `inline` modifikátor, typ je odvodit být následující:</span><span class="sxs-lookup"><span data-stu-id="ff9d7-123">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="ff9d7-124">To znamená, že funkce přijímá žádný typ, který podporuje převod na **float**.</span><span class="sxs-lookup"><span data-stu-id="ff9d7-124">This means that the function accepts any type that supports a conversion to **float**.</span></span>


## <a name="see-also"></a><span data-ttu-id="ff9d7-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff9d7-125">See Also</span></span>
[<span data-ttu-id="ff9d7-126">Funkce</span><span class="sxs-lookup"><span data-stu-id="ff9d7-126">Functions</span></span>](index.md)

[<span data-ttu-id="ff9d7-127">Omezení</span><span class="sxs-lookup"><span data-stu-id="ff9d7-127">Constraints</span></span>](../generics/constraints.md)

[<span data-ttu-id="ff9d7-128">Statisticky vyřešené parametry typu</span><span class="sxs-lookup"><span data-stu-id="ff9d7-128">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
