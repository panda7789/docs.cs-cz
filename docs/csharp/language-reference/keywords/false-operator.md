---
title: false – – operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: e73113bd37dbb68590267141ad037f78919520bc
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43253246"
---
# <a name="false-operator-c-reference"></a><span data-ttu-id="bd133-102">false – – operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bd133-102">false operator (C# Reference)</span></span>

<span data-ttu-id="bd133-103">Vrátí [bool](bool.md) hodnotu `true` označuje, že operand `false` a vrátí `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="bd133-103">Returns the [bool](bool.md) value `true` to indicate that an operand is `false` and returns `false` otherwise.</span></span>

<span data-ttu-id="bd133-104">Před C# 2.0 `true` a `false` operátory byly použity k vytvoření typy s možnou hodnotou Null hodnotu definovanou uživatelem, které byly kompatibilní s typy, jako `SqlBool`.</span><span class="sxs-lookup"><span data-stu-id="bd133-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="bd133-105">Však jazyk teď poskytuje integrovanou podporu pro typy s možnou hodnotou Null, a kdykoli je to možné, abyste používali tyto místo přetížení `true` a `false` operátory.</span><span class="sxs-lookup"><span data-stu-id="bd133-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="bd133-106">Další informace najdete v tématu [typy připouštějící hodnotu Null](../../programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="bd133-106">For more information, see [Nullable Types](../../programming-guide/nullable-types/index.md).</span></span>

<span data-ttu-id="bd133-107">S s povolenou hodnotou Null, logické hodnoty výrazu `a != b` , nemusí být nutně roven `!(a == b)` protože jedna nebo obě hodnoty může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="bd133-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="bd133-108">Budete muset obě přetížení `true` a `false` operátorům samostatně správně zpracování hodnot null ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="bd133-108">You have to overload both the `true` and `false` operators separately to correctly handle the null values in the expression.</span></span> <span data-ttu-id="bd133-109">Následující příklad ukazuje, jak přetížení a použít `true` a `false` operátory.</span><span class="sxs-lookup"><span data-stu-id="bd133-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>

[!code-csharp[csrefKeywordsOperator#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#16)]

<span data-ttu-id="bd133-110">Typ, který přetížení `true` a `false` operátory lze používat pro řídicí výraz v [Pokud](if-else.md), [proveďte](do.md), [při](while.md), a [ pro](for.md) příkazy a [podmíněné výrazy](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="bd133-110">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](if-else.md), [do](do.md), [while](while.md), and [for](for.md) statements and in [conditional expressions](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="bd133-111">Pokud typ definuje operátor `false`, musíte také definovat operátor [true](true.md).</span><span class="sxs-lookup"><span data-stu-id="bd133-111">If a type defines operator `false`, it must also define operator [true](true.md).</span></span>

<span data-ttu-id="bd133-112">Typ nejde přetížit přímo podmíněné logické operátory [ && ](../operators/conditional-and-operator.md) a [ &#124; &#124; ](../operators/conditional-or-operator.md), ale stejného účinku lze dosáhnout přetížení regulární logické operátory operátory a operátory `true` a `false`.</span><span class="sxs-lookup"><span data-stu-id="bd133-112">A type cannot directly overload the conditional logical operators [&&](../operators/conditional-and-operator.md) and [&#124;&#124;](../operators/conditional-or-operator.md), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bd133-113">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bd133-113">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bd133-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd133-114">See also</span></span>

- [<span data-ttu-id="bd133-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bd133-115">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="bd133-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bd133-116">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="bd133-117">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bd133-117">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="bd133-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bd133-118">C# Operators</span></span>](../operators/index.md)  
- [<span data-ttu-id="bd133-119">true</span><span class="sxs-lookup"><span data-stu-id="bd133-119">true</span></span>](true.md)  