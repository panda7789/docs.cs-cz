---
title: "&lt;Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76d53d4c943c886f6b8c8a68e2b8bb12bc9a9d6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="4ee53-102">&lt;Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4ee53-102">&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="4ee53-103">Všechny typy číselné a výčet definovat "menší než" relační operátor (`<`), který vrací `true` Pokud první operand je menší než druhý, `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="4ee53-103">All numeric and enumeration types define a "less than" relational operator (`<`) that returns `true` if the first operand is less than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ee53-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ee53-104">Remarks</span></span>  
 <span data-ttu-id="4ee53-105">Uživatelem definované typy může přetížit `<` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="4ee53-105">User-defined types can overload the `<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="4ee53-106">Pokud `<` je přetížena [ > ](../../../csharp/language-reference/operators/greater-than-operator.md) také musí být přetížený.</span><span class="sxs-lookup"><span data-stu-id="4ee53-106">If `<` is overloaded, [>](../../../csharp/language-reference/operators/greater-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="4ee53-107">Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="4ee53-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ee53-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ee53-108">Example</span></span>  
 [!code-csharp[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4ee53-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ee53-109">See Also</span></span>  
 [<span data-ttu-id="4ee53-110">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4ee53-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4ee53-111">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4ee53-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4ee53-112">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4ee53-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
