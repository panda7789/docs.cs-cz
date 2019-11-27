---
title: 'Smyčky: Výraz for...to'
description: Podívejte se, F# jak pro... na výraz se používá k iterování ve smyčce přes rozsah hodnot proměnné smyčky.
ms.date: 05/16/2016
ms.openlocfilehash: 882b6e48dd09efcb57f7ef2f419e68a6c43393a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283905"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="feab2-103">Smyčky: Výraz for...to</span><span class="sxs-lookup"><span data-stu-id="feab2-103">Loops: for...to Expression</span></span>

<span data-ttu-id="feab2-104">Výraz `for...to` slouží k iterování ve smyčce přes rozsah hodnot proměnné smyčky.</span><span class="sxs-lookup"><span data-stu-id="feab2-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>

## <a name="syntax"></a><span data-ttu-id="feab2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="feab2-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="feab2-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="feab2-106">Remarks</span></span>

<span data-ttu-id="feab2-107">Typ identifikátoru je odvozen od typu výrazů *zahájení* a *dokončení* .</span><span class="sxs-lookup"><span data-stu-id="feab2-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="feab2-108">Typy pro tyto výrazy musí být 32 celých čísel.</span><span class="sxs-lookup"><span data-stu-id="feab2-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="feab2-109">I když technicky výraz, `for...to` je více podobně jako tradiční příkaz v imperativním programovacím jazyce.</span><span class="sxs-lookup"><span data-stu-id="feab2-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="feab2-110">Návratový typ pro *tělo-výrazu* musí být `unit`.</span><span class="sxs-lookup"><span data-stu-id="feab2-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="feab2-111">Následující příklady znázorňují různá použití výrazu `for...to`.</span><span class="sxs-lookup"><span data-stu-id="feab2-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="feab2-112">Výstup předchozího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="feab2-112">The output of the previous code is as follows.</span></span>

```console
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="feab2-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="feab2-113">See also</span></span>

- [<span data-ttu-id="feab2-114">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="feab2-114">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="feab2-115">Smyčky: výraz `for...in`</span><span class="sxs-lookup"><span data-stu-id="feab2-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="feab2-116">Smyčky: výraz `while...do`</span><span class="sxs-lookup"><span data-stu-id="feab2-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
