---
title: '%= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 04/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: 009c162b13fab05ba349d0535fe8dfae206502f3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507934"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="55428-102">%= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="55428-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="55428-103">Operátor přiřazení zbytku.</span><span class="sxs-lookup"><span data-stu-id="55428-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55428-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55428-104">Remarks</span></span>  
 <span data-ttu-id="55428-105">Pomocí výrazu `%=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="55428-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```csharp  
x %= y  
```  
  
 <span data-ttu-id="55428-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="55428-106">is equivalent to</span></span>  
  
```csharp  
x = x % y  
```  
  
 <span data-ttu-id="55428-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="55428-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="55428-108">[% – Operátor](../../../csharp/language-reference/operators/remainder-operator.md) předdefinovaných číselných typů k výpočtu zbytek po dělení.</span><span class="sxs-lookup"><span data-stu-id="55428-108">The [% operator](../../../csharp/language-reference/operators/remainder-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="55428-109">`%=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [% – operátor](../../../csharp/language-reference/operators/remainder-operator.md) (viz [– operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="55428-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/remainder-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55428-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="55428-110">Example</span></span>  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="55428-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="55428-111">See Also</span></span>

- [<span data-ttu-id="55428-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="55428-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="55428-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="55428-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="55428-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="55428-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
