---
title: operátory true a false - C# odkaz
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 7cbfca932b5f9f8a6f658e84204da5005da5ffb8
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609842"
---
# <a name="true-and-false-operators-c-reference"></a><span data-ttu-id="03fa6-102">operátory true a false (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="03fa6-102">true and false operators (C# reference)</span></span>

<span data-ttu-id="03fa6-103">`true` Operátor vrátí [bool](../keywords/bool.md) hodnotu `true` označuje jednoznačně true operand.</span><span class="sxs-lookup"><span data-stu-id="03fa6-103">The `true` operator returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span> <span data-ttu-id="03fa6-104">`false` Operátor vrátí `bool` hodnotu `true` k označení, že operand je jednoznačně false.</span><span class="sxs-lookup"><span data-stu-id="03fa6-104">The `false` operator returns the `bool` value `true` to indicate that an operand is definitely false.</span></span> <span data-ttu-id="03fa6-105">`true` a `false` operátory zaručené vzájemně doplňují.</span><span class="sxs-lookup"><span data-stu-id="03fa6-105">The `true` and `false` operators are not guaranteed to complement each other.</span></span> <span data-ttu-id="03fa6-106">To znamená i `true` a `false` operátor může vrátit `bool` hodnotu `false` pro stejný operand.</span><span class="sxs-lookup"><span data-stu-id="03fa6-106">That is, both the `true` and `false` operator might return the `bool` value `false` for the same operand.</span></span> <span data-ttu-id="03fa6-107">Pokud typ definuje jeden dva operátory, musíte také definovat další operátor.</span><span class="sxs-lookup"><span data-stu-id="03fa6-107">If a type defines one of the two operators, it must also define another operator.</span></span>

> [!TIP]
> <span data-ttu-id="03fa6-108">Použití `bool?` typu, pokud budete potřebovat pro podporu s hodnotou tři logiku, například při práci s databázemi, které podporují tři vracející typ Boolean.</span><span class="sxs-lookup"><span data-stu-id="03fa6-108">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="03fa6-109">C#poskytuje `&` a `|` operátory, které podporují tři vracející logiky pomocí `bool?` operandy.</span><span class="sxs-lookup"><span data-stu-id="03fa6-109">C# provides the `&` and `|` operators that support the three-valued logic with the `bool?` operands.</span></span> <span data-ttu-id="03fa6-110">Další informace najdete v tématu [logické operátory s povolenou hodnotou Null logická](boolean-logical-operators.md#nullable-boolean-logical-operators) část [logické logické operátory](boolean-logical-operators.md) článku.</span><span class="sxs-lookup"><span data-stu-id="03fa6-110">For more information, see the [Nullable Boolean logical operators](boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](boolean-logical-operators.md) article.</span></span>

## <a name="boolean-expressions"></a><span data-ttu-id="03fa6-111">logické výrazy</span><span class="sxs-lookup"><span data-stu-id="03fa6-111">Boolean expressions</span></span>

<span data-ttu-id="03fa6-112">Typ s definovanou `true` operátor může být typ výsledku řízení podmíněného výrazu v [Pokud](../keywords/if-else.md), [proveďte](../keywords/do.md), [při](../keywords/while.md), a [ pro](../keywords/for.md) příkazy a [podmiňovací operátor `?:` ](conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="03fa6-112">A type with the defined `true` operator can be the type of a result of a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](conditional-operator.md).</span></span> <span data-ttu-id="03fa6-113">Další informace najdete v tématu [logické výrazy](~/_csharplang/spec/expressions.md#boolean-expressions) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="03fa6-113">For more information, see the [Boolean expressions](~/_csharplang/spec/expressions.md#boolean-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="user-defined-conditional-logical-operators"></a><span data-ttu-id="03fa6-114">Podmíněné logické operátory definované uživatelem</span><span class="sxs-lookup"><span data-stu-id="03fa6-114">User-defined conditional logical operators</span></span>

<span data-ttu-id="03fa6-115">Pokud typ s definovanou `true` a `false` operátory [přetížení](operator-overloading.md) [logického operátoru OR](boolean-logical-operators.md#logical-or-operator-) `|` nebo [logického operátoru AND](boolean-logical-operators.md#logical-and-operator-) `&` určitým způsobem, [podmíněné logického operátoru OR](boolean-logical-operators.md#conditional-logical-or-operator-) `||` nebo [podmíněné logického operátoru AND](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, může být vyhodnocen pro operandy typu.</span><span class="sxs-lookup"><span data-stu-id="03fa6-115">If a type with the defined `true` and `false` operators [overloads](operator-overloading.md) the [logical OR operator](boolean-logical-operators.md#logical-or-operator-) `|` or the [logical AND operator](boolean-logical-operators.md#logical-and-operator-) `&` in a certain way, the [conditional logical OR operator](boolean-logical-operators.md#conditional-logical-or-operator-) `||` or [conditional logical AND operator](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="03fa6-116">Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="03fa6-116">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="example"></a><span data-ttu-id="03fa6-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="03fa6-117">Example</span></span>

<span data-ttu-id="03fa6-118">Následující příklad představuje typ, který definuje obě `true` a `false` operátory.</span><span class="sxs-lookup"><span data-stu-id="03fa6-118">The following example presents the type that defines both `true` and `false` operators.</span></span> <span data-ttu-id="03fa6-119">Typ také přetížení logického operátoru AND `&` takovým způsobem, který operátor `&&` také může být vyhodnocen pro operandy typu.</span><span class="sxs-lookup"><span data-stu-id="03fa6-119">The type also overloads the logical AND operator `&` in such a way that the operator `&&` also can be evaluated for the operands of that type.</span></span>

[!code-csharp[true and false operators example](~/samples/csharp/language-reference/operators/TrueFalseOperators.cs)]

<span data-ttu-id="03fa6-120">Všimněte si, že short-circuiting chování `&&` operátor.</span><span class="sxs-lookup"><span data-stu-id="03fa6-120">Notice the short-circuiting behavior of the `&&` operator.</span></span> <span data-ttu-id="03fa6-121">Když `GetFuelLaunchStatus` vrátí metoda `LaunchStatus.Red`, zpracovával pravý operand z `&&` operator nevyhodnocuje.</span><span class="sxs-lookup"><span data-stu-id="03fa6-121">When the `GetFuelLaunchStatus` method returns `LaunchStatus.Red`, the right-hand operand of the `&&` operator is not evaluated.</span></span> <span data-ttu-id="03fa6-122">Důvodem je, že `LaunchStatus.Red` je jednoznačně false.</span><span class="sxs-lookup"><span data-stu-id="03fa6-122">That is because `LaunchStatus.Red` is definitely false.</span></span> <span data-ttu-id="03fa6-123">Potom výsledek logický operátor AND nezávisí na hodnotu operandu pravé.</span><span class="sxs-lookup"><span data-stu-id="03fa6-123">Then the result of the logical AND doesn't depend on the value of the right-hand operand.</span></span> <span data-ttu-id="03fa6-124">Výstup v příkladu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="03fa6-124">The output of the example is as follows:</span></span>

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a><span data-ttu-id="03fa6-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03fa6-125">See also</span></span>

- [<span data-ttu-id="03fa6-126">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="03fa6-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="03fa6-127">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="03fa6-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="03fa6-128">true – literál</span><span class="sxs-lookup"><span data-stu-id="03fa6-128">true literal</span></span>](../keywords/true-literal.md)
- [<span data-ttu-id="03fa6-129">false – literál</span><span class="sxs-lookup"><span data-stu-id="03fa6-129">false literal</span></span>](../keywords/false-literal.md)
