---
title: = – odkaz C# – operátor
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: f30b48fc6bd1e896658a7234a58409ea9a0f5e6f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69601952"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0800f-102">= – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="0800f-102">= operator (C# reference)</span></span>

<span data-ttu-id="0800f-103">Operátor `=` přiřazení přiřadí hodnotu jeho pravého operandu proměnné, [vlastnosti](../../programming-guide/classes-and-structs/properties.md)nebo prvku indexeru, který je dán [](../../programming-guide/indexers/index.md) jeho levým operandem.</span><span class="sxs-lookup"><span data-stu-id="0800f-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="0800f-104">Výsledkem výrazu přiřazení je hodnota přiřazená k levému operandu.</span><span class="sxs-lookup"><span data-stu-id="0800f-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="0800f-105">Typ operandu na pravé straně musí být stejný jako typ operandu na levé straně nebo implicitně převést na něj.</span><span class="sxs-lookup"><span data-stu-id="0800f-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="0800f-106">Operátor přiřazení je asociativní zprava, tj. výraz formuláře.</span><span class="sxs-lookup"><span data-stu-id="0800f-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="0800f-107">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="0800f-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="0800f-108">Následující příklad ukazuje použití operátoru přiřazení s lokální proměnnou, vlastností a prvkem indexeru jako jeho levý operand:</span><span class="sxs-lookup"><span data-stu-id="0800f-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="0800f-109">operátor přiřazení ref</span><span class="sxs-lookup"><span data-stu-id="0800f-109">ref assignment operator</span></span>

<span data-ttu-id="0800f-110">Počínaje C# 7,3 můžete použít operátor `= ref` přiřazení ref k opětovnému přiřazení místní proměnné typu [ref](../keywords/ref.md#ref-locals) nebo [ref jen pro čtení](../keywords/ref.md#ref-readonly-locals) .</span><span class="sxs-lookup"><span data-stu-id="0800f-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="0800f-111">Následující příklad ukazuje použití operátoru přiřazení ref:</span><span class="sxs-lookup"><span data-stu-id="0800f-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="0800f-112">V případě operátoru přiřazení ref musí být typ obou operandů stejný.</span><span class="sxs-lookup"><span data-stu-id="0800f-112">In the case of the ref assignment operator, the type of both its operands must be the same.</span></span>

<span data-ttu-id="0800f-113">Další informace najdete v poznámkách k [návrhu funkcí](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="0800f-113">For more information, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="0800f-114">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="0800f-114">Compound assignment</span></span>

<span data-ttu-id="0800f-115">Pro binární operátor `op`, výraz složeného přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="0800f-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="0800f-116">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="0800f-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="0800f-117">s výjimkou, že `x` je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="0800f-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="0800f-118">Složené přiřazení je podporováno [aritmetickými](arithmetic-operators.md#compound-assignment)a [](boolean-logical-operators.md#compound-assignment)logickými logickými a operátory [SHIFT a Shift](bitwise-and-shift-operators.md#compound-assignment) .</span><span class="sxs-lookup"><span data-stu-id="0800f-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="0800f-119">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="0800f-119">Operator overloadability</span></span>

<span data-ttu-id="0800f-120">Uživatelsky definovaný typ nemůže přetížit operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="0800f-120">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="0800f-121">Uživatelsky definovaný typ však může definovat implicitní převod na jiný typ.</span><span class="sxs-lookup"><span data-stu-id="0800f-121">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="0800f-122">Tímto způsobem lze hodnotu uživatelsky definovaného typu přiřadit proměnné, vlastnosti nebo prvku indexeru jiného typu.</span><span class="sxs-lookup"><span data-stu-id="0800f-122">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="0800f-123">Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="0800f-123">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0800f-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0800f-124">C# language specification</span></span>

<span data-ttu-id="0800f-125">Další informace naleznete v části [operátory přiřazení](~/_csharplang/spec/expressions.md#assignment-operators) ve [ C# specifikaci jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0800f-125">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0800f-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0800f-126">See also</span></span>

- [<span data-ttu-id="0800f-127">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="0800f-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0800f-128">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0800f-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="0800f-129">ref – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="0800f-129">ref keyword</span></span>](../keywords/ref.md)
