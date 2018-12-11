---
title: ~ – operátor (Referenční dokumentace jazyka C#)
ms.date: 11/05/2018
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 1bcb07c5639a098e3a8c566e92083ca0d48efb81
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153212"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4019b-102">~ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4019b-102">~ Operator (C# Reference)</span></span>

<span data-ttu-id="4019b-103">Operátor bitového doplňku `~` je unární operátor, který vytvoří bitový doplněk svého operandu přehozením každý bit.</span><span class="sxs-lookup"><span data-stu-id="4019b-103">The bitwise complement operator `~` is a unary operator that produces a bitwise complement of its operand by reversing each bit.</span></span> <span data-ttu-id="4019b-104">Podporují všechny typy celých čísel `~` operátor.</span><span class="sxs-lookup"><span data-stu-id="4019b-104">All integer types support the `~` operator.</span></span>

> [!NOTE]
> <span data-ttu-id="4019b-105">`~` Symbol se také používá k deklaraci finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="4019b-105">The `~` symbol is also used to declare finalizers.</span></span> <span data-ttu-id="4019b-106">Další informace najdete v tématu [finalizační metody](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="4019b-106">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

<span data-ttu-id="4019b-107">Následující příklad ukazuje použití `~` operátor:</span><span class="sxs-lookup"><span data-stu-id="4019b-107">The following example demonstrates the usage of the `~` operator:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseComplementExamples.cs#Example)]

> [!NOTE]
> <span data-ttu-id="4019b-108">V předchozím příkladu binární literály: [zavedený C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) a [rozšířené v C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span><span class="sxs-lookup"><span data-stu-id="4019b-108">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced  in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4019b-109">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="4019b-109">Operator overloadability</span></span>

<span data-ttu-id="4019b-110">Uživatelem definované typy lze [přetížení](../keywords/operator.md) `~` operátor.</span><span class="sxs-lookup"><span data-stu-id="4019b-110">User-defined types can [overload](../keywords/operator.md) the `~` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4019b-111">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4019b-111">C# language specification</span></span>

<span data-ttu-id="4019b-112">Další informace najdete v tématu [operátor bitového doplňku](~/_csharplang/spec/expressions.md#bitwise-complement-operator) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4019b-112">For more information, see the [Bitwise complement operator](~/_csharplang/spec/expressions.md#bitwise-complement-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4019b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4019b-113">See also</span></span>

- [<span data-ttu-id="4019b-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4019b-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4019b-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4019b-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4019b-116">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4019b-116">C# Operators</span></span>](index.md)
- [<span data-ttu-id="4019b-117">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="4019b-117">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)
- [<span data-ttu-id="4019b-118">& – operátor</span><span class="sxs-lookup"><span data-stu-id="4019b-118">& operator</span></span>](and-operator.md)
- [<span data-ttu-id="4019b-119">| – operátor</span><span class="sxs-lookup"><span data-stu-id="4019b-119">| operator</span></span>](or-operator.md)
- [<span data-ttu-id="4019b-120">^ – operátor</span><span class="sxs-lookup"><span data-stu-id="4019b-120">^ operator</span></span>](xor-operator.md)
