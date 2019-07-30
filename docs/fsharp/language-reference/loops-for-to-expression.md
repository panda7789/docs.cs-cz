---
title: 'Smyčky: Výraz for...to'
description: Podívejte se, F# jak pro... na výraz se používá k iterování ve smyčce přes rozsah hodnot proměnné smyčky.
ms.date: 05/16/2016
ms.openlocfilehash: 910c04aa4ea6b2c637dcad147347c1c317b5e0c0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626622"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="45986-103">Smyčky: Výraz for...to</span><span class="sxs-lookup"><span data-stu-id="45986-103">Loops: for...to Expression</span></span>

<span data-ttu-id="45986-104">`for...to` Výraz se používá k iterování smyčky v rámci rozsahu hodnot proměnné smyčky.</span><span class="sxs-lookup"><span data-stu-id="45986-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>

## <a name="syntax"></a><span data-ttu-id="45986-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45986-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="45986-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45986-106">Remarks</span></span>

<span data-ttu-id="45986-107">Typ identifikátoru je odvozen od typu výrazů *zahájení* a *dokončení* .</span><span class="sxs-lookup"><span data-stu-id="45986-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="45986-108">Typy pro tyto výrazy musí být 32 celých čísel.</span><span class="sxs-lookup"><span data-stu-id="45986-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="45986-109">I když je technicky výraz `for...to` , je více podobný jako tradiční příkaz v imperativním programovacím jazyce.</span><span class="sxs-lookup"><span data-stu-id="45986-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="45986-110">Návratový typ pro *výraz body* musí být `unit`.</span><span class="sxs-lookup"><span data-stu-id="45986-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="45986-111">Následující příklady znázorňují různá použití `for...to` výrazu.</span><span class="sxs-lookup"><span data-stu-id="45986-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="45986-112">Výstup předchozího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="45986-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="45986-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45986-113">See also</span></span>

- [<span data-ttu-id="45986-114">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="45986-114">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="45986-115">Smyčky `for...in`Vyjádření</span><span class="sxs-lookup"><span data-stu-id="45986-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="45986-116">Smyčky `while...do`Vyjádření</span><span class="sxs-lookup"><span data-stu-id="45986-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
