---
title: false – – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: f2001d92e99476131d6f03e13f0bc12104f638b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218255"
---
# <a name="false-operator-c-reference"></a><span data-ttu-id="e9f58-102">false – – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e9f58-102">false Operator (C# Reference)</span></span>
<span data-ttu-id="e9f58-103">Vrátí [bool](../../../csharp/language-reference/keywords/bool.md) hodnotu `true` označuje, že operand `false` a vrátí `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="e9f58-103">Returns the [bool](../../../csharp/language-reference/keywords/bool.md) value `true` to indicate that an operand is `false` and returns `false` otherwise.</span></span>  
  
 <span data-ttu-id="e9f58-104">Před C# 2.0 `true` a `false` operátory jste použili k vytvoření typů s povolenou hodnotou Null hodnotu definovanou uživatelem, které byly kompatibilní s typy, jako `SqlBool`.</span><span class="sxs-lookup"><span data-stu-id="e9f58-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="e9f58-105">Ale jazyk teď poskytuje integrovanou podporu pro typy hodnot s povolenou hodnotou Null, a kdykoli je to možné postupujte podle těchto místo přetížení `true` a `false` operátory.</span><span class="sxs-lookup"><span data-stu-id="e9f58-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="e9f58-106">Další informace najdete v tématu [typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9f58-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="e9f58-107">S s možnou hodnotou Null logické hodnoty, výraz `a != b` není nutně roven `!(a == b)` vzhledem k tomu, že jedna nebo obě hodnoty může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="e9f58-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="e9f58-108">Budete muset přetížení i `true` a `false` operátorům samostatně správně zpracování hodnot null ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="e9f58-108">You have to overload both the `true` and `false` operators separately to correctly handle the null values in the expression.</span></span> <span data-ttu-id="e9f58-109">Následující příklad ukazuje, jak přetížení a používat `true` a `false` operátory.</span><span class="sxs-lookup"><span data-stu-id="e9f58-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]  
  
 <span data-ttu-id="e9f58-110">Typ, který přetížení `true` a `false` operátory lze použít pro řízení výrazu v [Pokud](../../../csharp/language-reference/keywords/if-else.md), [provést](../../../csharp/language-reference/keywords/do.md), [při](../../../csharp/language-reference/keywords/while.md), a [ pro](../../../csharp/language-reference/keywords/for.md) příkazy a v [podmíněné výrazy](../../../csharp/language-reference/operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e9f58-110">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md), and [for](../../../csharp/language-reference/keywords/for.md) statements and in [conditional expressions](../../../csharp/language-reference/operators/conditional-operator.md).</span></span>  
  
 <span data-ttu-id="e9f58-111">Pokud typ definuje operátor `false`, musí definovat také operátor [true](../../../csharp/language-reference/keywords/true.md).</span><span class="sxs-lookup"><span data-stu-id="e9f58-111">If a type defines operator `false`, it must also define operator [true](../../../csharp/language-reference/keywords/true.md).</span></span>  
  
 <span data-ttu-id="e9f58-112">Typ nelze přímo přetížení podmíněného logické operátory [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) a [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md), ale lze dosáhnout ekvivalentní vliv přetížení regulární logické operátory operátory a `true` a `false`.</span><span class="sxs-lookup"><span data-stu-id="e9f58-112">A type cannot directly overload the conditional logical operators [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e9f58-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e9f58-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e9f58-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9f58-114">See Also</span></span>  
 [<span data-ttu-id="e9f58-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e9f58-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e9f58-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e9f58-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e9f58-117">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e9f58-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e9f58-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e9f58-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="e9f58-119">true</span><span class="sxs-lookup"><span data-stu-id="e9f58-119">true</span></span>](../../../csharp/language-reference/keywords/true.md)
