---
title: / = – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: ed4dd6c0c944b77543aae4de8d51534b4df4f4ef
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286517"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c7156-102">/= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c7156-102">/= Operator (C# Reference)</span></span>

<span data-ttu-id="c7156-103">Operátor přiřazení dělení.</span><span class="sxs-lookup"><span data-stu-id="c7156-103">The division assignment operator.</span></span>

<span data-ttu-id="c7156-104">Pomocí výrazu `/=` operátorů, například</span><span class="sxs-lookup"><span data-stu-id="c7156-104">An expression using the `/=` operator, such as</span></span>

```csharp
x /= y
```

<span data-ttu-id="c7156-105">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="c7156-105">is equivalent to</span></span>

```csharp
x = x / y
```

<span data-ttu-id="c7156-106">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="c7156-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="c7156-107">[Operátor dělení](division-operator.md) `/` rozděluje svůj první operand tak svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="c7156-107">The [division operator](division-operator.md) `/` divides its first operand by its second operand.</span></span> <span data-ttu-id="c7156-108">Podporuje všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="c7156-108">It's supported by all numeric types.</span></span>

<span data-ttu-id="c7156-109">Následující příklad ukazuje použití `/=` operátor:</span><span class="sxs-lookup"><span data-stu-id="c7156-109">The following example demonstrates the usage of the `/=` operator:</span></span>

[!code-csharp-interactive[divide and assign](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#DivisionAssignment)]

## <a name="operator-overloadability"></a><span data-ttu-id="c7156-110">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="c7156-110">Operator overloadability</span></span>

<span data-ttu-id="c7156-111">Pokud uživatelský typ [přetížení](../keywords/operator.md) [operátor dělení](division-operator.md) `/`, operátor přiřazení dělení `/=` je implicitně přetížena.</span><span class="sxs-lookup"><span data-stu-id="c7156-111">If a user-defined type [overloads](../keywords/operator.md) the [division operator](division-operator.md) `/`, the division assignment operator `/=` is implicitly overloaded.</span></span> <span data-ttu-id="c7156-112">Uživatelem definovaný typ nejde explicitně přetížit operátor přiřazení dělení.</span><span class="sxs-lookup"><span data-stu-id="c7156-112">A user-defined type cannot explicitly overload the division assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c7156-113">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c7156-113">C# language specification</span></span>

<span data-ttu-id="c7156-114">Další informace najdete v tématu [složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="c7156-114">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c7156-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7156-115">See also</span></span>

- [<span data-ttu-id="c7156-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c7156-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c7156-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c7156-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c7156-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c7156-118">C# Operators</span></span>](index.md)
