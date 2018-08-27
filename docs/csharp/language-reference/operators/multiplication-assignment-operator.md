---
title: '*= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: e47bc5c681c94ac3fc5c345c56b3814350ffa5ec
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932347"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="7e5be-102">\*= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7e5be-102">\*= Operator (C# Reference)</span></span>
<span data-ttu-id="7e5be-103">Operátor přiřazení binárního násobení.</span><span class="sxs-lookup"><span data-stu-id="7e5be-103">The binary multiplication assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e5be-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e5be-104">Remarks</span></span>  
 <span data-ttu-id="7e5be-105">Pomocí výrazu `*=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="7e5be-105">An expression using the `*=` assignment operator, such as</span></span>  
  
```csharp  
x *= y  
```  
  
 <span data-ttu-id="7e5be-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="7e5be-106">is equivalent to</span></span>  
  
```csharp  
x = x * y  
```  
  
 <span data-ttu-id="7e5be-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="7e5be-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="7e5be-108">[\* – Operátor](../../../csharp/language-reference/operators/multiplication-operator.md) předdefinovaných číselných typů k provedení násobení.</span><span class="sxs-lookup"><span data-stu-id="7e5be-108">The [\* operator](../../../csharp/language-reference/operators/multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>  
  
 <span data-ttu-id="7e5be-109">`*=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [* – operátor](../../../csharp/language-reference/operators/multiplication-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="7e5be-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e5be-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e5be-110">Example</span></span>  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7e5be-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e5be-111">See Also</span></span>

- [<span data-ttu-id="7e5be-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7e5be-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="7e5be-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7e5be-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="7e5be-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7e5be-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
