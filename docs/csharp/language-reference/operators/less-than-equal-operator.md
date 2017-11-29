---
title: "&lt;= – Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: <=_CSharpKeyword
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a74af852451a193aaee70fea2a68ca8ff29cc215
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="a11a5-102">&lt;= – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a11a5-102">&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="a11a5-103">Všechny typy číselné a výčet definice "menší než nebo rovno" relační operátora (`<=`), který vrací `true` Pokud první operand je menší než nebo rovna druhý, `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="a11a5-103">All numeric and enumeration types define a "less than or equal" relational operator (`<=`) that returns `true` if the first operand is less than or equal to the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a11a5-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a11a5-104">Remarks</span></span>  
 <span data-ttu-id="a11a5-105">Uživatelem definované typy může přetížit `<=` operátor.</span><span class="sxs-lookup"><span data-stu-id="a11a5-105">User-defined types can overload the `<=` operator.</span></span> <span data-ttu-id="a11a5-106">Další informace najdete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="a11a5-106">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="a11a5-107">Pokud `<=` je přetížena [ >= ](../../../csharp/language-reference/operators/greater-than-equal-operator.md) také musí být přetížený.</span><span class="sxs-lookup"><span data-stu-id="a11a5-107">If `<=` is overloaded, [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="a11a5-108">Operace u celočíselných typů jsou obecně povoleny na výčtu.</span><span class="sxs-lookup"><span data-stu-id="a11a5-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a11a5-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a11a5-109">Example</span></span>  
 [!code-csharp[csRefOperators#32](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a11a5-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a11a5-110">See Also</span></span>  
 [<span data-ttu-id="a11a5-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a11a5-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a11a5-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a11a5-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a11a5-113">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a11a5-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="a11a5-114">explicitní</span><span class="sxs-lookup"><span data-stu-id="a11a5-114">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)
