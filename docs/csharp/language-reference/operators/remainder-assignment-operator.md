---
title: '%= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 04/04/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 864b96dcf16e4756cd0e74a6e02297660e72357e
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ca8bd-102">%= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ca8bd-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="ca8bd-103">Operátor přiřazení zbytku.</span><span class="sxs-lookup"><span data-stu-id="ca8bd-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca8bd-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca8bd-104">Remarks</span></span>  
 <span data-ttu-id="ca8bd-105">K pomocí výrazu `%=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="ca8bd-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```  
x %= y  
```  
  
 <span data-ttu-id="ca8bd-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="ca8bd-106">is equivalent to</span></span>  
  
```  
x = x % y  
```  
  
 <span data-ttu-id="ca8bd-107">Kromě toho, že `x` je Vyhodnocená jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="ca8bd-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="ca8bd-108">[% – Operátor](../../../csharp/language-reference/operators/remainder-operator.md) je předdefinovaná pro číselné typy vypočítat zbytek po dělení.</span><span class="sxs-lookup"><span data-stu-id="ca8bd-108">The [% operator](../../../csharp/language-reference/operators/remainder-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="ca8bd-109">`%=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [% – operátor](../../../csharp/language-reference/operators/remainder-operator.md) (viz [– operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="ca8bd-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/remainder-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca8bd-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ca8bd-110">Example</span></span>  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ca8bd-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca8bd-111">See Also</span></span>  
 [<span data-ttu-id="ca8bd-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ca8bd-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ca8bd-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ca8bd-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ca8bd-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ca8bd-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
