---
title: '&amp; – Operátor (referenční dokumentace jazyka C#)'
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: a8f76ded0ef9f8e8099838a903d90f1695324991
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2018
ms.locfileid: "43510975"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="476c9-102">&amp; – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="476c9-102">&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="476c9-103">`&` Operátor je podporován ve dvou formách: operátor address-of unární nebo binární logický operátor.</span><span class="sxs-lookup"><span data-stu-id="476c9-103">The `&` operator is supported in two forms: a unary address-of operator or a binary logical operator.</span></span>

## <a name="unary-address-of-operator"></a><span data-ttu-id="476c9-104">Unární operátor address-of</span><span class="sxs-lookup"><span data-stu-id="476c9-104">Unary address-of operator</span></span>

<span data-ttu-id="476c9-105">Unární `&` operátor vrátí adresu svého operandu.</span><span class="sxs-lookup"><span data-stu-id="476c9-105">The unary `&` operator returns the address of its operand.</span></span> <span data-ttu-id="476c9-106">Další informace najdete v tématu [postupy: získávání adresy proměnné](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="476c9-106">For more information, see [How to: obtain the address of a variable](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span></span>

<span data-ttu-id="476c9-107">Operátor address-of `&` vyžaduje [nebezpečné](../keywords/unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="476c9-107">The address-of operator `&` requires [unsafe](../keywords/unsafe.md) context.</span></span>

## <a name="integer-logical-bitwise-and-operator"></a><span data-ttu-id="476c9-108">Celé číslo logického bitového operátoru AND</span><span class="sxs-lookup"><span data-stu-id="476c9-108">Integer logical bitwise AND operator</span></span>

<span data-ttu-id="476c9-109">Pro celočíselné typy `&` vypočítá logické bitové operace AND jeho operandy operátoru:</span><span class="sxs-lookup"><span data-stu-id="476c9-109">For integer types, the `&` operator computes the logical bitwise AND of its operands:</span></span>

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> <span data-ttu-id="476c9-110">V předchozím příkladu binární literály: [zavedený C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) a [rozšířené v C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span><span class="sxs-lookup"><span data-stu-id="476c9-110">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

<span data-ttu-id="476c9-111">Vzhledem k tomu, že operace s celočíselnými typy jsou obecně povoleny na typy výčtu `&` operátor také podporuje [výčtu](../keywords/enum.md) operandy.</span><span class="sxs-lookup"><span data-stu-id="476c9-111">Because operations on integer types are generally allowed on enumeration types, the `&` operator also supports [enum](../keywords/enum.md) operands.</span></span>

## <a name="boolean-logical-and-operator"></a><span data-ttu-id="476c9-112">Logická logického operátoru AND</span><span class="sxs-lookup"><span data-stu-id="476c9-112">Boolean logical AND operator</span></span>

<span data-ttu-id="476c9-113">Pro [bool](../keywords/bool.md) operandy, `&` operátor vypočítá logický operátor AND operandů.</span><span class="sxs-lookup"><span data-stu-id="476c9-113">For [bool](../keywords/bool.md) operands, the `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="476c9-114">Výsledek `x & y` je `true` Pokud mají oba `x` a `y` jsou `true`.</span><span class="sxs-lookup"><span data-stu-id="476c9-114">The result of `x & y` is `true` if both `x` and `y` are `true`.</span></span> <span data-ttu-id="476c9-115">V opačném případě je výsledek `false`.</span><span class="sxs-lookup"><span data-stu-id="476c9-115">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="476c9-116">`&` Operátor vyhodnotí oba operandy i v případě, že první operand vyhodnocen jako `false`tak, aby výsledek musí být `false` bez ohledu na hodnotu druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="476c9-116">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span> <span data-ttu-id="476c9-117">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="476c9-117">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

<span data-ttu-id="476c9-118">[Podmiňovací operátor AND](conditional-and-operator.md) `&&` také vypočítá logické a z operandů, ale je vyhodnocen jako druhý operand pouze v případě, že první operand vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="476c9-118">The [conditional AND operator](conditional-and-operator.md) `&&` also computes the logical AND of its operands, but evaluates the second operand only if the first operand evaluates to `true`.</span></span>

<span data-ttu-id="476c9-119">Pro operandy typu s možnou hodnotou Null bool, chování `&` operátor je konzistentní s logikou s hodnotou tři SQL.</span><span class="sxs-lookup"><span data-stu-id="476c9-119">For nullable bool operands, the behavior of the `&` operator is consistent with SQL's three-valued logic.</span></span> <span data-ttu-id="476c9-120">Další informace najdete v tématu [bool? typ](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) část [použití typů s povolenou hodnotou Null](../../programming-guide/nullable-types/using-nullable-types.md) článku.</span><span class="sxs-lookup"><span data-stu-id="476c9-120">For more information, see the [The bool? type](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="476c9-121">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="476c9-121">Operator overloadability</span></span>

<span data-ttu-id="476c9-122">Uživatelem definované typy lze [přetížení](../keywords/operator.md) binárního souboru `&` operátor.</span><span class="sxs-lookup"><span data-stu-id="476c9-122">User-defined types can [overload](../keywords/operator.md) the binary `&` operator.</span></span> <span data-ttu-id="476c9-123">Když binární soubor `&` je operátor přetížen, [operátor přiřazení AND](and-assignment-operator.md) `&=` je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="476c9-123">When a binary `&` operator is overloaded, the [AND assignment operator](and-assignment-operator.md) `&=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="476c9-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="476c9-124">C# language specification</span></span>

<span data-ttu-id="476c9-125">Další informace najdete v tématu [operátoru address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) a [logické operátory](~/_csharplang/spec/expressions.md#logical-operators) oddíly [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="476c9-125">For more information, see [The address-of operator](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) and [Logical operators](~/_csharplang/spec/expressions.md#logical-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="476c9-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="476c9-126">See also</span></span>

- [<span data-ttu-id="476c9-127">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="476c9-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="476c9-128">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="476c9-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="476c9-129">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="476c9-129">C# Operators</span></span>](index.md)
- [<span data-ttu-id="476c9-130">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="476c9-130">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="476c9-131">| – operátor</span><span class="sxs-lookup"><span data-stu-id="476c9-131">| operator</span></span>](or-operator.md)
- [<span data-ttu-id="476c9-132">^ – operátor</span><span class="sxs-lookup"><span data-stu-id="476c9-132">^ operator</span></span>](xor-operator.md)
- [<span data-ttu-id="476c9-133">~ – operátor</span><span class="sxs-lookup"><span data-stu-id="476c9-133">~ operator</span></span>](bitwise-complement-operator.md)
- [<span data-ttu-id="476c9-134">& & – operátor</span><span class="sxs-lookup"><span data-stu-id="476c9-134">&& operator</span></span>](conditional-and-operator.md)
