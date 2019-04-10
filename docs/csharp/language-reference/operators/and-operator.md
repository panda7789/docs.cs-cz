---
title: '&amp; Operator - C# odkaz'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 67d60709e1c6c76071ecfb7aac74c83dec6f372a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310041"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="4c13b-102">&amp; – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4c13b-102">&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="4c13b-103">`&` Operátor je podporován ve dvou formách: operátor address-of unární nebo binární logický operátor.</span><span class="sxs-lookup"><span data-stu-id="4c13b-103">The `&` operator is supported in two forms: a unary address-of operator or a binary logical operator.</span></span>

## <a name="unary-address-of-operator"></a><span data-ttu-id="4c13b-104">Unární operátor address-of</span><span class="sxs-lookup"><span data-stu-id="4c13b-104">Unary address-of operator</span></span>

<span data-ttu-id="4c13b-105">Unární `&` operátor vrátí adresu svého operandu.</span><span class="sxs-lookup"><span data-stu-id="4c13b-105">The unary `&` operator returns the address of its operand.</span></span> <span data-ttu-id="4c13b-106">Další informace najdete v tématu [postupy: získávání adresy proměnné](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="4c13b-106">For more information, see [How to: obtain the address of a variable](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span></span>

<span data-ttu-id="4c13b-107">Operátor address-of `&` vyžaduje [nebezpečné](../keywords/unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="4c13b-107">The address-of operator `&` requires [unsafe](../keywords/unsafe.md) context.</span></span>

## <a name="integer-logical-bitwise-and-operator"></a><span data-ttu-id="4c13b-108">Celé číslo logického bitového operátoru AND</span><span class="sxs-lookup"><span data-stu-id="4c13b-108">Integer logical bitwise AND operator</span></span>

<span data-ttu-id="4c13b-109">Pro celočíselné typy `&` vypočítá logické bitové operace AND jeho operandy operátoru:</span><span class="sxs-lookup"><span data-stu-id="4c13b-109">For integer types, the `&` operator computes the logical bitwise AND of its operands:</span></span>

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> <span data-ttu-id="4c13b-110">V předchozím příkladu binární literály: [zavedený C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) a [rozšířené v C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span><span class="sxs-lookup"><span data-stu-id="4c13b-110">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

<span data-ttu-id="4c13b-111">Vzhledem k tomu, že operace s celočíselnými typy jsou obecně povoleny na typy výčtu `&` operátor také podporuje [výčtu](../keywords/enum.md) operandy.</span><span class="sxs-lookup"><span data-stu-id="4c13b-111">Because operations on integer types are generally allowed on enumeration types, the `&` operator also supports [enum](../keywords/enum.md) operands.</span></span>

## <a name="boolean-logical-and-operator"></a><span data-ttu-id="4c13b-112">Logická logického operátoru AND</span><span class="sxs-lookup"><span data-stu-id="4c13b-112">Boolean logical AND operator</span></span>

<span data-ttu-id="4c13b-113">Pro [bool](../keywords/bool.md) operandy, `&` operátor vypočítá logický operátor AND operandů.</span><span class="sxs-lookup"><span data-stu-id="4c13b-113">For [bool](../keywords/bool.md) operands, the `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="4c13b-114">Výsledek `x & y` je `true` Pokud mají oba `x` a `y` jsou `true`.</span><span class="sxs-lookup"><span data-stu-id="4c13b-114">The result of `x & y` is `true` if both `x` and `y` are `true`.</span></span> <span data-ttu-id="4c13b-115">V opačném případě je výsledek `false`.</span><span class="sxs-lookup"><span data-stu-id="4c13b-115">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="4c13b-116">`&` Operátor vyhodnotí oba operandy i v případě, že první operand vyhodnocen jako `false`tak, aby výsledek musí být `false` bez ohledu na hodnotu druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="4c13b-116">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span> <span data-ttu-id="4c13b-117">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="4c13b-117">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

<span data-ttu-id="4c13b-118">[Podmiňovací operátor AND](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` také vypočítá logický operátor a jeho operandy, ale nebude vyhodnocení druhého operandu, jestli je první operand vyhodnocen jako `false`.</span><span class="sxs-lookup"><span data-stu-id="4c13b-118">The [conditional AND operator](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="4c13b-119">Pro operandy typu s možnou hodnotou Null bool, chování `&` operátor je konzistentní s logikou s hodnotou tři SQL.</span><span class="sxs-lookup"><span data-stu-id="4c13b-119">For nullable bool operands, the behavior of the `&` operator is consistent with SQL's three-valued logic.</span></span> <span data-ttu-id="4c13b-120">Další informace najdete v tématu [logické operátory s povolenou hodnotou Null logická](boolean-logical-operators.md#nullable-boolean-logical-operators) část [logické logické operátory](boolean-logical-operators.md) článku.</span><span class="sxs-lookup"><span data-stu-id="4c13b-120">For more information, see the [Nullable Boolean logical operators](boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](boolean-logical-operators.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4c13b-121">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="4c13b-121">Operator overloadability</span></span>

<span data-ttu-id="4c13b-122">Uživatelem definované typy lze [přetížení](../keywords/operator.md) binárního souboru `&` operátor.</span><span class="sxs-lookup"><span data-stu-id="4c13b-122">User-defined types can [overload](../keywords/operator.md) the binary `&` operator.</span></span> <span data-ttu-id="4c13b-123">Když binární soubor `&` je operátor přetížen, [operátor přiřazení AND](and-assignment-operator.md) `&=` je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="4c13b-123">When a binary `&` operator is overloaded, the [AND assignment operator](and-assignment-operator.md) `&=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4c13b-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4c13b-124">C# language specification</span></span>

<span data-ttu-id="4c13b-125">Další informace najdete v tématu [operátoru address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) a [logické operátory](~/_csharplang/spec/expressions.md#logical-operators) oddíly [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4c13b-125">For more information, see [The address-of operator](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) and [Logical operators](~/_csharplang/spec/expressions.md#logical-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c13b-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c13b-126">See also</span></span>

- [<span data-ttu-id="4c13b-127">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4c13b-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4c13b-128">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4c13b-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4c13b-129">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4c13b-129">C# Operators</span></span>](index.md)
- [<span data-ttu-id="4c13b-130">Logická logické operátory</span><span class="sxs-lookup"><span data-stu-id="4c13b-130">Boolean logical operators</span></span>](boolean-logical-operators.md)
- [<span data-ttu-id="4c13b-131">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="4c13b-131">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="4c13b-132">| operátor</span><span class="sxs-lookup"><span data-stu-id="4c13b-132">| operator</span></span>](or-operator.md)
- [<span data-ttu-id="4c13b-133">^ – operátor</span><span class="sxs-lookup"><span data-stu-id="4c13b-133">^ operator</span></span>](xor-operator.md)
- [<span data-ttu-id="4c13b-134">~ – operátor</span><span class="sxs-lookup"><span data-stu-id="4c13b-134">~ operator</span></span>](bitwise-complement-operator.md)
