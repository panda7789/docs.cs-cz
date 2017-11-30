---
title: "false – – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f9761fb49e2c7f6e4a7615e64cec9fed88318c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="false-operator-c-reference"></a><span data-ttu-id="c96a9-102">false – – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c96a9-102">false Operator (C# Reference)</span></span>
<span data-ttu-id="c96a9-103">Vrátí [bool](../../../csharp/language-reference/keywords/bool.md) hodnotu `true` označuje, že operand `false` a vrátí `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="c96a9-103">Returns the [bool](../../../csharp/language-reference/keywords/bool.md) value `true` to indicate that an operand is `false` and returns `false` otherwise.</span></span>  
  
 <span data-ttu-id="c96a9-104">Před C# 2.0 `true` a `false` operátory jste použili k vytvoření typů s povolenou hodnotou Null hodnotu definovanou uživatelem, které byly kompatibilní s typy, jako `SqlBool`.</span><span class="sxs-lookup"><span data-stu-id="c96a9-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="c96a9-105">Ale jazyk teď poskytuje integrovanou podporu pro typy hodnot s povolenou hodnotou Null, a kdykoli je to možné postupujte podle těchto místo přetížení `true` a `false` operátory.</span><span class="sxs-lookup"><span data-stu-id="c96a9-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="c96a9-106">Další informace najdete v tématu [typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="c96a9-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="c96a9-107">S s možnou hodnotou Null logické hodnoty, výraz `a != b` není nutně roven `!(a == b)` vzhledem k tomu, že jedna nebo obě hodnoty může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c96a9-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="c96a9-108">Budete muset přetížení i `true` a `false` operátorům samostatně správně zpracování hodnot null ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="c96a9-108">You have to overload both the `true` and `false` operators separately to correctly handle the null values in the expression.</span></span> <span data-ttu-id="c96a9-109">Následující příklad ukazuje, jak přetížení a používat `true` a `false` operátory.</span><span class="sxs-lookup"><span data-stu-id="c96a9-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]  
  
 <span data-ttu-id="c96a9-110">Typ, který přetížení `true` a `false` operátory lze použít pro řízení výrazu v [Pokud](../../../csharp/language-reference/keywords/if-else.md), [provést](../../../csharp/language-reference/keywords/do.md), [při](../../../csharp/language-reference/keywords/while.md), a [ pro](../../../csharp/language-reference/keywords/for.md) příkazy a v [podmíněné výrazy](../../../csharp/language-reference/operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c96a9-110">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md), and [for](../../../csharp/language-reference/keywords/for.md) statements and in [conditional expressions](../../../csharp/language-reference/operators/conditional-operator.md).</span></span>  
  
 <span data-ttu-id="c96a9-111">Pokud typ definuje operátor `false`, musí definovat také operátor [true](../../../csharp/language-reference/keywords/true.md).</span><span class="sxs-lookup"><span data-stu-id="c96a9-111">If a type defines operator `false`, it must also define operator [true](../../../csharp/language-reference/keywords/true.md).</span></span>  
  
 <span data-ttu-id="c96a9-112">Typ nelze přímo přetížení podmíněného logické operátory [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) a [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), ale lze dosáhnout ekvivalentní vliv přetížení regulární logické operátory operátory a `true` a `false`.</span><span class="sxs-lookup"><span data-stu-id="c96a9-112">A type cannot directly overload the conditional logical operators [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c96a9-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c96a9-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c96a9-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c96a9-114">See Also</span></span>  
 [<span data-ttu-id="c96a9-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c96a9-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c96a9-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c96a9-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c96a9-117">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c96a9-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c96a9-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c96a9-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="c96a9-119">Hodnota TRUE</span><span class="sxs-lookup"><span data-stu-id="c96a9-119">true</span></span>](../../../csharp/language-reference/keywords/true.md)
