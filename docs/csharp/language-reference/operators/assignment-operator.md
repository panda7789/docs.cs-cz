---
title: Operátory přiřazení – reference jazyka C#
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 7b4f3b3f4d6b697903461f08435552f2df36bfe4
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916928"
---
# <a name="assignment-operators-c-reference"></a><span data-ttu-id="3299e-102">Operátory přiřazení (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3299e-102">Assignment operators (C# reference)</span></span>

<span data-ttu-id="3299e-103">Operátor přiřazení `=` přiřadí hodnotu jeho pravého operandu proměnné, [vlastnosti](../../programming-guide/classes-and-structs/properties.md)nebo prvku [indexeru](../../programming-guide/indexers/index.md) , který je dán jeho levým operandem.</span><span class="sxs-lookup"><span data-stu-id="3299e-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="3299e-104">Výsledkem výrazu přiřazení je hodnota přiřazená k levému operandu.</span><span class="sxs-lookup"><span data-stu-id="3299e-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="3299e-105">Typ operandu na pravé straně musí být stejný jako typ operandu na levé straně nebo implicitně převést na něj.</span><span class="sxs-lookup"><span data-stu-id="3299e-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="3299e-106">Operátor přiřazení `=` je asociativní zprava, tj. výraz formuláře.</span><span class="sxs-lookup"><span data-stu-id="3299e-106">The assignment operator `=` is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="3299e-107">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="3299e-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="3299e-108">Následující příklad ukazuje použití operátoru přiřazení s lokální proměnnou, vlastností a prvkem indexeru jako jeho levý operand:</span><span class="sxs-lookup"><span data-stu-id="3299e-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](snippets/shared/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="3299e-109">operátor přiřazení ref</span><span class="sxs-lookup"><span data-stu-id="3299e-109">ref assignment operator</span></span>

<span data-ttu-id="3299e-110">Počínaje jazykem C# 7,3 můžete použít operátor přiřazení odkazu `= ref` k opětovnému přiřazení místní proměnné typu [ref](../keywords/ref.md#ref-locals) nebo [ref jen pro čtení](../keywords/ref.md#ref-readonly-locals) .</span><span class="sxs-lookup"><span data-stu-id="3299e-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="3299e-111">Následující příklad ukazuje použití operátoru přiřazení ref:</span><span class="sxs-lookup"><span data-stu-id="3299e-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](snippets/shared/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="3299e-112">V případě operátoru přiřazení odkazu musí být oba operandy stejného typu.</span><span class="sxs-lookup"><span data-stu-id="3299e-112">In the case of the ref assignment operator, the both of its operands must be of the same type.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="3299e-113">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="3299e-113">Compound assignment</span></span>

<span data-ttu-id="3299e-114">Pro binární operátor `op` , výraz složeného přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="3299e-114">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="3299e-115">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="3299e-115">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="3299e-116">s výjimkou, že `x` je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="3299e-116">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="3299e-117">Složené přiřazení je podporováno [aritmetickými](arithmetic-operators.md#compound-assignment)a [logickými logickými](boolean-logical-operators.md#compound-assignment)a operátory [SHIFT a Shift](bitwise-and-shift-operators.md#compound-assignment) .</span><span class="sxs-lookup"><span data-stu-id="3299e-117">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="3299e-118">Přiřazení slučování s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="3299e-118">Null-coalescing assignment</span></span>

<span data-ttu-id="3299e-119">Počínaje jazykem C# 8,0 můžete použít operátor přiřazení s použitím hodnoty null `??=` k přiřazení hodnoty jeho pravého operandu k jeho levému operandu pouze v případě, že je operand na levé straně vyhodnocen `null` .</span><span class="sxs-lookup"><span data-stu-id="3299e-119">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="3299e-120">Další informace najdete v tématu [?? a?? =](null-coalescing-operator.md) – článek o operátorech</span><span class="sxs-lookup"><span data-stu-id="3299e-120">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="3299e-121">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="3299e-121">Operator overloadability</span></span>

<span data-ttu-id="3299e-122">Uživatelsky definovaný typ nemůže [přetížit](operator-overloading.md) operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3299e-122">A user-defined type cannot [overload](operator-overloading.md) the assignment operator.</span></span> <span data-ttu-id="3299e-123">Uživatelsky definovaný typ však může definovat implicitní převod na jiný typ.</span><span class="sxs-lookup"><span data-stu-id="3299e-123">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="3299e-124">Tímto způsobem lze hodnotu uživatelsky definovaného typu přiřadit proměnné, vlastnosti nebo prvku indexeru jiného typu.</span><span class="sxs-lookup"><span data-stu-id="3299e-124">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="3299e-125">Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="3299e-125">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

<span data-ttu-id="3299e-126">Uživatelsky definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3299e-126">A user-defined type cannot explicitly overload a compound assignment operator.</span></span> <span data-ttu-id="3299e-127">Pokud však uživatelsky definovaný typ přetěžuje binární operátor `op` , `op=` je operátor, pokud existuje, také implicitně přetížený.</span><span class="sxs-lookup"><span data-stu-id="3299e-127">However, if a user-defined type overloads a binary operator `op`, the `op=` operator, if it exists, is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3299e-128">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3299e-128">C# language specification</span></span>

<span data-ttu-id="3299e-129">Další informace naleznete v části [operátory přiřazení](~/_csharplang/spec/expressions.md#assignment-operators) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="3299e-129">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="3299e-130">Další informace o operátoru přiřazení odkazu `= ref` najdete v [poznámce k návrhu funkcí](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="3299e-130">For more information about the ref assignment operator `= ref`, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3299e-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="3299e-131">See also</span></span>

- [<span data-ttu-id="3299e-132">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="3299e-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3299e-133">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="3299e-133">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="3299e-134">ref – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="3299e-134">ref keyword</span></span>](../keywords/ref.md)
