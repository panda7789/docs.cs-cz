---
title: 'Smyčky: Výraz while...do'
description: Podívejte se, jak while... výraz do se používá k provedení iterativního spuštění (opakování), zatímco zadaná podmínka testu je pravdivá.
ms.date: 05/16/2016
ms.openlocfilehash: f05bdd9f8f4b9446d59f68e1231fb75e18e9b526
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630752"
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="1d4bf-103">Smyčky: Výraz while...do</span><span class="sxs-lookup"><span data-stu-id="1d4bf-103">Loops: while...do Expression</span></span>

<span data-ttu-id="1d4bf-104">`while...do` Výraz se používá k provedení iterativního spuštění (opakování), zatímco zadaná podmínka testu je pravdivá.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>

## <a name="syntax"></a><span data-ttu-id="1d4bf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d4bf-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="1d4bf-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d4bf-106">Remarks</span></span>

<span data-ttu-id="1d4bf-107">*Test-Expression* je vyhodnocen; Pokud je `true`, je proveden *výraz tělo* a testový výraz je znovu vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="1d4bf-108">*Výraz body* musí být typu `unit`.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="1d4bf-109">Pokud je `false`výraz testu, iterace skončí.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="1d4bf-110">Následující příklad ilustruje použití `while...do` výrazu.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="1d4bf-111">Výstupem předchozího kódu je datový proud náhodných čísel od 1 do 20, přičemž poslední z nich je 10.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> <span data-ttu-id="1d4bf-112">Můžete použít `while...do` ve výrazech pořadí a dalších výrazech výpočtu. v takovém případě se používá přizpůsobená verze `while...do` výrazu.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="1d4bf-113">Další informace najdete v tématu [sekvence](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md)a [výpočetní výrazy](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1d4bf-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d4bf-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d4bf-114">See also</span></span>

- [<span data-ttu-id="1d4bf-115">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="1d4bf-115">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="1d4bf-116">Smyčky `for...in`Vyjádření</span><span class="sxs-lookup"><span data-stu-id="1d4bf-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="1d4bf-117">Smyčky `for...to`Vyjádření</span><span class="sxs-lookup"><span data-stu-id="1d4bf-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
