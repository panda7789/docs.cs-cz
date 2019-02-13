---
title: << = – operátor - C# odkaz
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: d2105fbee4ddfe1b2cb3325d82b0f2f8c5559297
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219446"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="03c46-102">\<\<= – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="03c46-102">\<\<= operator (C# Reference)</span></span>

<span data-ttu-id="03c46-103">Operátor přiřazení posunutí doleva.</span><span class="sxs-lookup"><span data-stu-id="03c46-103">The left-shift assignment operator.</span></span>

<span data-ttu-id="03c46-104">Pomocí výrazu `<<=` operátorů, například</span><span class="sxs-lookup"><span data-stu-id="03c46-104">An expression using the `<<=` operator, such as</span></span>

```csharp
x <<= y
```

<span data-ttu-id="03c46-105">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="03c46-105">is equivalent to</span></span>

```csharp
x = x << y
```

<span data-ttu-id="03c46-106">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="03c46-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="03c46-107">[ `<<` Operátor](left-shift-operator.md) staffhubu svůj první operand doleva o počet bitů, které jsou určené svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="03c46-107">The [`<<` operator](left-shift-operator.md) shifts its first operand left by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="03c46-108">Následující příklad ukazuje použití `<<=` operátor:</span><span class="sxs-lookup"><span data-stu-id="03c46-108">The following example demonstrates the usage of the `<<=` operator:</span></span>

[!code-csharp-interactive[left shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftAssignment)]

## <a name="operator-overloadability"></a><span data-ttu-id="03c46-109">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="03c46-109">Operator overloadability</span></span>

<span data-ttu-id="03c46-110">Pokud uživatelem definovaného typu [přetížení](../keywords/operator.md) [ `<<` operátor](left-shift-operator.md), operátor přiřazení posunutí doleva `<<=` je implicitně přetížena.</span><span class="sxs-lookup"><span data-stu-id="03c46-110">If a user-defined type [overloads](../keywords/operator.md) the [`<<` operator](left-shift-operator.md), the left-shift assignment operator `<<=` is implicitly overloaded.</span></span> <span data-ttu-id="03c46-111">Uživatelem definovaný typ nejde explicitně přetížit operátor přiřazení posunutí doleva.</span><span class="sxs-lookup"><span data-stu-id="03c46-111">A user-defined type cannot explicitly overload the left-shift assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="03c46-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="03c46-112">C# language specification</span></span>

<span data-ttu-id="03c46-113">Další informace najdete v tématu [složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="03c46-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="03c46-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03c46-114">See also</span></span>

- [<span data-ttu-id="03c46-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="03c46-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="03c46-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="03c46-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="03c46-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="03c46-117">C# Operators</span></span>](index.md)
