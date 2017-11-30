---
title: "Smyčky: Výraz for...to (F#)"
description: "V tématu Jak for. F #.. výrazu je použít k iteraci ve smyčce přes rozsah hodnot proměnné smyčky."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e14c38d9-b1ef-4b7f-be9a-fb6ef6708e02
ms.openlocfilehash: 1a1d71d30b5e87e4691a78acd5032de9419399db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="loops-forto-expression"></a><span data-ttu-id="a0634-104">Smyčky: Výraz for...to</span><span class="sxs-lookup"><span data-stu-id="a0634-104">Loops: for...to Expression</span></span>

<span data-ttu-id="a0634-105">`for...to` Výraz se používá k iterace ve smyčce v rozsahu hodnot proměnné smyčky.</span><span class="sxs-lookup"><span data-stu-id="a0634-105">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>


## <a name="syntax"></a><span data-ttu-id="a0634-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0634-106">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="a0634-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0634-107">Remarks</span></span>
<span data-ttu-id="a0634-108">Typ identifikátoru je odvozen z typu *spustit* a *Dokončit* výrazy.</span><span class="sxs-lookup"><span data-stu-id="a0634-108">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="a0634-109">Typy pro tyto výrazy musí být 32bitová celá čísla.</span><span class="sxs-lookup"><span data-stu-id="a0634-109">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="a0634-110">I když technicky výraz `for...to` je více než tradiční příkaz v imperativní programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="a0634-110">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="a0634-111">Návratový typ pro *textu výraz* musí být `unit`.</span><span class="sxs-lookup"><span data-stu-id="a0634-111">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="a0634-112">Následující příklady ukazují použití různých `for...to` výraz.</span><span class="sxs-lookup"><span data-stu-id="a0634-112">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="a0634-113">Výstup předchozího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="a0634-113">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="a0634-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0634-114">See Also</span></span>
[<span data-ttu-id="a0634-115">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="a0634-115">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="a0634-116">Smyčky: `for...in` výraz</span><span class="sxs-lookup"><span data-stu-id="a0634-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="a0634-117">Smyčky: `while...do` výraz</span><span class="sxs-lookup"><span data-stu-id="a0634-117">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
