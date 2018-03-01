---
title: "&amp;= – Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bea90651faaafe7b754ce1cf16bddbab997d5f5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="fa37e-102">&amp;= – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="fa37e-102">&amp;= Operator (C# Reference)</span></span>
<span data-ttu-id="fa37e-103">Operátor přiřazení a.</span><span class="sxs-lookup"><span data-stu-id="fa37e-103">The AND assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa37e-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa37e-104">Remarks</span></span>  
 <span data-ttu-id="fa37e-105">K pomocí výrazu `&=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="fa37e-105">An expression using the `&=` assignment operator, such as</span></span>  
  
```  
x &= y  
```  
  
 <span data-ttu-id="fa37e-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="fa37e-106">is equivalent to</span></span>  
  
```  
x = x & y  
```  
  
 <span data-ttu-id="fa37e-107">Kromě toho, že `x` je Vyhodnocená jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="fa37e-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="fa37e-108">[& Operátor](../../../csharp/language-reference/operators/and-operator.md) bitové logické a operace na integrální operandy a logické a provádí `bool` operandy.</span><span class="sxs-lookup"><span data-stu-id="fa37e-108">The [& operator](../../../csharp/language-reference/operators/and-operator.md) performs a bitwise logical AND operation on integral operands and logical AND on `bool` operands.</span></span>  
  
 <span data-ttu-id="fa37e-109">`&=` Operátor nemohou být přetíženy přímo, ale uživatelem definované typy může přetížit binárního souboru [& operátor](../../../csharp/language-reference/operators/and-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="fa37e-109">The `&=` operator cannot be overloaded directly, but user-defined types can overload the binary [& operator](../../../csharp/language-reference/operators/and-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa37e-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa37e-110">Example</span></span>  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="fa37e-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa37e-111">See Also</span></span>  
 [<span data-ttu-id="fa37e-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fa37e-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="fa37e-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="fa37e-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fa37e-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fa37e-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
