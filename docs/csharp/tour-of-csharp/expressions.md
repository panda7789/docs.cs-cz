---
title: Výrazy jazyka C# – prohlídka jazyka C#
description: Výrazy, operandy a operátory jsou stavebními kameny jazyka C#
ms.date: 02/27/2020
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 209b5da01cd7539f2bd97023f40fd149910b6f1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159153"
---
# <a name="expressions"></a><span data-ttu-id="426cf-103">Výrazy</span><span class="sxs-lookup"><span data-stu-id="426cf-103">Expressions</span></span>

<span data-ttu-id="426cf-104">*Výrazy* jsou vytvořeny z *operandů* a *operátorů*.</span><span class="sxs-lookup"><span data-stu-id="426cf-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="426cf-105">Operátory výrazu označují, které operace se mají u operandů použít.</span><span class="sxs-lookup"><span data-stu-id="426cf-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="426cf-106">`+`Příklady operátorů: `-` `*`, `/`, `new`, a .</span><span class="sxs-lookup"><span data-stu-id="426cf-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="426cf-107">Příklady operandů zahrnují literály, pole, místní proměnné a výrazy.</span><span class="sxs-lookup"><span data-stu-id="426cf-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="426cf-108">Pokud výraz obsahuje více operátorů, *priorita* operátorů řídí pořadí, ve kterém jsou vyhodnocovány jednotlivé operátory.</span><span class="sxs-lookup"><span data-stu-id="426cf-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="426cf-109">Výraz `x + y * z` je například vyhodnocen jako `x + (y * z)` proto, že `*` operátor má vyšší prioritu `+` než operátor.</span><span class="sxs-lookup"><span data-stu-id="426cf-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="426cf-110">Pokud dojde k operandu mezi dvěma operátory se stejnou prioritou, *asociativity* operátorů řídí pořadí, ve kterém jsou operace prováděny:</span><span class="sxs-lookup"><span data-stu-id="426cf-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

* <span data-ttu-id="426cf-111">S výjimkou operátorů přiřazení a null-coalescing jsou všechny binární operátory *levostranné*, což znamená, že operace jsou prováděny zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="426cf-111">Except for the assignment and null-coalescing operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="426cf-112">Například `x + y + z` je vyhodnocen jako `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="426cf-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
* <span data-ttu-id="426cf-113">Operátory přiřazení, `??` null-coalescing `??=` a operátory `?:` a podmíněný operátor jsou *pravostranné*, což znamená, že operace jsou prováděny zprava doleva.</span><span class="sxs-lookup"><span data-stu-id="426cf-113">The assignment operators, the null-coalescing `??` and `??=` operators, and the conditional operator `?:` are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="426cf-114">Například `x = y = z` je vyhodnocen jako `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="426cf-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="426cf-115">Prioritu a asociativitu lze ovládat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="426cf-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="426cf-116">`x + y * z` Například nejprve `y` vynásobí `z` a `x`potom `(x + y) * z` přidá `x` `y` výsledek do , ale `z`nejprve přidá a potom vynásobí výsledek .</span><span class="sxs-lookup"><span data-stu-id="426cf-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="426cf-117">Většina operátorů může být [*přetížena*](../language-reference/operators/operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="426cf-117">Most operators can be [*overloaded*](../language-reference/operators/operator-overloading.md).</span></span> <span data-ttu-id="426cf-118">Přetížení operátoru umožňuje uživatelem definované implementace operátorů, které mají být určeny pro operace, kde jeden nebo oba operandy jsou uživatelem definované třídy nebo struktury typu.</span><span class="sxs-lookup"><span data-stu-id="426cf-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="426cf-119">C# poskytuje počet operátorů k provádění [aritmetické](../language-reference/operators/arithmetic-operators.md), [logické](../language-reference/operators/boolean-logical-operators.md), [bitové a shift](../language-reference/operators/bitwise-and-shift-operators.md) operace a rovnost [i](../language-reference/operators/equality-operators.md) [pořadí](../language-reference/operators/comparison-operators.md) porovnání.</span><span class="sxs-lookup"><span data-stu-id="426cf-119">C# provides a number of operators to perform [arithmetic](../language-reference/operators/arithmetic-operators.md), [logical](../language-reference/operators/boolean-logical-operators.md), [bitwise and shift](../language-reference/operators/bitwise-and-shift-operators.md) operations and [equality](../language-reference/operators/equality-operators.md) and [order](../language-reference/operators/comparison-operators.md) comparisons.</span></span>

<span data-ttu-id="426cf-120">Úplný seznam operátorů jazyka C# seřazené podle úrovně priority naleznete v [tématu Operátory jazyka C#](../language-reference/operators/index.md).</span><span class="sxs-lookup"><span data-stu-id="426cf-120">For the complete list of C# operators ordered by precedence level, see [C# operators](../language-reference/operators/index.md).</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="426cf-121">[Předchozí](types-and-variables.md)
> [další](statements.md)</span><span class="sxs-lookup"><span data-stu-id="426cf-121">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
