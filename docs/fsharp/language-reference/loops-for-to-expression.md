---
title: 'Smyčky: Výraz for...to (F#)'
description: Naleznete v tématu Jak F# for... výraz se používá k iteraci ve smyčce napříč celou škálou hodnoty proměnné smyčky.
ms.date: 05/16/2016
ms.openlocfilehash: 8160fd30c4f3afe8bb6b58f468802ef1c0ef32ee
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43800466"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="edd0e-103">Smyčky: Výraz for...to</span><span class="sxs-lookup"><span data-stu-id="edd0e-103">Loops: for...to Expression</span></span>

<span data-ttu-id="edd0e-104">`for...to` Výrazu se používá k iteraci ve smyčce napříč celou škálou hodnoty proměnné smyčky.</span><span class="sxs-lookup"><span data-stu-id="edd0e-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>

## <a name="syntax"></a><span data-ttu-id="edd0e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edd0e-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="edd0e-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="edd0e-106">Remarks</span></span>

<span data-ttu-id="edd0e-107">Typ identifikátoru je odvozen z typu *start* a *Dokončit* výrazy.</span><span class="sxs-lookup"><span data-stu-id="edd0e-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="edd0e-108">Typy pro tyto výrazy musí být 32bitová celá čísla.</span><span class="sxs-lookup"><span data-stu-id="edd0e-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="edd0e-109">I když technicky výraz `for...to` je více než tradiční výroky imperativní programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="edd0e-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="edd0e-110">Návratový typ *výraz těla* musí být `unit`.</span><span class="sxs-lookup"><span data-stu-id="edd0e-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="edd0e-111">Následující příklady znázorňují různé způsoby použití `for...to` výrazu.</span><span class="sxs-lookup"><span data-stu-id="edd0e-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="edd0e-112">Výstup předchozího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="edd0e-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="edd0e-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="edd0e-113">See also</span></span>

- [<span data-ttu-id="edd0e-114">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="edd0e-114">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="edd0e-115">Smyčky: `for...in` výraz</span><span class="sxs-lookup"><span data-stu-id="edd0e-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="edd0e-116">Smyčky: `while...do` výraz</span><span class="sxs-lookup"><span data-stu-id="edd0e-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
