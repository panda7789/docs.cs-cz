---
title: '>>= – operátor - C# odkaz'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 51914bb5e9ebffd5d868528b5a8d3072a956cea6
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220910"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1da8e-102">>> = – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="1da8e-102">>>= operator (C# Reference)</span></span>

<span data-ttu-id="1da8e-103">Operátor přiřazení posunutí doprava.</span><span class="sxs-lookup"><span data-stu-id="1da8e-103">The right-shift assignment operator.</span></span>

<span data-ttu-id="1da8e-104">Pomocí výrazu `>>=` operátorů, například</span><span class="sxs-lookup"><span data-stu-id="1da8e-104">An expression using the `>>=` operator, such as</span></span>

```csharp
x >>= y
```

<span data-ttu-id="1da8e-105">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="1da8e-105">is equivalent to</span></span>

```csharp
x = x >> y
```

<span data-ttu-id="1da8e-106">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="1da8e-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="1da8e-107">[ `>>` Operátor](right-shift-operator.md) posune jeho prvního operandu vpravo počet bitů, které jsou určené svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="1da8e-107">The [`>>` operator](right-shift-operator.md) shifts its first operand right by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="1da8e-108">Následující příklad ukazuje použití `>>=` operátor:</span><span class="sxs-lookup"><span data-stu-id="1da8e-108">The following example demonstrates the usage of the `>>=` operator:</span></span>

[!code-csharp-interactive[right shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftAssignment)]

## <a name="operator-overloadability"></a><span data-ttu-id="1da8e-109">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="1da8e-109">Operator overloadability</span></span>

<span data-ttu-id="1da8e-110">Pokud uživatelem definovaného typu [přetížení](../keywords/operator.md) [ `>>` operátor](right-shift-operator.md), operátor přiřazení posunutí doprava `>>=` je implicitně přetížena.</span><span class="sxs-lookup"><span data-stu-id="1da8e-110">If a user-defined type [overloads](../keywords/operator.md) the [`>>` operator](right-shift-operator.md), the right-shift assignment operator `>>=` is implicitly overloaded.</span></span> <span data-ttu-id="1da8e-111">Uživatelem definovaný typ nejde explicitně přetížit operátor přiřazení posunutí doprava.</span><span class="sxs-lookup"><span data-stu-id="1da8e-111">A user-defined type cannot explicitly overload the right-shift assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1da8e-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1da8e-112">C# language specification</span></span>

<span data-ttu-id="1da8e-113">Další informace najdete v tématu [složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="1da8e-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1da8e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1da8e-114">See also</span></span>

- [<span data-ttu-id="1da8e-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1da8e-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1da8e-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1da8e-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1da8e-117">C#operátory</span><span class="sxs-lookup"><span data-stu-id="1da8e-117">C# operators</span></span>](index.md)