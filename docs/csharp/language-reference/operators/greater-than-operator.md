---
title: '&gt; Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
ms.openlocfilehash: 1589c5e785b33db6106a0ef0a58202e771db9fa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273495"
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="425ca-102">&gt; Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="425ca-102">&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="425ca-103">Všechny typy číselné a výčet definovat relační operátor "větší než" (`>`), který vrací `true` Pokud první operand je větší než druhý, `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="425ca-103">All numeric and enumeration types define a "greater than" relational operator (`>`) that returns `true` if the first operand is greater than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="425ca-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="425ca-104">Remarks</span></span>  
 <span data-ttu-id="425ca-105">Uživatelem definované typy může přetížit `>` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="425ca-105">User-defined types can overload the `>` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="425ca-106">Pokud `>` je přetížena [ < ](../../../csharp/language-reference/operators/less-than-operator.md) také musí být přetížený.</span><span class="sxs-lookup"><span data-stu-id="425ca-106">If `>` is overloaded, [<](../../../csharp/language-reference/operators/less-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="425ca-107">Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="425ca-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="425ca-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="425ca-108">Example</span></span>  
 [!code-csharp[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="425ca-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="425ca-109">See Also</span></span>  
 [<span data-ttu-id="425ca-110">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="425ca-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="425ca-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="425ca-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="425ca-112">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="425ca-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="425ca-113">explicit</span><span class="sxs-lookup"><span data-stu-id="425ca-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)
