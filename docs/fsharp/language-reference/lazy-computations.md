---
title: "Opožděné výpočty (F#)"
description: "Zjistěte, jak vylepšit výkon aplikace a knihovny F # opožděné výpočty."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3499293e-1d53-4b02-b764-f687fbdaa7fe
ms.openlocfilehash: 984c96ab68a8919e2382eefe8260b07f191027dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="lazy-computations"></a><span data-ttu-id="1d442-104">Opožděné výpočty</span><span class="sxs-lookup"><span data-stu-id="1d442-104">Lazy Computations</span></span>

<span data-ttu-id="1d442-105">*Opožděné výpočty* jsou výpočty, které se nevyhodnotily okamžitě, ale místo toho vyhodnocují potřeby výsledek.</span><span class="sxs-lookup"><span data-stu-id="1d442-105">*Lazy computations* are computations that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="1d442-106">To vám může pomoct zlepšit výkon vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="1d442-106">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="1d442-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d442-107">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="1d442-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d442-108">Remarks</span></span>

<span data-ttu-id="1d442-109">V předchozích syntaxi *výraz* je kód, který se vyhodnotí jenom v případě, že v důsledku toho je nutné, a *identifikátor* je hodnota, která ukládá výsledek.</span><span class="sxs-lookup"><span data-stu-id="1d442-109">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="1d442-110">Hodnota je typu [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), kde skutečnou typu se používá pro `'T` se určí na základě výsledku výraz.</span><span class="sxs-lookup"><span data-stu-id="1d442-110">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="1d442-111">Opožděné výpočty umožňují vylepšit výkon, omezení provádění výpočtu pouze situací, ve kterých je potřeba výsledku.</span><span class="sxs-lookup"><span data-stu-id="1d442-111">Lazy computations enable you to improve performance by restricting the execution of a computation to only those situations in which a result is needed.</span></span>

<span data-ttu-id="1d442-112">Chcete-li vynutit výpočet provést, volejte metodu `Force`.</span><span class="sxs-lookup"><span data-stu-id="1d442-112">To force the computation to be performed, you call the method `Force`.</span></span> <span data-ttu-id="1d442-113">`Force`způsobí, že provádění provést pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="1d442-113">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="1d442-114">Následující volání `Force` vrátí stejné vést, ale nemůžou provést žádný kód.</span><span class="sxs-lookup"><span data-stu-id="1d442-114">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="1d442-115">Následující kód ukazuje použití opožděné výpočty a použití `Force`.</span><span class="sxs-lookup"><span data-stu-id="1d442-115">The following code illustrates the use of lazy computation and the use of `Force`.</span></span> <span data-ttu-id="1d442-116">V tomto kódu typ `result` je `Lazy<int>`a `Force` metoda vrátí `int`.</span><span class="sxs-lookup"><span data-stu-id="1d442-116">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="1d442-117">Opožděné vyhodnocení, ale ne `Lazy` typem, se taky používá pro pořadí.</span><span class="sxs-lookup"><span data-stu-id="1d442-117">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="1d442-118">Další informace najdete v tématu [pořadí](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="1d442-118">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d442-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d442-119">See Also</span></span>

[<span data-ttu-id="1d442-120">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="1d442-120">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="1d442-121">Lazyextensions – modul</span><span class="sxs-lookup"><span data-stu-id="1d442-121">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
