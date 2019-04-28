---
title: -= – operátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 3b6890be4460a599a5d2f5f5f6ee1627be933f0b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688680"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="18d97-102">-= – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="18d97-102">-= operator (C# Reference)</span></span>

<span data-ttu-id="18d97-103">Operátor přiřazení odčítání.</span><span class="sxs-lookup"><span data-stu-id="18d97-103">The subtraction assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="18d97-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18d97-104">Remarks</span></span>

<span data-ttu-id="18d97-105">Pomocí výrazu `-=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="18d97-105">An expression using the `-=` assignment operator, such as</span></span>

```csharp
x -= y
```

 <span data-ttu-id="18d97-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="18d97-106">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="18d97-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="18d97-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="18d97-108">Význam [-– operátor](subtraction-operator.md) závisí na typech `x` a `y` (odčítání pro číselné operandy, delegovat odebrání pro delegáta operandy a tak dále).</span><span class="sxs-lookup"><span data-stu-id="18d97-108">The meaning of the [- operator](subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>

<span data-ttu-id="18d97-109">`-=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [-– operátor](subtraction-operator.md) (naleznete v tématu [operátor](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="18d97-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](subtraction-operator.md) (see [operator](../keywords/operator.md)).</span></span>

<span data-ttu-id="18d97-110">-= – Operátor také umožňuje v jazyce C# zrušit odběr události.</span><span class="sxs-lookup"><span data-stu-id="18d97-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="18d97-111">Další informace najdete v tématu [jak: Přihlaste se k odběru a zrušit její odběr události](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="18d97-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="example"></a><span data-ttu-id="18d97-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="18d97-112">Example</span></span>

[!code-csharp[csRefOperators#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#6)]

## <a name="see-also"></a><span data-ttu-id="18d97-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18d97-113">See also</span></span>

- [<span data-ttu-id="18d97-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="18d97-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="18d97-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="18d97-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="18d97-116">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="18d97-116">C# operators</span></span>](index.md)
