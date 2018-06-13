---
title: Opožděné výpočty (F#)
description: 'Zjistěte, jak vylepšit výkon aplikace a knihovny F # opožděné výpočty.'
ms.date: 05/16/2016
ms.openlocfilehash: 1c4eb6ab247c44a04a9d145185e2de7ec01b8e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563929"
---
# <a name="lazy-computations"></a><span data-ttu-id="76510-103">Opožděné výpočty</span><span class="sxs-lookup"><span data-stu-id="76510-103">Lazy Computations</span></span>

<span data-ttu-id="76510-104">*Opožděné výpočty* jsou výpočty, které se nevyhodnotily okamžitě, ale místo toho vyhodnocují potřeby výsledek.</span><span class="sxs-lookup"><span data-stu-id="76510-104">*Lazy computations* are computations that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="76510-105">To vám může pomoct zlepšit výkon vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="76510-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="76510-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76510-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="76510-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76510-107">Remarks</span></span>

<span data-ttu-id="76510-108">V předchozích syntaxi *výraz* je kód, který se vyhodnotí jenom v případě, že v důsledku toho je nutné, a *identifikátor* je hodnota, která ukládá výsledek.</span><span class="sxs-lookup"><span data-stu-id="76510-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="76510-109">Hodnota je typu [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), kde skutečnou typu se používá pro `'T` se určí na základě výsledku výraz.</span><span class="sxs-lookup"><span data-stu-id="76510-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="76510-110">Opožděné výpočty umožňují vylepšit výkon, omezení provádění výpočtu pouze situací, ve kterých je potřeba výsledku.</span><span class="sxs-lookup"><span data-stu-id="76510-110">Lazy computations enable you to improve performance by restricting the execution of a computation to only those situations in which a result is needed.</span></span>

<span data-ttu-id="76510-111">Chcete-li vynutit výpočet provést, volejte metodu `Force`.</span><span class="sxs-lookup"><span data-stu-id="76510-111">To force the computation to be performed, you call the method `Force`.</span></span> <span data-ttu-id="76510-112">`Force` způsobí, že provádění provést pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="76510-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="76510-113">Následující volání `Force` vrátí stejné vést, ale nemůžou provést žádný kód.</span><span class="sxs-lookup"><span data-stu-id="76510-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="76510-114">Následující kód ukazuje použití opožděné výpočty a použití `Force`.</span><span class="sxs-lookup"><span data-stu-id="76510-114">The following code illustrates the use of lazy computation and the use of `Force`.</span></span> <span data-ttu-id="76510-115">V tomto kódu typ `result` je `Lazy<int>`a `Force` metoda vrátí `int`.</span><span class="sxs-lookup"><span data-stu-id="76510-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="76510-116">Opožděné vyhodnocení, ale ne `Lazy` typem, se taky používá pro pořadí.</span><span class="sxs-lookup"><span data-stu-id="76510-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="76510-117">Další informace najdete v tématu [pořadí](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="76510-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="76510-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="76510-118">See Also</span></span>

[<span data-ttu-id="76510-119">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="76510-119">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="76510-120">Lazyextensions – modul</span><span class="sxs-lookup"><span data-stu-id="76510-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
