---
title: True – – operátor (C# odkaz)
ms.date: 12/03/2018
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
ms.openlocfilehash: 17830e5ae842255dcf71e73097779d17520b81e6
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130673"
---
# <a name="true-operator-c-reference"></a><span data-ttu-id="622f1-102">True – – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="622f1-102">true operator (C# Reference)</span></span>

<span data-ttu-id="622f1-103">Vrátí [bool](bool.md) hodnotu `true` označuje jednoznačně true operand.</span><span class="sxs-lookup"><span data-stu-id="622f1-103">Returns the [bool](bool.md) value `true` to indicate that an operand is definitely true.</span></span> <span data-ttu-id="622f1-104">Pokud typ definuje `true` operátoru, je třeba definovat [false – – operátor](false-operator.md).</span><span class="sxs-lookup"><span data-stu-id="622f1-104">If a type defines the `true` operator, it must also define the [false operator](false-operator.md).</span></span> <span data-ttu-id="622f1-105">`true` a `false` operátory zaručené vzájemně doplňují.</span><span class="sxs-lookup"><span data-stu-id="622f1-105">The `true` and `false` operators are not guaranteed to complement each other.</span></span>

<span data-ttu-id="622f1-106">Pro příklad, který definuje obě `true` a `false` operátory, najdete v článku [false – – operátor](false-operator.md) článku.</span><span class="sxs-lookup"><span data-stu-id="622f1-106">For the example that defines both `true` and `false` operators, see the [false operator](false-operator.md) article.</span></span>

> [!TIP]
> <span data-ttu-id="622f1-107">Použití `bool?` typu, pokud budete potřebovat pro podporu s hodnotou tři logiku, například při práci s databázemi, které podporují logický typ s hodnotou tři.</span><span class="sxs-lookup"><span data-stu-id="622f1-107">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued logical type.</span></span> <span data-ttu-id="622f1-108">Další informace najdete v tématu [bool? typ](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) část [použití typů s povolenou hodnotou Null](../../programming-guide/nullable-types/using-nullable-types.md) článku.</span><span class="sxs-lookup"><span data-stu-id="622f1-108">For more information, see [The bool? type](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="622f1-109">Pokud typ s definovanou `true` operátor [přetížení](operator.md) [logický operátor OR](../operators/or-operator.md) `|` určitým způsobem, [podmíněné logický operátor OR](../operators/conditional-or-operator.md) `||`, což je short-circuiting, může být vyhodnocen pro operandy typu.</span><span class="sxs-lookup"><span data-stu-id="622f1-109">If a type with the defined `true` operator [overloads](operator.md) the [logical OR operator](../operators/or-operator.md) `|` in a certain way, the [conditional logical OR operator](../operators/conditional-or-operator.md) `||`, which is short-circuiting, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="622f1-110">Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="622f1-110">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

<span data-ttu-id="622f1-111">Typ s definovanou `true` operátor může být typ výsledku řízení podmíněného výrazu v [Pokud](if-else.md), [proveďte](do.md), [při](while.md), a [ pro](for.md) příkazy a [podmiňovací operátor `?:` ](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="622f1-111">A type with the defined `true` operator can be the type of a result of a controlling conditional expression in the [if](if-else.md), [do](do.md), [while](while.md), and [for](for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span> <span data-ttu-id="622f1-112">Další informace najdete v tématu [logické výrazy](~/_csharplang/spec/expressions.md#boolean-expressions) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="622f1-112">For more information, see the [Boolean expressions](~/_csharplang/spec/expressions.md#boolean-expressions) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="622f1-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="622f1-113">See also</span></span>

- [<span data-ttu-id="622f1-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="622f1-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="622f1-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="622f1-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="622f1-116">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="622f1-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="622f1-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="622f1-117">C# Operators</span></span>](../operators/index.md)
- [<span data-ttu-id="622f1-118">`true` literál</span><span class="sxs-lookup"><span data-stu-id="622f1-118">`true` literal</span></span>](true-literal.md)