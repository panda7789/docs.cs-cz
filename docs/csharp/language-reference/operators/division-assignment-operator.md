---
title: "/= – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 26096d9b5dfc565c9933f1ed8ffb241dc900d9ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4cbb4-102">/= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4cbb4-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="4cbb4-103">Operátor přiřazení dělení.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cbb4-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4cbb4-104">Remarks</span></span>  
 <span data-ttu-id="4cbb4-105">K pomocí výrazu `/=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="4cbb4-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```  
x /= y  
```  
  
 <span data-ttu-id="4cbb4-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="4cbb4-106">is equivalent to</span></span>  
  
```  
x = x / y  
```  
  
 <span data-ttu-id="4cbb4-107">Kromě toho, že `x` je Vyhodnocená jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="4cbb4-108">[Nebo operátor](../../../csharp/language-reference/operators/division-operator.md) je předdefinovaná pro číselné typy provádět dělení.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="4cbb4-109">`/=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [nebo operátor](../../../csharp/language-reference/operators/division-operator.md) (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="4cbb4-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="4cbb4-110">Na všechny složené operátory přiřazení přetížení binární operátor implicitně přetížení ekvivalentní složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="4cbb4-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cbb4-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cbb4-111">Example</span></span>  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4cbb4-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="4cbb4-112">See Also</span></span>  
 [<span data-ttu-id="4cbb4-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4cbb4-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4cbb4-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4cbb4-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4cbb4-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4cbb4-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
