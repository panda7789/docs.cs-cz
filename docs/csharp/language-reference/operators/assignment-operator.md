---
title: = – odkaz C# – operátor
ms.custom: seodec18
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: a450a55524f33f4f06ed077aba864e8f641a458d
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924662"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="26bb4-102">= – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="26bb4-102">= operator (C# reference)</span></span>

<span data-ttu-id="26bb4-103">Operátor `=` přiřazení přiřadí hodnotu jeho pravého operandu proměnné, [vlastnosti](../../programming-guide/classes-and-structs/properties.md)nebo prvku [indexeru](../../programming-guide/indexers/index.md) , který je dán jeho levým operandem.</span><span class="sxs-lookup"><span data-stu-id="26bb4-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="26bb4-104">Výsledkem výrazu přiřazení je hodnota přiřazená k levému operandu.</span><span class="sxs-lookup"><span data-stu-id="26bb4-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="26bb4-105">Typ operandu na pravé straně musí být stejný jako typ operandu na levé straně nebo implicitně převést na něj.</span><span class="sxs-lookup"><span data-stu-id="26bb4-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="26bb4-106">Operátor přiřazení je asociativní zprava, tj. výraz formuláře.</span><span class="sxs-lookup"><span data-stu-id="26bb4-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="26bb4-107">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="26bb4-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="26bb4-108">Následující příklad ukazuje použití operátoru přiřazení s lokální proměnnou, vlastností a prvkem indexeru jako jeho levý operand:</span><span class="sxs-lookup"><span data-stu-id="26bb4-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="26bb4-109">operátor přiřazení ref</span><span class="sxs-lookup"><span data-stu-id="26bb4-109">ref assignment operator</span></span>

<span data-ttu-id="26bb4-110">Počínaje C# 7,3 můžete použít operátor `= ref` přiřazení ref k opětovnému přiřazení místní proměnné typu [ref](../keywords/ref.md#ref-locals) nebo [ref jen pro čtení](../keywords/ref.md#ref-readonly-locals) .</span><span class="sxs-lookup"><span data-stu-id="26bb4-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="26bb4-111">Následující příklad ukazuje použití operátoru přiřazení ref:</span><span class="sxs-lookup"><span data-stu-id="26bb4-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="26bb4-112">V případě operátoru přiřazení ref musí být typ obou operandů stejný.</span><span class="sxs-lookup"><span data-stu-id="26bb4-112">In the case of the ref assignment operator, the type of both its operands must be the same.</span></span>

<span data-ttu-id="26bb4-113">Další informace najdete v [poznámkách k návrhu funkcí](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="26bb4-113">For more information, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="26bb4-114">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="26bb4-114">Compound assignment</span></span>

<span data-ttu-id="26bb4-115">Pro binární operátor `op`, výraz složeného přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="26bb4-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="26bb4-116">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="26bb4-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="26bb4-117">s výjimkou, že `x` je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="26bb4-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="26bb4-118">Složené přiřazení je podporováno [aritmetickými](arithmetic-operators.md#compound-assignment)a [logickými logickými](boolean-logical-operators.md#compound-assignment)a operátory [SHIFT a Shift](bitwise-and-shift-operators.md#compound-assignment) .</span><span class="sxs-lookup"><span data-stu-id="26bb4-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="26bb4-119">Přiřazení slučování s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="26bb4-119">Null-coalescing assignment</span></span>

<span data-ttu-id="26bb4-120">Počínaje C# 8,0 můžete použít operátor `??=` přiřazení s použitím hodnoty null k přiřazení hodnoty jeho pravého operandu k levému operandu pouze v případě, že je `null`operand na levé straně vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="26bb4-120">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="26bb4-121">Další informace najdete v tématu [?? a?? =](null-coalescing-operator.md) – článek o operátorech</span><span class="sxs-lookup"><span data-stu-id="26bb4-121">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="26bb4-122">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="26bb4-122">Operator overloadability</span></span>

<span data-ttu-id="26bb4-123">Uživatelsky definovaný typ nemůže přetížit operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="26bb4-123">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="26bb4-124">Uživatelsky definovaný typ však může definovat implicitní převod na jiný typ.</span><span class="sxs-lookup"><span data-stu-id="26bb4-124">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="26bb4-125">Tímto způsobem lze hodnotu uživatelsky definovaného typu přiřadit proměnné, vlastnosti nebo prvku indexeru jiného typu.</span><span class="sxs-lookup"><span data-stu-id="26bb4-125">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="26bb4-126">Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="26bb4-126">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="26bb4-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="26bb4-127">C# language specification</span></span>

<span data-ttu-id="26bb4-128">Další informace naleznete v části [operátory přiřazení](~/_csharplang/spec/expressions.md#assignment-operators) ve [ C# specifikaci jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="26bb4-128">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="26bb4-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26bb4-129">See also</span></span>

- [<span data-ttu-id="26bb4-130">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="26bb4-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="26bb4-131">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="26bb4-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="26bb4-132">ref – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="26bb4-132">ref keyword</span></span>](../keywords/ref.md)
