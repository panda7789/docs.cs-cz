---
title: Výrazy Lazy
description: Přečtěte F# si, jak opožděné výrazy můžou zlepšit výkon vašich aplikací a knihoven.
ms.date: 03/13/2019
ms.openlocfilehash: 97429e9a4c3838cbaa2ead197db4443e0820e8b3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630750"
---
# <a name="lazy-expressions"></a><span data-ttu-id="acb34-103">Výrazy Lazy</span><span class="sxs-lookup"><span data-stu-id="acb34-103">Lazy Expressions</span></span>

<span data-ttu-id="acb34-104">*Opožděné výrazy* jsou výrazy, které nejsou vyhodnocovány okamžitě, ale jsou vyhodnoceny, když je výsledek požadován.</span><span class="sxs-lookup"><span data-stu-id="acb34-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="acb34-105">To může pomoci zvýšit výkon kódu.</span><span class="sxs-lookup"><span data-stu-id="acb34-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="acb34-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acb34-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="acb34-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="acb34-107">Remarks</span></span>

<span data-ttu-id="acb34-108">V předchozí syntaxi je *výraz* kódem, který je vyhodnocován pouze v případě, že je požadován výsledek, a *identifikátor* je hodnota, která ukládá výsledek.</span><span class="sxs-lookup"><span data-stu-id="acb34-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="acb34-109">Hodnota je typu [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), kde skutečný typ, který je použit pro `'T` , je určen z výsledku výrazu.</span><span class="sxs-lookup"><span data-stu-id="acb34-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="acb34-110">Opožděné výrazy umožňují zvýšit výkon omezením spouštění výrazů pouze na případy, kdy je zapotřebí výsledek.</span><span class="sxs-lookup"><span data-stu-id="acb34-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="acb34-111">Chcete-li vynutit, aby byly výrazy provedeny, zavolejte `Force`metodu.</span><span class="sxs-lookup"><span data-stu-id="acb34-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="acb34-112">`Force`způsobí, že se provádění provede jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="acb34-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="acb34-113">Následná volání `Force` vrátí stejný výsledek, ale nespustí žádný kód.</span><span class="sxs-lookup"><span data-stu-id="acb34-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="acb34-114">Následující kód ilustruje použití opožděných výrazů a použití `Force`.</span><span class="sxs-lookup"><span data-stu-id="acb34-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="acb34-115">V tomto kódu `result` typ je `Lazy<int>` `Force`ametoda vrátí. `int`</span><span class="sxs-lookup"><span data-stu-id="acb34-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="acb34-116">Opožděné vyhodnocení, ale ne `Lazy` typ, se používá také pro sekvence.</span><span class="sxs-lookup"><span data-stu-id="acb34-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="acb34-117">Další informace najdete v tématu [sekvence](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="acb34-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="acb34-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acb34-118">See also</span></span>

- [<span data-ttu-id="acb34-119">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="acb34-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="acb34-120">Modul LazyExtensions</span><span class="sxs-lookup"><span data-stu-id="acb34-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
