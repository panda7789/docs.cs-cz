---
title: -= – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: dc3cedafc57e1c6ec9bc34ca4e2c2aa9c604848c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239576"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="0b1a4-102">-= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0b1a4-102">-= Operator (C# Reference)</span></span>
<span data-ttu-id="0b1a4-103">Operátor přiřazení odčítání.</span><span class="sxs-lookup"><span data-stu-id="0b1a4-103">The subtraction assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b1a4-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b1a4-104">Remarks</span></span>  
 <span data-ttu-id="0b1a4-105">Pomocí výrazu `-=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="0b1a4-105">An expression using the `-=` assignment operator, such as</span></span>  
  
```csharp  
x -= y  
```  
  
 <span data-ttu-id="0b1a4-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="0b1a4-106">is equivalent to</span></span>  
  
```csharp  
x = x - y  
```  
  
 <span data-ttu-id="0b1a4-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="0b1a4-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="0b1a4-108">Význam [-– operátor](../../../csharp/language-reference/operators/subtraction-operator.md) závisí na typech `x` a `y` (odčítání pro číselné operandy, delegovat odebrání pro delegáta operandy a tak dále).</span><span class="sxs-lookup"><span data-stu-id="0b1a4-108">The meaning of the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>  
  
 <span data-ttu-id="0b1a4-109">`-=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [-– operátor](../../../csharp/language-reference/operators/subtraction-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="0b1a4-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="0b1a4-110">-= – Operátor také umožňuje v jazyce C# zrušit odběr události.</span><span class="sxs-lookup"><span data-stu-id="0b1a4-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="0b1a4-111">Další informace najdete v tématu [jak: Přihlaste se k odběru a zrušit její odběr události](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="0b1a4-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b1a4-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b1a4-112">Example</span></span>  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0b1a4-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b1a4-113">See Also</span></span>

- [<span data-ttu-id="0b1a4-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0b1a4-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="0b1a4-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0b1a4-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0b1a4-116">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0b1a4-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
