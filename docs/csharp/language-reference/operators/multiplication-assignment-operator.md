---
title: '*= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc2201f78e1e05bd0ccdea04522896c00294bdd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="56794-102">\*= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="56794-102">\*= Operator (C# Reference)</span></span>
<span data-ttu-id="56794-103">Operátor přiřazení binárního násobení.</span><span class="sxs-lookup"><span data-stu-id="56794-103">The binary multiplication assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56794-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56794-104">Remarks</span></span>  
 <span data-ttu-id="56794-105">K pomocí výrazu `*=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="56794-105">An expression using the `*=` assignment operator, such as</span></span>  
  
```  
x *= y  
```  
  
 <span data-ttu-id="56794-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="56794-106">is equivalent to</span></span>  
  
```  
x = x * y  
```  
  
 <span data-ttu-id="56794-107">Kromě toho, že `x` je Vyhodnocená jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="56794-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="56794-108">[\* Operátor](../../../csharp/language-reference/operators/multiplication-operator.md) je předdefinovaná pro číselné typy provést násobení.</span><span class="sxs-lookup"><span data-stu-id="56794-108">The [\* operator](../../../csharp/language-reference/operators/multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>  
  
 <span data-ttu-id="56794-109">`*=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [* operátor](../../../csharp/language-reference/operators/multiplication-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="56794-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56794-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="56794-110">Example</span></span>  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="56794-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="56794-111">See Also</span></span>  
 [<span data-ttu-id="56794-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="56794-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="56794-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="56794-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="56794-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="56794-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
