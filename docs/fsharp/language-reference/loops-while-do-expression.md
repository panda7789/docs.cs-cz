---
title: 'Smyčky: Výraz while...do'
description: Naleznete v tématu jak při... proveďte použit výraz provádět iterativní spuštění (opakování), zatímco je zadaný testovací podmínka pravdivá.
ms.date: 05/16/2016
ms.openlocfilehash: d2a77e0bfefe3b6b026012e6b2938ba670326bcf
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613008"
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="ee478-103">Smyčky: Výraz while...do</span><span class="sxs-lookup"><span data-stu-id="ee478-103">Loops: while...do Expression</span></span>

<span data-ttu-id="ee478-104">`while...do` Použit výraz provádět iterativní spuštění (opakování), zatímco je zadaný testovací podmínka pravdivá.</span><span class="sxs-lookup"><span data-stu-id="ee478-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>

## <a name="syntax"></a><span data-ttu-id="ee478-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee478-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="ee478-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee478-106">Remarks</span></span>

<span data-ttu-id="ee478-107">*Výrazu testu* je vyhodnocen; Pokud je `true`, *výraz těla* provádí a testovací výraz je vyhodnocen znovu.</span><span class="sxs-lookup"><span data-stu-id="ee478-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="ee478-108">*Výraz těla* musí mít typ `unit`.</span><span class="sxs-lookup"><span data-stu-id="ee478-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="ee478-109">Pokud je test výraz `false`, konce iterace.</span><span class="sxs-lookup"><span data-stu-id="ee478-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="ee478-110">Následující příklad ukazuje použití `while...do` výrazu.</span><span class="sxs-lookup"><span data-stu-id="ee478-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="ee478-111">Výstup předchozího kódu je datový proud náhodných čísel od 1 do 20, poslední z nich je 10.</span><span class="sxs-lookup"><span data-stu-id="ee478-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> <span data-ttu-id="ee478-112">Můžete použít `while...do` ve výrazech pořadí a jiných výrazech výpočtu se v takovém případě přizpůsobenou verzi `while...do` výraz je použit.</span><span class="sxs-lookup"><span data-stu-id="ee478-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="ee478-113">Další informace najdete v tématu [pořadí](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [výrazech výpočtu](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ee478-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ee478-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee478-114">See also</span></span>

- [<span data-ttu-id="ee478-115">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="ee478-115">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="ee478-116">Smyčky: `for...in` Výraz</span><span class="sxs-lookup"><span data-stu-id="ee478-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="ee478-117">Smyčky: `for...to` Výraz</span><span class="sxs-lookup"><span data-stu-id="ee478-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)