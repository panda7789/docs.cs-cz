---
title: '* = – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 70461f79e714e44354fe4137e5360769fa048d3e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967383"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3d2ec-102">\*= – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3d2ec-102">\*= Operator (C# Reference)</span></span>

<span data-ttu-id="3d2ec-103">Operátor přiřazení násobení.</span><span class="sxs-lookup"><span data-stu-id="3d2ec-103">The multiplication assignment operator.</span></span>

<span data-ttu-id="3d2ec-104">Pomocí výrazu `*=` operátorů, například</span><span class="sxs-lookup"><span data-stu-id="3d2ec-104">An expression using the `*=` operator, such as</span></span>

```csharp
x *= y
```

<span data-ttu-id="3d2ec-105">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="3d2ec-105">is equivalent to</span></span>

```csharp
x = x * y
```

<span data-ttu-id="3d2ec-106">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="3d2ec-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="3d2ec-107">Pro číselné typy [ \* operátor](multiplication-operator.md) vypočítá součin z operandů.</span><span class="sxs-lookup"><span data-stu-id="3d2ec-107">For numeric types, the [\* operator](multiplication-operator.md) computes the product of its operands.</span></span>

<span data-ttu-id="3d2ec-108">Následující příklad ukazuje použití `*=` operátor:</span><span class="sxs-lookup"><span data-stu-id="3d2ec-108">The following example demonstrates the usage of the `*=` operator:</span></span>

[!code-csharp-interactive[multiply and assign](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#MultiplyAndAssign)]

## <a name="operator-overloadability"></a><span data-ttu-id="3d2ec-109">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="3d2ec-109">Operator overloadability</span></span>

<span data-ttu-id="3d2ec-110">Pokud uživatelský typ [přetížení](../keywords/operator.md) [operátor násobení](multiplication-operator.md) `*`, operátor přiřazení násobení `*=` je implicitně přetížena.</span><span class="sxs-lookup"><span data-stu-id="3d2ec-110">If a user-defined type [overloads](../keywords/operator.md) the [multiplication operator](multiplication-operator.md) `*`, the multiplication assignment operator `*=` is implicitly overloaded.</span></span> <span data-ttu-id="3d2ec-111">Uživatelem definovaný typ nejde explicitně přetížit operátor přiřazení násobení.</span><span class="sxs-lookup"><span data-stu-id="3d2ec-111">A user-defined type cannot explicitly overload the multiplication assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3d2ec-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3d2ec-112">C# language specification</span></span>

<span data-ttu-id="3d2ec-113">Další informace najdete v tématu [složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3d2ec-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d2ec-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d2ec-114">See also</span></span>

- [<span data-ttu-id="3d2ec-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3d2ec-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3d2ec-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3d2ec-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3d2ec-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3d2ec-117">C# Operators</span></span>](index.md)
