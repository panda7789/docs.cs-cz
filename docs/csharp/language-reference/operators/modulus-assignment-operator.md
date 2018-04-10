---
title: '%= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- modulus assignment operator (=%) [C#]
- '%= assignment operator (modulus assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9bafd0078153e29fbf923948d9b380d4795c3d35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="aa1d0-102">%= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="aa1d0-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="aa1d0-103">Operátor přiřazení zbytku.</span><span class="sxs-lookup"><span data-stu-id="aa1d0-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa1d0-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa1d0-104">Remarks</span></span>  
 <span data-ttu-id="aa1d0-105">K pomocí výrazu `%=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="aa1d0-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```  
x %= y  
```  
  
 <span data-ttu-id="aa1d0-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="aa1d0-106">is equivalent to</span></span>  
  
```  
x = x % y  
```  
  
 <span data-ttu-id="aa1d0-107">Kromě toho, že `x` je Vyhodnocená jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="aa1d0-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="aa1d0-108">[% – Operátor](../../../csharp/language-reference/operators/modulus-operator.md) je předdefinovaná pro číselné typy vypočítat zbytek po dělení.</span><span class="sxs-lookup"><span data-stu-id="aa1d0-108">The [% operator](../../../csharp/language-reference/operators/modulus-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="aa1d0-109">`%=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [% – operátor](../../../csharp/language-reference/operators/modulus-operator.md) (viz [– operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="aa1d0-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/modulus-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa1d0-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa1d0-110">Example</span></span>  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="aa1d0-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa1d0-111">See Also</span></span>  
 [<span data-ttu-id="aa1d0-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aa1d0-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="aa1d0-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="aa1d0-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="aa1d0-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aa1d0-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
