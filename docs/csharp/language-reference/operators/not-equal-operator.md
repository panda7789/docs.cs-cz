---
title: '! = – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 939b5664dba4345e62a43fb2f8d4d5379659d6aa
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610174"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6cd58-102">!= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6cd58-102">!= Operator (C# Reference)</span></span>

<span data-ttu-id="6cd58-103">Operátor nerovnosti `!=` vrátí `true` Pokud nejsou stejné, jeho operandy `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="6cd58-103">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="6cd58-104">Pro operandy [předdefinovaných typů](../keywords/built-in-types-table.md), výraz `x != y` vytváří stejný výsledek jako výraz `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="6cd58-104">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="6cd58-105">Další informace najdete v tématu [== – operátor](equality-comparison-operator.md) článku.</span><span class="sxs-lookup"><span data-stu-id="6cd58-105">For more information, see the [== Operator](equality-comparison-operator.md) article.</span></span>

<span data-ttu-id="6cd58-106">Následující příklad ukazuje použití `!=` operátor:</span><span class="sxs-lookup"><span data-stu-id="6cd58-106">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="6cd58-107">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="6cd58-107">Operator overloadability</span></span>

<span data-ttu-id="6cd58-108">Uživatelem definované typy lze [přetížení](../keywords/operator.md) `!=` operátor.</span><span class="sxs-lookup"><span data-stu-id="6cd58-108">User-defined types can [overload](../keywords/operator.md) the `!=` operator.</span></span> <span data-ttu-id="6cd58-109">Pokud typ přetížení operátor nerovnosti `!=`, musíte také přetížit [operátor rovnosti](equality-comparison-operator.md) `==`.</span><span class="sxs-lookup"><span data-stu-id="6cd58-109">If a type overloads the inequality operator `!=`, it must also overload the [equality operator](equality-comparison-operator.md) `==`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6cd58-110">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6cd58-110">C# language specification</span></span>

<span data-ttu-id="6cd58-111">Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="6cd58-111">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6cd58-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6cd58-112">See also</span></span>

- [<span data-ttu-id="6cd58-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6cd58-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6cd58-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6cd58-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6cd58-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6cd58-115">C# Operators</span></span>](index.md)
- [<span data-ttu-id="6cd58-116">Porovnání rovnosti</span><span class="sxs-lookup"><span data-stu-id="6cd58-116">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
