---
title: '% – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- modulus operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cea4aa03424e93f3ec144126d73c63931a737b54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="2a371-102">% – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2a371-102">% Operator (C# Reference)</span></span>
<span data-ttu-id="2a371-103">`%` Operátor vypočítá zbytek po dělení jeho první operand jeho sekundu.</span><span class="sxs-lookup"><span data-stu-id="2a371-103">The `%` operator computes the remainder after dividing its first operand by its second.</span></span> <span data-ttu-id="2a371-104">Všechny číselné typy obsahuje předdefinované zbývající operátory.</span><span class="sxs-lookup"><span data-stu-id="2a371-104">All numeric types have predefined remainder operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a371-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2a371-105">Remarks</span></span>  
 <span data-ttu-id="2a371-106">Uživatelem definované typy může přetížit `%` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="2a371-106">User-defined types can overload the `%` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="2a371-107">Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="2a371-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a371-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a371-108">Example</span></span>  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="2a371-109">Komentáře</span><span class="sxs-lookup"><span data-stu-id="2a371-109">Comments</span></span>  
 <span data-ttu-id="2a371-110">Všimněte si zaokrouhlovací chyby související s typ double.</span><span class="sxs-lookup"><span data-stu-id="2a371-110">Note the round-off errors associated with the double type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a371-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a371-111">See Also</span></span>  
 [<span data-ttu-id="2a371-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2a371-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2a371-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="2a371-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2a371-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2a371-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
