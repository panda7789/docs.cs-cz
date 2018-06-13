---
title: '*= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 6bbf2142ca7e9e05010a29920da52e1439f6e882
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171547"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="63f72-102">\*= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="63f72-102">\*= Operator (C# Reference)</span></span>
<span data-ttu-id="63f72-103">Operátor přiřazení binárního násobení.</span><span class="sxs-lookup"><span data-stu-id="63f72-103">The binary multiplication assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63f72-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63f72-104">Remarks</span></span>  
 <span data-ttu-id="63f72-105">K pomocí výrazu `*=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="63f72-105">An expression using the `*=` assignment operator, such as</span></span>  
  
```csharp  
x *= y  
```  
  
 <span data-ttu-id="63f72-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="63f72-106">is equivalent to</span></span>  
  
```csharp  
x = x * y  
```  
  
 <span data-ttu-id="63f72-107">Kromě toho, že `x` je Vyhodnocená jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="63f72-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="63f72-108">[\* Operátor](../../../csharp/language-reference/operators/multiplication-operator.md) je předdefinovaná pro číselné typy provést násobení.</span><span class="sxs-lookup"><span data-stu-id="63f72-108">The [\* operator](../../../csharp/language-reference/operators/multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>  
  
 <span data-ttu-id="63f72-109">`*=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [* operátor](../../../csharp/language-reference/operators/multiplication-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="63f72-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63f72-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="63f72-110">Example</span></span>  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="63f72-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="63f72-111">See Also</span></span>  
 [<span data-ttu-id="63f72-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="63f72-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="63f72-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="63f72-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="63f72-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="63f72-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
