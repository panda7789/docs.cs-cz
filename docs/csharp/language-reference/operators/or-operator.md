---
title: '| – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 374adc30e6937a68d67bfae152f2546c854b829b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9947a-102">| – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9947a-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="9947a-103">Binární `|` jsou operátory předdefinovány pro integrální typy a `bool`.</span><span class="sxs-lookup"><span data-stu-id="9947a-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="9947a-104">Pro integrální typy `|` vypočítá bitová hodnota OR jejími operandy.</span><span class="sxs-lookup"><span data-stu-id="9947a-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="9947a-105">Pro `bool` operandy, `|` vypočítá logické nebo operandů; to znamená, výsledkem je `false` Pokud jsou obě jejími operandy `false`.</span><span class="sxs-lookup"><span data-stu-id="9947a-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9947a-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9947a-106">Remarks</span></span>  
 <span data-ttu-id="9947a-107">Uživatelem definované typy může přetížit `|` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="9947a-107">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9947a-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="9947a-108">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9947a-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="9947a-109">See Also</span></span>  
 [<span data-ttu-id="9947a-110">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9947a-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9947a-111">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="9947a-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9947a-112">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9947a-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
