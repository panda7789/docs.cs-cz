---
title: Opožděné výpočty (F#)
description: 'Zjistěte, jak vylepšit výkon aplikace a knihovny F # opožděné výpočty.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 72dc5a14a845b52ae2512314d730516ca0cf4b9d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="lazy-computations"></a><span data-ttu-id="e2b82-103">Opožděné výpočty</span><span class="sxs-lookup"><span data-stu-id="e2b82-103">Lazy Computations</span></span>

<span data-ttu-id="e2b82-104">*Opožděné výpočty* jsou výpočty, které se nevyhodnotily okamžitě, ale místo toho vyhodnocují potřeby výsledek.</span><span class="sxs-lookup"><span data-stu-id="e2b82-104">*Lazy computations* are computations that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="e2b82-105">To vám může pomoct zlepšit výkon vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="e2b82-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="e2b82-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2b82-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="e2b82-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2b82-107">Remarks</span></span>

<span data-ttu-id="e2b82-108">V předchozích syntaxi *výraz* je kód, který se vyhodnotí jenom v případě, že v důsledku toho je nutné, a *identifikátor* je hodnota, která ukládá výsledek.</span><span class="sxs-lookup"><span data-stu-id="e2b82-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="e2b82-109">Hodnota je typu [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), kde skutečnou typu se používá pro `'T` se určí na základě výsledku výraz.</span><span class="sxs-lookup"><span data-stu-id="e2b82-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="e2b82-110">Opožděné výpočty umožňují vylepšit výkon, omezení provádění výpočtu pouze situací, ve kterých je potřeba výsledku.</span><span class="sxs-lookup"><span data-stu-id="e2b82-110">Lazy computations enable you to improve performance by restricting the execution of a computation to only those situations in which a result is needed.</span></span>

<span data-ttu-id="e2b82-111">Chcete-li vynutit výpočet provést, volejte metodu `Force`.</span><span class="sxs-lookup"><span data-stu-id="e2b82-111">To force the computation to be performed, you call the method `Force`.</span></span> <span data-ttu-id="e2b82-112">`Force` způsobí, že provádění provést pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="e2b82-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="e2b82-113">Následující volání `Force` vrátí stejné vést, ale nemůžou provést žádný kód.</span><span class="sxs-lookup"><span data-stu-id="e2b82-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="e2b82-114">Následující kód ukazuje použití opožděné výpočty a použití `Force`.</span><span class="sxs-lookup"><span data-stu-id="e2b82-114">The following code illustrates the use of lazy computation and the use of `Force`.</span></span> <span data-ttu-id="e2b82-115">V tomto kódu typ `result` je `Lazy<int>`a `Force` metoda vrátí `int`.</span><span class="sxs-lookup"><span data-stu-id="e2b82-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="e2b82-116">Opožděné vyhodnocení, ale ne `Lazy` typem, se taky používá pro pořadí.</span><span class="sxs-lookup"><span data-stu-id="e2b82-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="e2b82-117">Další informace najdete v tématu [pořadí](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="e2b82-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2b82-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2b82-118">See Also</span></span>

[<span data-ttu-id="e2b82-119">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="e2b82-119">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="e2b82-120">Lazyextensions – modul</span><span class="sxs-lookup"><span data-stu-id="e2b82-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
