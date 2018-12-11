---
title: '&amp;= – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: 223d2f30ee77457e1f9d5304ec299517932499d0
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237022"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="1013d-102">&amp;= – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1013d-102">&amp;= Operator (C# Reference)</span></span>

<span data-ttu-id="1013d-103">Operátor přiřazení AND.</span><span class="sxs-lookup"><span data-stu-id="1013d-103">The AND assignment operator.</span></span>

<span data-ttu-id="1013d-104">Pomocí výrazu `&=` operátorů, například</span><span class="sxs-lookup"><span data-stu-id="1013d-104">An expression using the `&=` operator, such as</span></span>

```csharp
x &= y
```

<span data-ttu-id="1013d-105">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="1013d-105">is equivalent to</span></span>

```csharp
x = x & y
```

<span data-ttu-id="1013d-106">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="1013d-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="1013d-107">Pro celočíselné operandy [ `&` operátor](and-operator.md) vypočítá bitové logické AND operandů; pro [bool](../keywords/bool.md) operandy, vypočítá logický operátor AND operandů.</span><span class="sxs-lookup"><span data-stu-id="1013d-107">For integer operands, the [`&` operator](and-operator.md) computes the bitwise logical AND of its operands; for [bool](../keywords/bool.md) operands, it computes the logical AND of its operands.</span></span>

<span data-ttu-id="1013d-108">Následující příklad ukazuje použití `&=` operátor:</span><span class="sxs-lookup"><span data-stu-id="1013d-108">The following example demonstrates the usage of the `&=` operator:</span></span>

[!code-csharp-interactive[AND assignment example](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#AndAssignmentExample)]

## <a name="operator-overloadability"></a><span data-ttu-id="1013d-109">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="1013d-109">Operator overloadability</span></span>

<span data-ttu-id="1013d-110">Pokud uživatelem definovaného typu [přetížení](../keywords/operator.md) [ `&` operátor](and-operator.md), operátor přiřazení AND `&=` je implicitně přetížena.</span><span class="sxs-lookup"><span data-stu-id="1013d-110">If a user-defined type [overloads](../keywords/operator.md) the [`&` operator](and-operator.md), the AND assignment operator `&=` is implicitly overloaded.</span></span> <span data-ttu-id="1013d-111">Uživatelem definovaný typ nejde explicitně přetížit operátor přiřazení AND.</span><span class="sxs-lookup"><span data-stu-id="1013d-111">A user-defined type cannot explicitly overload the AND assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1013d-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1013d-112">C# language specification</span></span>

<span data-ttu-id="1013d-113">Další informace najdete v tématu [složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="1013d-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1013d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1013d-114">See also</span></span>

- [<span data-ttu-id="1013d-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1013d-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1013d-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1013d-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1013d-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1013d-117">C# Operators</span></span>](index.md)
