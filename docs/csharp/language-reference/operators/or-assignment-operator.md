---
title: "|= – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aac4fd6016b65daa15da4bd3a414f385edce7c22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b771d-102">|= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b771d-102">|= Operator (C# Reference)</span></span>
<span data-ttu-id="b771d-103">Operátor přiřazení OR.</span><span class="sxs-lookup"><span data-stu-id="b771d-103">The OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b771d-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b771d-104">Remarks</span></span>  
 <span data-ttu-id="b771d-105">K pomocí výrazu `|=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="b771d-105">An expression using the `|=` assignment operator, such as</span></span>  
  
```  
x |= y  
```  
  
 <span data-ttu-id="b771d-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="b771d-106">is equivalent to</span></span>  
  
```  
x = x | y  
```  
  
 <span data-ttu-id="b771d-107">Kromě toho, že `x` je Vyhodnocená jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="b771d-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="b771d-108">[&#124; operátor](../../../csharp/language-reference/operators/or-operator.md) bitové logický provoz nebo na integrální operandy a logické nebo provádí bool operandy.</span><span class="sxs-lookup"><span data-stu-id="b771d-108">The [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>  
  
 <span data-ttu-id="b771d-109">`|=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [&#124; – operátor](../../../csharp/language-reference/operators/or-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="b771d-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b771d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b771d-110">Example</span></span>  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b771d-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b771d-111">See Also</span></span>  
 [<span data-ttu-id="b771d-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b771d-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b771d-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b771d-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b771d-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b771d-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
