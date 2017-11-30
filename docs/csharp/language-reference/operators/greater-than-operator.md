---
title: "&gt;Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fc7c173ecc97bd3ca3b76a92ccbabc0f40062ac7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="75fff-102">&gt;Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="75fff-102">&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="75fff-103">Všechny typy číselné a výčet definovat relační operátor "větší než" (`>`), který vrací `true` Pokud první operand je větší než druhý, `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="75fff-103">All numeric and enumeration types define a "greater than" relational operator (`>`) that returns `true` if the first operand is greater than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75fff-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75fff-104">Remarks</span></span>  
 <span data-ttu-id="75fff-105">Uživatelem definované typy může přetížit `>` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="75fff-105">User-defined types can overload the `>` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="75fff-106">Pokud `>` je přetížena [ < ](../../../csharp/language-reference/operators/less-than-operator.md) také musí být přetížený.</span><span class="sxs-lookup"><span data-stu-id="75fff-106">If `>` is overloaded, [<](../../../csharp/language-reference/operators/less-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="75fff-107">Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="75fff-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75fff-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="75fff-108">Example</span></span>  
 [!code-csharp[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="75fff-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="75fff-109">See Also</span></span>  
 [<span data-ttu-id="75fff-110">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="75fff-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="75fff-111">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="75fff-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="75fff-112">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="75fff-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="75fff-113">explicitní</span><span class="sxs-lookup"><span data-stu-id="75fff-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)
