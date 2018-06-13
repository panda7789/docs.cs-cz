---
title: '%= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 04/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: aadcb5ef969ff408cc1e738fc0f5b67152fdc78b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171964"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9054f-102">%= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9054f-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="9054f-103">Operátor přiřazení zbytku.</span><span class="sxs-lookup"><span data-stu-id="9054f-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9054f-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9054f-104">Remarks</span></span>  
 <span data-ttu-id="9054f-105">K pomocí výrazu `%=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="9054f-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```csharp  
x %= y  
```  
  
 <span data-ttu-id="9054f-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="9054f-106">is equivalent to</span></span>  
  
```csharp  
x = x % y  
```  
  
 <span data-ttu-id="9054f-107">Kromě toho, že `x` je Vyhodnocená jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="9054f-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="9054f-108">[% – Operátor](../../../csharp/language-reference/operators/remainder-operator.md) je předdefinovaná pro číselné typy vypočítat zbytek po dělení.</span><span class="sxs-lookup"><span data-stu-id="9054f-108">The [% operator](../../../csharp/language-reference/operators/remainder-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="9054f-109">`%=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [% – operátor](../../../csharp/language-reference/operators/remainder-operator.md) (viz [– operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="9054f-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/remainder-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9054f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="9054f-110">Example</span></span>  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9054f-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="9054f-111">See Also</span></span>  
 [<span data-ttu-id="9054f-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9054f-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9054f-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9054f-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9054f-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9054f-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
