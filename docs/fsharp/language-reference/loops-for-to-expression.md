---
title: 'Smyčky: Výraz for...to'
description: V tématu Jak F# for... výraz se používá k iteraci ve smyčce napříč celou škálou hodnoty proměnné smyčky.
ms.date: 05/16/2016
ms.openlocfilehash: 041e98fa4bcc140aa3cd699f6ed35bf52c8b4175
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612319"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="f33cb-103">Smyčky: Výraz for...to</span><span class="sxs-lookup"><span data-stu-id="f33cb-103">Loops: for...to Expression</span></span>

<span data-ttu-id="f33cb-104">`for...to` Výrazu se používá k iteraci ve smyčce napříč celou škálou hodnoty proměnné smyčky.</span><span class="sxs-lookup"><span data-stu-id="f33cb-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>

## <a name="syntax"></a><span data-ttu-id="f33cb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f33cb-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="f33cb-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f33cb-106">Remarks</span></span>

<span data-ttu-id="f33cb-107">Typ identifikátoru je odvozen z typu *start* a *Dokončit* výrazy.</span><span class="sxs-lookup"><span data-stu-id="f33cb-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="f33cb-108">Typy pro tyto výrazy musí být 32bitová celá čísla.</span><span class="sxs-lookup"><span data-stu-id="f33cb-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="f33cb-109">I když technicky výraz `for...to` je více než tradiční výroky imperativní programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="f33cb-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="f33cb-110">Návratový typ *výraz těla* musí být `unit`.</span><span class="sxs-lookup"><span data-stu-id="f33cb-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="f33cb-111">Následující příklady znázorňují různé způsoby použití `for...to` výrazu.</span><span class="sxs-lookup"><span data-stu-id="f33cb-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="f33cb-112">Výstup předchozího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="f33cb-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="f33cb-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f33cb-113">See also</span></span>

- [<span data-ttu-id="f33cb-114">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="f33cb-114">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="f33cb-115">Smyčky: `for...in` Výraz</span><span class="sxs-lookup"><span data-stu-id="f33cb-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="f33cb-116">Smyčky: `while...do` Výraz</span><span class="sxs-lookup"><span data-stu-id="f33cb-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)