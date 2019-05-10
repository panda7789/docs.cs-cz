---
title: C#Výrazy – připravuje C# jazyka
description: výrazy, operandy a operátory jsou stavební bloky C# jazyka
ms.date: 04/25/2019
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: ffe800304a9125e11e20d96a84919936f1fee2c1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753644"
---
# <a name="expressions"></a><span data-ttu-id="82d2c-103">Výrazy</span><span class="sxs-lookup"><span data-stu-id="82d2c-103">Expressions</span></span>

<span data-ttu-id="82d2c-104">*Výrazy* se vytvářejí na základě *operandy* a *operátory*.</span><span class="sxs-lookup"><span data-stu-id="82d2c-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="82d2c-105">Operátory výrazu označují operace, které chcete použít pro operandy.</span><span class="sxs-lookup"><span data-stu-id="82d2c-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="82d2c-106">Příklady operátorů `+`, `-`, `*`, `/`, a `new`.</span><span class="sxs-lookup"><span data-stu-id="82d2c-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="82d2c-107">Příklady operandy: literály, pole, místní proměnné a výrazy.</span><span class="sxs-lookup"><span data-stu-id="82d2c-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="82d2c-108">Pokud výraz obsahuje více operátorů *prioritu* operátorů určuje pořadí, ve kterém jsou jednotlivé operátory vyhodnocovány.</span><span class="sxs-lookup"><span data-stu-id="82d2c-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="82d2c-109">Například výraz `x + y * z` se vyhodnotí jako `x + (y * z)` protože `*` má vyšší prioritu než operátor `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="82d2c-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="82d2c-110">Dojde-li operand mezi dva operátory se stejnou prioritou, *asociativita* operátorů určuje pořadí, ve kterém jsou operace prováděny:</span><span class="sxs-lookup"><span data-stu-id="82d2c-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

* <span data-ttu-id="82d2c-111">S výjimkou operátory přiřazení jsou všechny binární operátory *asociativní zleva*, což znamená, že operace se provádějí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="82d2c-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="82d2c-112">Například `x + y + z` se vyhodnotí jako `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="82d2c-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
* <span data-ttu-id="82d2c-113">Operátory přiřazení a podmiňovací operátor (`?:`) jsou *asociativní zprava*, což znamená, že operace se provádějí zprava doleva.</span><span class="sxs-lookup"><span data-stu-id="82d2c-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="82d2c-114">Například `x = y = z` se vyhodnotí jako `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="82d2c-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="82d2c-115">Přednost a asociativita operátorů lze ovládat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="82d2c-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="82d2c-116">Například `x + y * z` nejprve vynásobí `y` podle `z` a pak přidá výsledek, který má `x`, ale `(x + y) * z` nejprve přidá `x` a `y` a pak vynásobí výsledků `z`.</span><span class="sxs-lookup"><span data-stu-id="82d2c-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="82d2c-117">Většina operátory mohou být [ *přetížené*](../language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="82d2c-117">Most operators can be [*overloaded*](../language-reference/keywords/operator.md).</span></span> <span data-ttu-id="82d2c-118">Přetížení operátoru umožňuje uživatelem definovaný operátor implementace pro operace, kde jeden nebo oba operandy jsou třídy nebo struktury typu uživatelem definované.</span><span class="sxs-lookup"><span data-stu-id="82d2c-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="82d2c-119">C#poskytuje několik operátorů sloužící k provedení [aritmetické](../language-reference/operators/arithmetic-operators.md), [logické](../language-reference/operators/boolean-logical-operators.md), [bitové a shift](../language-reference/operators/bitwise-and-shift-operators.md) operací a [rovnosti](../language-reference/operators/equality-operators.md) a [pořadí](../language-reference/operators/comparison-operators.md) porovnání.</span><span class="sxs-lookup"><span data-stu-id="82d2c-119">C# provides a number of operators to perform [arithmetic](../language-reference/operators/arithmetic-operators.md), [logical](../language-reference/operators/boolean-logical-operators.md), [bitwise and shift](../language-reference/operators/bitwise-and-shift-operators.md) operations and [equality](../language-reference/operators/equality-operators.md) and [order](../language-reference/operators/comparison-operators.md) comparisons.</span></span>

<span data-ttu-id="82d2c-120">Pro úplný seznam C# operátory seřazené podle úrovně priority, naleznete v tématu [ C# operátory](../language-reference/operators/index.md).</span><span class="sxs-lookup"><span data-stu-id="82d2c-120">For the complete list of C# operators ordered by precedence level, see [C# operators](../language-reference/operators/index.md).</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="82d2c-121">[Předchozí](types-and-variables.md)
> [další](statements.md)</span><span class="sxs-lookup"><span data-stu-id="82d2c-121">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
