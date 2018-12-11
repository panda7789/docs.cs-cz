---
title: '* = – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: f8604cdadeda14a5761bc923bd966186fd258a6d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245347"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="67e2f-102">\*= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="67e2f-102">\*= Operator (C# Reference)</span></span>
<span data-ttu-id="67e2f-103">Operátor přiřazení binárního násobení.</span><span class="sxs-lookup"><span data-stu-id="67e2f-103">The binary multiplication assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67e2f-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67e2f-104">Remarks</span></span>  
 <span data-ttu-id="67e2f-105">Pomocí výrazu `*=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="67e2f-105">An expression using the `*=` assignment operator, such as</span></span>  
  
```csharp  
x *= y  
```  
  
 <span data-ttu-id="67e2f-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="67e2f-106">is equivalent to</span></span>  
  
```csharp  
x = x * y  
```  
  
 <span data-ttu-id="67e2f-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="67e2f-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="67e2f-108">[\* – Operátor](../../../csharp/language-reference/operators/multiplication-operator.md) předdefinovaných číselných typů k provedení násobení.</span><span class="sxs-lookup"><span data-stu-id="67e2f-108">The [\* operator](../../../csharp/language-reference/operators/multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>  
  
 <span data-ttu-id="67e2f-109">`*=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [\* – operátor](../../../csharp/language-reference/operators/multiplication-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="67e2f-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [\* operator](../../../csharp/language-reference/operators/multiplication-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="67e2f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="67e2f-110">Example</span></span>  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="67e2f-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="67e2f-111">See Also</span></span>

- [<span data-ttu-id="67e2f-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="67e2f-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="67e2f-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="67e2f-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="67e2f-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="67e2f-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
