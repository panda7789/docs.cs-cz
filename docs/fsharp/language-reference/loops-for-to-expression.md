---
title: 'Smyčky: Výraz for...to (F#)'
description: 'V tématu Jak for. F #.. výrazu je použít k iteraci ve smyčce přes rozsah hodnot proměnné smyčky.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 95a8960d71c82c01118d2e71479fc0ec5298a02b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="loops-forto-expression"></a><span data-ttu-id="17959-103">Smyčky: Výraz for...to</span><span class="sxs-lookup"><span data-stu-id="17959-103">Loops: for...to Expression</span></span>

<span data-ttu-id="17959-104">`for...to` Výraz se používá k iterace ve smyčce v rozsahu hodnot proměnné smyčky.</span><span class="sxs-lookup"><span data-stu-id="17959-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>


## <a name="syntax"></a><span data-ttu-id="17959-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17959-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="17959-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17959-106">Remarks</span></span>
<span data-ttu-id="17959-107">Typ identifikátoru je odvozen z typu *spustit* a *Dokončit* výrazy.</span><span class="sxs-lookup"><span data-stu-id="17959-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="17959-108">Typy pro tyto výrazy musí být 32bitová celá čísla.</span><span class="sxs-lookup"><span data-stu-id="17959-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="17959-109">I když technicky výraz `for...to` je více než tradiční příkaz v imperativní programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="17959-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="17959-110">Návratový typ pro *textu výraz* musí být `unit`.</span><span class="sxs-lookup"><span data-stu-id="17959-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="17959-111">Následující příklady ukazují použití různých `for...to` výraz.</span><span class="sxs-lookup"><span data-stu-id="17959-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="17959-112">Výstup předchozího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="17959-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="17959-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="17959-113">See Also</span></span>
[<span data-ttu-id="17959-114">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="17959-114">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="17959-115">Smyčky: `for...in` výraz</span><span class="sxs-lookup"><span data-stu-id="17959-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="17959-116">Smyčky: `while...do` výraz</span><span class="sxs-lookup"><span data-stu-id="17959-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
