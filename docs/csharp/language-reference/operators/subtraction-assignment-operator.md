---
title: -= – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 2f37bfa303fb523840b15e896ee3b4a967eb5b2b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171452"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="254ab-102">-= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="254ab-102">-= Operator (C# Reference)</span></span>
<span data-ttu-id="254ab-103">Operátor přiřazení odčítání.</span><span class="sxs-lookup"><span data-stu-id="254ab-103">The subtraction assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="254ab-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="254ab-104">Remarks</span></span>  
 <span data-ttu-id="254ab-105">K pomocí výrazu `-=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="254ab-105">An expression using the `-=` assignment operator, such as</span></span>  
  
```csharp  
x -= y  
```  
  
 <span data-ttu-id="254ab-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="254ab-106">is equivalent to</span></span>  
  
```csharp  
x = x - y  
```  
  
 <span data-ttu-id="254ab-107">Kromě toho, že `x` je Vyhodnocená jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="254ab-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="254ab-108">Význam [– operátor](../../../csharp/language-reference/operators/subtraction-operator.md) závisí na typech `x` a `y` (odčítání pro číselné operandy delegovat odebrání pro operandy delegáta a tak dále).</span><span class="sxs-lookup"><span data-stu-id="254ab-108">The meaning of the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>  
  
 <span data-ttu-id="254ab-109">`-=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [– operátor](../../../csharp/language-reference/operators/subtraction-operator.md) (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="254ab-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="254ab-110">-= – Operátor používá taky v jazyce C# k odhlášení odběru událostí.</span><span class="sxs-lookup"><span data-stu-id="254ab-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="254ab-111">Další informace najdete v tématu [postupy: přihlášení a odhlášení odběru událostí](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="254ab-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="254ab-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="254ab-112">Example</span></span>  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="254ab-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="254ab-113">See Also</span></span>  
 [<span data-ttu-id="254ab-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="254ab-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="254ab-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="254ab-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="254ab-116">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="254ab-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
