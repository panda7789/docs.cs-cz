---
title: += – operátor (Referenční dokumentace jazyka C#)
ms.date: 10/22/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: ee335e3e2e7d352d4e26b802bad2b08a05c666ab
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192028"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9faad-102">+= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9faad-102">+= Operator (C# Reference)</span></span>

<span data-ttu-id="9faad-103">Operátor přiřazení sčítání.</span><span class="sxs-lookup"><span data-stu-id="9faad-103">The addition assignment operator.</span></span>

<span data-ttu-id="9faad-104">Pomocí výrazu `+=` operátorů, například</span><span class="sxs-lookup"><span data-stu-id="9faad-104">An expression using the `+=` operator, such as</span></span>  

```csharp
x += y
```  

<span data-ttu-id="9faad-105">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="9faad-105">is equivalent to</span></span>  

```csharp
x = x + y
```  

<span data-ttu-id="9faad-106">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="9faad-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="9faad-107">Pro číselné typy [operátor sčítání](addition-operator.md) `+` kód vypočítá součet operandů.</span><span class="sxs-lookup"><span data-stu-id="9faad-107">For numeric types, the [addition operator](addition-operator.md) `+` computes the sum of its operands.</span></span> <span data-ttu-id="9faad-108">Pokud je jeden nebo oba operandy typu [řetězec](../keywords/string.md), zřetězí řetězcové reprezentace jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="9faad-108">If one or both operands is of type [string](../keywords/string.md), it concatenates the string representations of its operands.</span></span> <span data-ttu-id="9faad-109">Pro typy delegátů `+` operátor vrátí novou instanci delegáta, který je kombinací operandů.</span><span class="sxs-lookup"><span data-stu-id="9faad-109">For delegate types, the `+` operator returns a new delegate instance that is combination of its operands.</span></span>

<span data-ttu-id="9faad-110">Pokud uživatelský typ [přetížení](../keywords/operator.md) [operátor sčítání](addition-operator.md) `+`, operátor přiřazení sčítání `+=` je implicitně přetížena.</span><span class="sxs-lookup"><span data-stu-id="9faad-110">If a user-defined type [overloads](../keywords/operator.md) the [addition operator](addition-operator.md) `+`, the addition assignment operator `+=` is implicitly overloaded.</span></span>

<span data-ttu-id="9faad-111">Můžete také použít `+=` operátor zadat metodu obslužné rutiny události, když se přihlásíte k odběru [události](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="9faad-111">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="9faad-112">Další informace najdete v tématu [postupy: přihlášení k odběru a zrušit její odběr události](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="9faad-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

<span data-ttu-id="9faad-113">Následující příklad ukazuje použití `+=` operátor:</span><span class="sxs-lookup"><span data-stu-id="9faad-113">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]
  
## <a name="see-also"></a><span data-ttu-id="9faad-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9faad-114">See also</span></span>

- [<span data-ttu-id="9faad-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9faad-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9faad-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9faad-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9faad-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9faad-117">C# Operators</span></span>](index.md)
- [<span data-ttu-id="9faad-118">Události</span><span class="sxs-lookup"><span data-stu-id="9faad-118">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="9faad-119">Delegáti</span><span class="sxs-lookup"><span data-stu-id="9faad-119">Delegates</span></span>](../../programming-guide/delegates/index.md)
