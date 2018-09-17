---
title: Vložené funkce (F#)
description: 'Další informace o použití F # vložené funkce, které jsou integrované přímo do kódu volajícího.'
ms.date: 05/16/2016
ms.openlocfilehash: 47fca0fe34630792aeb0908b0cee02a927e2567d
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45745942"
---
# <a name="inline-functions"></a><span data-ttu-id="7a26c-103">Vložené funkce</span><span class="sxs-lookup"><span data-stu-id="7a26c-103">Inline Functions</span></span>

<span data-ttu-id="7a26c-104">*Vložené funkce* jsou funkce, které jsou integrované přímo do kódu volajícího.</span><span class="sxs-lookup"><span data-stu-id="7a26c-104">*Inline functions* are functions that are integrated directly into the calling code.</span></span>

## <a name="using-inline-functions"></a><span data-ttu-id="7a26c-105">Použití vložených funkcí</span><span class="sxs-lookup"><span data-stu-id="7a26c-105">Using Inline Functions</span></span>

<span data-ttu-id="7a26c-106">Při použití parametrů statického typu musí být všechny funkce, které jsou parametrizovány parametry typu inline.</span><span class="sxs-lookup"><span data-stu-id="7a26c-106">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="7a26c-107">Zaručí se tak, že kompilátor může rozpoznat tyto parametry typu.</span><span class="sxs-lookup"><span data-stu-id="7a26c-107">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="7a26c-108">Při použití parametrů obecného typu obyčejné neexistuje žádné takové omezení.</span><span class="sxs-lookup"><span data-stu-id="7a26c-108">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="7a26c-109">Než povoluje použití členská omezení, může být užitečné při optimalizaci kódu vložených funkcí.</span><span class="sxs-lookup"><span data-stu-id="7a26c-109">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="7a26c-110">Nadměrné využití vložených funkcí však může způsobit menší odolné vůči změny v optimalizace kompilátoru a implementaci funkce knihovny kódu.</span><span class="sxs-lookup"><span data-stu-id="7a26c-110">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="7a26c-111">Z tohoto důvodu byste neměli používat vložené funkce optimalizace, pokud jste vyzkoušeli všechny jiné techniky optimalizace.</span><span class="sxs-lookup"><span data-stu-id="7a26c-111">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="7a26c-112">Provádění vložené funkce nebo metoda může někdy zlepšit výkon, ale není to vždy.</span><span class="sxs-lookup"><span data-stu-id="7a26c-112">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="7a26c-113">Měření výkonu proto měli také používat k ověření pozitivní účinek nemá ve skutečnosti provádění jakékoli vložené dané funkce.</span><span class="sxs-lookup"><span data-stu-id="7a26c-113">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="7a26c-114">`inline` Modifikátor lze použít u funkcí na nejvyšší úrovni, na úrovni modulu nebo na úrovni metody ve třídě.</span><span class="sxs-lookup"><span data-stu-id="7a26c-114">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="7a26c-115">Následující příklad kódu ukazuje vloženou funkcí na nejvyšší úrovni, vložená metoda instance a vložená metoda statická.</span><span class="sxs-lookup"><span data-stu-id="7a26c-115">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="7a26c-116">Vložené funkce a odvození typu</span><span class="sxs-lookup"><span data-stu-id="7a26c-116">Inline Functions and Type Inference</span></span>

<span data-ttu-id="7a26c-117">Přítomnost `inline` odvození typu ovlivňuje.</span><span class="sxs-lookup"><span data-stu-id="7a26c-117">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="7a26c-118">Je to proto vložených funkcí lze staticky řešené parametry typu, že nelze jiných než vložených funkcí.</span><span class="sxs-lookup"><span data-stu-id="7a26c-118">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="7a26c-119">Následující příklad kódu ukazuje případ kde `inline` je užitečné, protože používáte funkci, která má parametr staticky řešeného typu `float` operátoru převodu.</span><span class="sxs-lookup"><span data-stu-id="7a26c-119">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="7a26c-120">Bez `inline` modifikátor, vynutí odvození typu funkce v tomto případě se konkrétní typ `int`.</span><span class="sxs-lookup"><span data-stu-id="7a26c-120">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="7a26c-121">Ale `inline` modifikátor funkce je také odvozen, aby měl parametr staticky řešeného typu.</span><span class="sxs-lookup"><span data-stu-id="7a26c-121">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="7a26c-122">S `inline` modifikátor, typ je odvozen bude následující:</span><span class="sxs-lookup"><span data-stu-id="7a26c-122">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="7a26c-123">To znamená, že funkce přijímá libovolný typ, který podporuje převod na **float**.</span><span class="sxs-lookup"><span data-stu-id="7a26c-123">This means that the function accepts any type that supports a conversion to **float**.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a26c-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a26c-124">See also</span></span>

- [<span data-ttu-id="7a26c-125">Funkce</span><span class="sxs-lookup"><span data-stu-id="7a26c-125">Functions</span></span>](index.md)
- [<span data-ttu-id="7a26c-126">Omezení</span><span class="sxs-lookup"><span data-stu-id="7a26c-126">Constraints</span></span>](../generics/constraints.md)
- [<span data-ttu-id="7a26c-127">Statisticky vyřešené parametry typu</span><span class="sxs-lookup"><span data-stu-id="7a26c-127">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
