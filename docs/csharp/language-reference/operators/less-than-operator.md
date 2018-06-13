---
title: '&lt; Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
ms.openlocfilehash: eceb6214e4e625aa71e12788d5dd5e8324c75443
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270228"
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="d8c65-102">&lt; Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d8c65-102">&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="d8c65-103">Všechny typy číselné a výčet definovat "menší než" relační operátor (`<`), který vrací `true` Pokud první operand je menší než druhý, `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="d8c65-103">All numeric and enumeration types define a "less than" relational operator (`<`) that returns `true` if the first operand is less than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8c65-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8c65-104">Remarks</span></span>  
 <span data-ttu-id="d8c65-105">Uživatelem definované typy může přetížit `<` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d8c65-105">User-defined types can overload the `<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="d8c65-106">Pokud `<` je přetížena [ > ](../../../csharp/language-reference/operators/greater-than-operator.md) také musí být přetížený.</span><span class="sxs-lookup"><span data-stu-id="d8c65-106">If `<` is overloaded, [>](../../../csharp/language-reference/operators/greater-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="d8c65-107">Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="d8c65-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8c65-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="d8c65-108">Example</span></span>  
 [!code-csharp[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d8c65-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8c65-109">See Also</span></span>  
 [<span data-ttu-id="d8c65-110">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d8c65-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d8c65-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d8c65-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d8c65-112">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d8c65-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
