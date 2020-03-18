---
title: Operátory přiřazení – odkaz jazyka C#
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 420b41f586a6980d40cf1171eef00dad37bf5abf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399250"
---
# <a name="assignment-operators-c-reference"></a><span data-ttu-id="04ba4-102">Operátory přiřazení (odkaz C# )</span><span class="sxs-lookup"><span data-stu-id="04ba4-102">Assignment operators (C# reference)</span></span>

<span data-ttu-id="04ba4-103">Operátor `=` přiřazení přiřadí hodnotu svého pravostranného operandu proměnné, [vlastnosti](../../programming-guide/classes-and-structs/properties.md)nebo prvku [indexeru](../../programming-guide/indexers/index.md) daného jeho levostranným operandem.</span><span class="sxs-lookup"><span data-stu-id="04ba4-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="04ba4-104">Výsledkem výrazu přiřazení je hodnota přiřazená levostranné operaci.</span><span class="sxs-lookup"><span data-stu-id="04ba4-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="04ba4-105">Typ pravostranného operandu musí být stejný jako typ levého operandu nebo k němu implicitně převoditelný.</span><span class="sxs-lookup"><span data-stu-id="04ba4-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="04ba4-106">Operátor `=` přiřazení je právo-asociativní, to znamená výraz formuláře</span><span class="sxs-lookup"><span data-stu-id="04ba4-106">The assignment operator `=` is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="04ba4-107">je vyhodnocována jako</span><span class="sxs-lookup"><span data-stu-id="04ba4-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="04ba4-108">Následující příklad ukazuje použití operátoru přiřazení s místní proměnnou, vlastností a indexerovým prvkem jako jeho levostranným operandem:</span><span class="sxs-lookup"><span data-stu-id="04ba4-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](snippets/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="04ba4-109">operátor přiřazení ref</span><span class="sxs-lookup"><span data-stu-id="04ba4-109">ref assignment operator</span></span>

<span data-ttu-id="04ba4-110">Počínaje C# 7.3, můžete použít operátor `= ref` přiřazení ref znovu přiřadit [ref místní](../keywords/ref.md#ref-locals) nebo [ref pouze místní](../keywords/ref.md#ref-readonly-locals) proměnné.</span><span class="sxs-lookup"><span data-stu-id="04ba4-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="04ba4-111">Následující příklad ukazuje použití operátoru přiřazení ref:</span><span class="sxs-lookup"><span data-stu-id="04ba4-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](snippets/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="04ba4-112">V případě operátoru přiřazení ref musí být oba jeho operandy stejného typu.</span><span class="sxs-lookup"><span data-stu-id="04ba4-112">In the case of the ref assignment operator, the both of its operands must be of the same type.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="04ba4-113">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="04ba4-113">Compound assignment</span></span>

<span data-ttu-id="04ba4-114">Pro binární `op`operátor , složený výraz přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="04ba4-114">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="04ba4-115">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="04ba4-115">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="04ba4-116">kromě `x` toho, že se vyhodnocuje pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="04ba4-116">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="04ba4-117">Složené přiřazení je podporováno [aritmetickými](arithmetic-operators.md#compound-assignment), [logickými logickými](boolean-logical-operators.md#compound-assignment)a [bitovými logickými operátory a operátory směn.](bitwise-and-shift-operators.md#compound-assignment)</span><span class="sxs-lookup"><span data-stu-id="04ba4-117">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="04ba4-118">Přiřazení null-coalescing</span><span class="sxs-lookup"><span data-stu-id="04ba4-118">Null-coalescing assignment</span></span>

<span data-ttu-id="04ba4-119">Počínaje C# 8.0, můžete použít null-coalescing `??=` přiřazení operátor přiřadit hodnotu jeho pravé operand u jeho levé operand pouze v `null`případě, že levé operandu vyhodnotí .</span><span class="sxs-lookup"><span data-stu-id="04ba4-119">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="04ba4-120">Pro více informací, viz [?? a ?? = článek operátorů.](null-coalescing-operator.md)</span><span class="sxs-lookup"><span data-stu-id="04ba4-120">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="04ba4-121">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="04ba4-121">Operator overloadability</span></span>

<span data-ttu-id="04ba4-122">Uživatelem definovaný typ nemůže [přetížit](operator-overloading.md) operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="04ba4-122">A user-defined type cannot [overload](operator-overloading.md) the assignment operator.</span></span> <span data-ttu-id="04ba4-123">Typ definovaný uživatelem však může definovat implicitní převod na jiný typ.</span><span class="sxs-lookup"><span data-stu-id="04ba4-123">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="04ba4-124">Tímto způsobem lze hodnotu uživatelem definovaného typu přiřadit proměnné, vlastnosti nebo prvku indexeru jiného typu.</span><span class="sxs-lookup"><span data-stu-id="04ba4-124">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="04ba4-125">Další informace naleznete v [tématu User-defined operátory převodu](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="04ba4-125">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

<span data-ttu-id="04ba4-126">Uživatelem definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="04ba4-126">A user-defined type cannot explicitly overload a compound assignment operator.</span></span> <span data-ttu-id="04ba4-127">Však pokud uživatelem definovaný typ přetížení `op`binární `op=` operátor , operátor, pokud existuje, je také implicitně přetížena.</span><span class="sxs-lookup"><span data-stu-id="04ba4-127">However, if a user-defined type overloads a binary operator `op`, the `op=` operator, if it exists, is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="04ba4-128">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="04ba4-128">C# language specification</span></span>

<span data-ttu-id="04ba4-129">Další informace naleznete v části [Operátory přiřazení](~/_csharplang/spec/expressions.md#assignment-operators) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="04ba4-129">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="04ba4-130">Další informace o operátoru `= ref`přiřazení ref naleznete v [poznámce k návrhu funkce](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="04ba4-130">For more information about the ref assignment operator `= ref`, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="04ba4-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="04ba4-131">See also</span></span>

- [<span data-ttu-id="04ba4-132">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="04ba4-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="04ba4-133">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="04ba4-133">C# operators</span></span>](index.md)
- [<span data-ttu-id="04ba4-134">klíčové slovo ref</span><span class="sxs-lookup"><span data-stu-id="04ba4-134">ref keyword</span></span>](../keywords/ref.md)
