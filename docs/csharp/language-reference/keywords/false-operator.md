---
title: false – – operátor (referenční dokumentace jazyka C#)
ms.date: 12/03/2018
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 4428d88acb08246623e2deb71a9daf7fb1cca692
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152302"
---
# <a name="false-operator-c-reference"></a><span data-ttu-id="84541-102">false – – operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="84541-102">false operator (C# Reference)</span></span>

<span data-ttu-id="84541-103">Vrátí [bool](bool.md) hodnotu `true` k označení, že operand je jednoznačně false.</span><span class="sxs-lookup"><span data-stu-id="84541-103">Returns the [bool](bool.md) value `true` to indicate that an operand is definitely false.</span></span> <span data-ttu-id="84541-104">Pokud typ definuje `false` operátoru, je třeba definovat [true – – operátor](true-operator.md).</span><span class="sxs-lookup"><span data-stu-id="84541-104">If a type defines the `false` operator, it must also define the [true operator](true-operator.md).</span></span> <span data-ttu-id="84541-105">`true` a `false` operátory zaručené vzájemně doplňují.</span><span class="sxs-lookup"><span data-stu-id="84541-105">The `true` and `false` operators are not guaranteed to complement each other.</span></span>

> [!TIP]
> <span data-ttu-id="84541-106">Použití `bool?` typu, pokud budete potřebovat pro podporu s hodnotou tři logiku, například při práci s databázemi, které podporují logický typ s hodnotou tři.</span><span class="sxs-lookup"><span data-stu-id="84541-106">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued logical type.</span></span> <span data-ttu-id="84541-107">Další informace najdete v tématu [bool? typ](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) část [použití typů s povolenou hodnotou Null](../../programming-guide/nullable-types/using-nullable-types.md) článku.</span><span class="sxs-lookup"><span data-stu-id="84541-107">For more information, see [The bool? type](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="84541-108">Pokud typ s definovanou `false` operátor [přetížení](operator.md) [logického operátoru AND](../operators/and-operator.md) `&` určitým způsobem, [podmíněné logického operátoru AND](../operators/conditional-and-operator.md) `&&`, což je short-circuiting, může být vyhodnocen pro operandy typu.</span><span class="sxs-lookup"><span data-stu-id="84541-108">If a type with the defined `false` operator [overloads](operator.md) the [logical AND operator](../operators/and-operator.md) `&` in a certain way, the [conditional logical AND operator](../operators/conditional-and-operator.md) `&&`, which is short-circuiting, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="84541-109">Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="84541-109">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

<span data-ttu-id="84541-110">Následující příklad představuje typ, který definuje obě `true` a `false` operátory.</span><span class="sxs-lookup"><span data-stu-id="84541-110">The following example presents the type that defines both `true` and `false` operators.</span></span> <span data-ttu-id="84541-111">Kromě toho přetížení logického operátoru AND `&` takovým způsobem, který operátor `&&` také může být vyhodnocen pro operandy typu.</span><span class="sxs-lookup"><span data-stu-id="84541-111">Moreover, it overloads the logical AND operator `&` in such a way that the operator `&&` also can be evaluated for the operands of that type.</span></span>

[!code-csharp-interactive[true and false operators example](~/samples/snippets/csharp/keywords/TrueFalseOperatorsExample.cs)]

<span data-ttu-id="84541-112">Všimněte si, že short-circuiting chování `&&` operátor.</span><span class="sxs-lookup"><span data-stu-id="84541-112">Notice the short-circuiting behavior of the `&&` operator.</span></span> <span data-ttu-id="84541-113">Když `GetFuelLaunchStatus` vrátí metoda `LaunchStatus.Red`, druhý operand `&&` operator nevyhodnocuje.</span><span class="sxs-lookup"><span data-stu-id="84541-113">When the `GetFuelLaunchStatus` method returns `LaunchStatus.Red`, the second operand of the `&&` operator is not evaluated.</span></span> <span data-ttu-id="84541-114">Důvodem je, že `LaunchStatus.Red` je jednoznačně false.</span><span class="sxs-lookup"><span data-stu-id="84541-114">That is because `LaunchStatus.Red` is definitely false.</span></span> <span data-ttu-id="84541-115">Potom výsledek logický operátor AND nezávisí na hodnotu druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="84541-115">Then the result of the logical AND doesn't depend on the value of the second operand.</span></span> <span data-ttu-id="84541-116">Výstup v příkladu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="84541-116">The output of the example is as follows:</span></span>

```console
Getting fuel launch status...
Wait!
```

<span data-ttu-id="84541-117">Všimněte si také, že podmíněný výraz [podmiňovací operátor `?:` ](../operators/conditional-operator.md) je `LaunchStatus` typu.</span><span class="sxs-lookup"><span data-stu-id="84541-117">Also notice that the conditional expression in the [conditional operator `?:`](../operators/conditional-operator.md) is of the `LaunchStatus` type.</span></span> <span data-ttu-id="84541-118">Je to možné, protože `LaunchStatus` definuje `true` operátor.</span><span class="sxs-lookup"><span data-stu-id="84541-118">That is possible, because `LaunchStatus` defines the `true` operator.</span></span> <span data-ttu-id="84541-119">Další informace najdete v tématu [logické výrazy](~/_csharplang/spec/expressions.md#boolean-expressions) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="84541-119">For more information, see the [Boolean expressions](~/_csharplang/spec/expressions.md#boolean-expressions) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84541-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84541-120">See also</span></span>

- [<span data-ttu-id="84541-121">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="84541-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="84541-122">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="84541-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="84541-123">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="84541-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="84541-124">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="84541-124">C# Operators</span></span>](../operators/index.md)
- [<span data-ttu-id="84541-125">`false` literál</span><span class="sxs-lookup"><span data-stu-id="84541-125">`false` literal</span></span>](false-literal.md)