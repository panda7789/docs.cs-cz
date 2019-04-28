---
title: += – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: 5d48f2fe53a9bb6f781f8d35f1e0983bcaa30f88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660174"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d311e-102">+= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d311e-102">+= Operator (C# Reference)</span></span>

<span data-ttu-id="d311e-103">Operátor přiřazení sčítání.</span><span class="sxs-lookup"><span data-stu-id="d311e-103">The addition assignment operator.</span></span>

<span data-ttu-id="d311e-104">Pomocí výrazu `+=` operátorů, například</span><span class="sxs-lookup"><span data-stu-id="d311e-104">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="d311e-105">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="d311e-105">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="d311e-106">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="d311e-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="d311e-107">Pro číselné typy [operátor sčítání](addition-operator.md) `+` kód vypočítá součet operandů.</span><span class="sxs-lookup"><span data-stu-id="d311e-107">For numeric types, the [addition operator](addition-operator.md) `+` computes the sum of its operands.</span></span> <span data-ttu-id="d311e-108">Pokud je jeden nebo oba operandy typu [řetězec](../keywords/string.md), zřetězí řetězcové reprezentace jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="d311e-108">If one or both operands is of type [string](../keywords/string.md), it concatenates the string representations of its operands.</span></span> <span data-ttu-id="d311e-109">Pro typy delegátů `+` operátor vrátí novou instanci delegáta, který je kombinací operandů.</span><span class="sxs-lookup"><span data-stu-id="d311e-109">For delegate types, the `+` operator returns a new delegate instance that is combination of its operands.</span></span>

<span data-ttu-id="d311e-110">Můžete také použít `+=` operátor zadat metodu obslužné rutiny události, když se přihlásíte k odběru [události](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="d311e-110">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="d311e-111">Další informace najdete v tématu [jak: Přihlaste se k odběru a zrušit její odběr události](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="d311e-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

<span data-ttu-id="d311e-112">Následující příklad ukazuje použití `+=` operátor:</span><span class="sxs-lookup"><span data-stu-id="d311e-112">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]

## <a name="operator-overloadability"></a><span data-ttu-id="d311e-113">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="d311e-113">Operator overloadability</span></span>

<span data-ttu-id="d311e-114">Pokud uživatelský typ [přetížení](../keywords/operator.md) [operátor sčítání](addition-operator.md) `+`, operátor přiřazení sčítání `+=` je implicitně přetížena.</span><span class="sxs-lookup"><span data-stu-id="d311e-114">If a user-defined type [overloads](../keywords/operator.md) the [addition operator](addition-operator.md) `+`, the addition assignment operator `+=` is implicitly overloaded.</span></span> <span data-ttu-id="d311e-115">Uživatelem definovaný typ nejde explicitně přetížit operátor přiřazení sčítání.</span><span class="sxs-lookup"><span data-stu-id="d311e-115">A user-defined type cannot explicitly overload the addition assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d311e-116">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d311e-116">C# language specification</span></span>

<span data-ttu-id="d311e-117">Další informace najdete v tématu [složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment) a [události přiřazení](~/_csharplang/spec/expressions.md#event-assignment) oddíly [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d311e-117">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) and [Event assignment](~/_csharplang/spec/expressions.md#event-assignment) sections of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d311e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d311e-118">See also</span></span>

- [<span data-ttu-id="d311e-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d311e-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d311e-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d311e-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d311e-121">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d311e-121">C# Operators</span></span>](index.md)
- [<span data-ttu-id="d311e-122">Události</span><span class="sxs-lookup"><span data-stu-id="d311e-122">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="d311e-123">Delegáti</span><span class="sxs-lookup"><span data-stu-id="d311e-123">Delegates</span></span>](../../programming-guide/delegates/index.md)
