---
title: Vložené funkce
description: Naučte se používat F# vložené funkce, které jsou integrovány přímo do kódu volajícího.
ms.date: 05/16/2016
ms.openlocfilehash: 2830d1ada5b3005c3fcae975a44e85a7c84554f7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630675"
---
# <a name="inline-functions"></a><span data-ttu-id="37602-103">Vložené funkce</span><span class="sxs-lookup"><span data-stu-id="37602-103">Inline Functions</span></span>

<span data-ttu-id="37602-104">*Vložené funkce* jsou funkce, které jsou integrovány přímo do kódu volajícího.</span><span class="sxs-lookup"><span data-stu-id="37602-104">*Inline functions* are functions that are integrated directly into the calling code.</span></span>

## <a name="using-inline-functions"></a><span data-ttu-id="37602-105">Používání vložených funkcí</span><span class="sxs-lookup"><span data-stu-id="37602-105">Using Inline Functions</span></span>

<span data-ttu-id="37602-106">Při použití parametrů statického typu musí být všechny funkce, které jsou parametrizované parametry typu, vloženy.</span><span class="sxs-lookup"><span data-stu-id="37602-106">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="37602-107">To zaručuje, že kompilátor dokáže tyto parametry typu vyřešit.</span><span class="sxs-lookup"><span data-stu-id="37602-107">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="37602-108">Pokud používáte běžné parametry obecného typu, neexistuje takové omezení.</span><span class="sxs-lookup"><span data-stu-id="37602-108">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="37602-109">Kromě povolení použití omezení členů mohou být vložené funkce užitečné v rámci optimalizace kódu.</span><span class="sxs-lookup"><span data-stu-id="37602-109">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="37602-110">Nicméně nadměrné využití vložených funkcí může způsobit, že váš kód bude méně odolný vůči změnám v optimalizacích kompilátoru a implementaci funkcí knihovny.</span><span class="sxs-lookup"><span data-stu-id="37602-110">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="37602-111">Z tohoto důvodu byste se měli vyhnout použití vložených funkcí pro optimalizaci, pokud jste nezkoušeli všechny ostatní techniky optimalizace.</span><span class="sxs-lookup"><span data-stu-id="37602-111">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="37602-112">Vytvoření vložené funkce nebo metody může někdy zlepšit výkon, ale to není vždy v případě případu.</span><span class="sxs-lookup"><span data-stu-id="37602-112">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="37602-113">Proto byste měli použít také měření výkonu k ověření, že je fakt, že by jakákoli z vložených funkcí měla pozitivní účinek.</span><span class="sxs-lookup"><span data-stu-id="37602-113">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="37602-114">`inline` Modifikátor lze použít na funkce na nejvyšší úrovni, na úrovni modulu nebo na úrovni metody ve třídě.</span><span class="sxs-lookup"><span data-stu-id="37602-114">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="37602-115">Následující příklad kódu ukazuje vloženou funkci na nejvyšší úrovni, vloženou metodu instance a vloženou statickou metodu.</span><span class="sxs-lookup"><span data-stu-id="37602-115">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="37602-116">Vložené funkce a odvození typu</span><span class="sxs-lookup"><span data-stu-id="37602-116">Inline Functions and Type Inference</span></span>

<span data-ttu-id="37602-117">Přítomnost `inline` má vliv na odvození typu.</span><span class="sxs-lookup"><span data-stu-id="37602-117">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="37602-118">Je to proto, že vložené funkce mohou mít staticky vyřešené parametry typu, zatímco nevložená funkce nemůže.</span><span class="sxs-lookup"><span data-stu-id="37602-118">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="37602-119">Následující příklad kódu ukazuje případ, kde `inline` je užitečné, protože používáte funkci, která má staticky vyřešený parametr typu `float` , operátor převodu.</span><span class="sxs-lookup"><span data-stu-id="37602-119">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="37602-120">Bez modifikátoru vynutí odvození typu funkci, aby v tomto případě `int`vybrala konkrétní typ. `inline`</span><span class="sxs-lookup"><span data-stu-id="37602-120">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="37602-121">Ale s `inline` modifikátorem, je funkce také odvozena pro statický vyřešený parametr typu.</span><span class="sxs-lookup"><span data-stu-id="37602-121">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="37602-122">`inline` Pomocí modifikátoru je typ odvozen jako následující:</span><span class="sxs-lookup"><span data-stu-id="37602-122">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="37602-123">To znamená, že funkce přijímá libovolný typ, který podporuje převod na typ **float**.</span><span class="sxs-lookup"><span data-stu-id="37602-123">This means that the function accepts any type that supports a conversion to **float**.</span></span>

## <a name="see-also"></a><span data-ttu-id="37602-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37602-124">See also</span></span>

- [<span data-ttu-id="37602-125">Funkce</span><span class="sxs-lookup"><span data-stu-id="37602-125">Functions</span></span>](index.md)
- [<span data-ttu-id="37602-126">Omezení</span><span class="sxs-lookup"><span data-stu-id="37602-126">Constraints</span></span>](../generics/constraints.md)
- [<span data-ttu-id="37602-127">Statisticky vyřešené parametry typu</span><span class="sxs-lookup"><span data-stu-id="37602-127">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
