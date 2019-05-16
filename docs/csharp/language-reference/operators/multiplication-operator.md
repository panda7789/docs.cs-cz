---
title: '* Operator - C# odkaz'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 76ba0d9ac9ea6a2859dda31988588c3b3dd21807
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632921"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="bfe81-102">\* – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="bfe81-102">\* operator (C# Reference)</span></span>

<span data-ttu-id="bfe81-103">`*` Operátor je podporován ve dvou formách: Unární operátor dereference ukazatele nebo operátor binárního násobení.</span><span class="sxs-lookup"><span data-stu-id="bfe81-103">The `*` operator is supported in two forms: a unary pointer indirection operator or a binary multiplication operator.</span></span>

## <a name="pointer-indirection-operator"></a><span data-ttu-id="bfe81-104">Operátor dereference ukazatele</span><span class="sxs-lookup"><span data-stu-id="bfe81-104">Pointer indirection operator</span></span>

<span data-ttu-id="bfe81-105">Použít unární `*` operátoru získat proměnnou, na kterou ukazuje operand typu ukazatele.</span><span class="sxs-lookup"><span data-stu-id="bfe81-105">Use the unary `*` operator to obtain the variable to which an operand of a pointer type points.</span></span> <span data-ttu-id="bfe81-106">Další informace najdete v tématu [postupy: získávání hodnoty proměnné ukazatele](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md).</span><span class="sxs-lookup"><span data-stu-id="bfe81-106">For more information, see [How to: obtain the value of a pointer variable](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md).</span></span>

<span data-ttu-id="bfe81-107">Operátor dereference ukazatele `*` vyžaduje [nebezpečné](../keywords/unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="bfe81-107">The pointer indirection operator `*` requires [unsafe](../keywords/unsafe.md) context.</span></span>

## <a name="multiplication-operator"></a><span data-ttu-id="bfe81-108">Operátor násobení</span><span class="sxs-lookup"><span data-stu-id="bfe81-108">Multiplication operator</span></span>

<span data-ttu-id="bfe81-109">Pro číselné typy `*` operátor vypočítá součin z operandů:</span><span class="sxs-lookup"><span data-stu-id="bfe81-109">For numeric types, the `*` operator computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#Multiply)]

## <a name="operator-overloadability"></a><span data-ttu-id="bfe81-110">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="bfe81-110">Operator overloadability</span></span>

<span data-ttu-id="bfe81-111">Uživatelem definované typy lze [přetížení](../keywords/operator.md) binární soubor `*` operátor.</span><span class="sxs-lookup"><span data-stu-id="bfe81-111">User-defined types can [overload](../keywords/operator.md) a binary `*` operator.</span></span> <span data-ttu-id="bfe81-112">Když binární soubor `*` je operátor přetížen, [operátor přiřazení násobení](multiplication-assignment-operator.md) `*=` je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="bfe81-112">When a binary `*` operator is overloaded, the [multiplication assignment operator](multiplication-assignment-operator.md) `*=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bfe81-113">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bfe81-113">C# language specification</span></span>

<span data-ttu-id="bfe81-114">Další informace najdete v tématu [dereferenci ukazatele](~/_csharplang/spec/unsafe-code.md#pointer-indirection) a [operátor násobení](~/_csharplang/spec/expressions.md#multiplication-operator) oddíly [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="bfe81-114">For more information, see the [Pointer indirection](~/_csharplang/spec/unsafe-code.md#pointer-indirection) and [Multiplication operator](~/_csharplang/spec/expressions.md#multiplication-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bfe81-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bfe81-115">See also</span></span>

- [<span data-ttu-id="bfe81-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bfe81-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bfe81-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bfe81-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bfe81-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bfe81-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="bfe81-119">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="bfe81-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
