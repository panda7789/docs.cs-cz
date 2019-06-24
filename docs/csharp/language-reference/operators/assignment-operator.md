---
title: = – operátor - C# odkaz
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: ef9c9bab5c1cebb06edf934254507180e2197349
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306568"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="acc6d-102">= – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="acc6d-102">= operator (C# reference)</span></span>

<span data-ttu-id="acc6d-103">Operátor přiřazení `=` hodnota jeho operandu pravé přiřadí proměnné, [vlastnost](../../programming-guide/classes-and-structs/properties.md), nebo [indexer](../../../csharp/programming-guide/indexers/index.md) element Dal jeho levý operand.</span><span class="sxs-lookup"><span data-stu-id="acc6d-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../../csharp/programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="acc6d-104">Výsledkem výrazu přiřazení je hodnota přiřazená k levý operand.</span><span class="sxs-lookup"><span data-stu-id="acc6d-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="acc6d-105">Typ operandu pravé musí být stejný jako typ levý operand nebo implicitně převeditelné na ni.</span><span class="sxs-lookup"><span data-stu-id="acc6d-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="acc6d-106">Operátor přiřazení je asociativní zprava, to znamená, výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="acc6d-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="acc6d-107">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="acc6d-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="acc6d-108">Následující příklad ukazuje použití operátoru přiřazení s místní proměnná, vlastnost a indexer elementu jako jeho operand na levé straně:</span><span class="sxs-lookup"><span data-stu-id="acc6d-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="acc6d-109">operátoru přiřazení odkazu</span><span class="sxs-lookup"><span data-stu-id="acc6d-109">ref assignment operator</span></span>

<span data-ttu-id="acc6d-110">Počínaje C# 7.3, můžete pomocí operátoru přiřazení odkazu `= ref` přiřazení [lokální proměnná podle odkazu](../keywords/ref.md#ref-locals) nebo [lokální proměnná podle odkazu jen pro čtení](../keywords/ref.md#ref-readonly-locals) proměnné.</span><span class="sxs-lookup"><span data-stu-id="acc6d-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="acc6d-111">Následující příklad ukazuje použití operátoru přiřazení odkazu:</span><span class="sxs-lookup"><span data-stu-id="acc6d-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="acc6d-112">V případě operátoru přiřazení odkazu typ i jeho operandy musí být stejné.</span><span class="sxs-lookup"><span data-stu-id="acc6d-112">In the case of the ref assignment operator, the type of both its operands must be the same.</span></span>

<span data-ttu-id="acc6d-113">Další informace najdete v tématu [Poznámka návrh funkce](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="acc6d-113">For more information, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="acc6d-114">Složené přiřazení</span><span class="sxs-lookup"><span data-stu-id="acc6d-114">Compound assignment</span></span>

<span data-ttu-id="acc6d-115">Pro binární operátor `op`, výraz složeného přiřazení formuláře</span><span class="sxs-lookup"><span data-stu-id="acc6d-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="acc6d-116">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="acc6d-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="acc6d-117">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="acc6d-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="acc6d-118">Složené přiřazení podporuje [aritmetické](arithmetic-operators.md#compound-assignment), [logický datový typ Boolean](boolean-logical-operators.md#compound-assignment), a [bitové logické a shift](bitwise-and-shift-operators.md#compound-assignment) operátory.</span><span class="sxs-lookup"><span data-stu-id="acc6d-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="acc6d-119">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="acc6d-119">Operator overloadability</span></span>

<span data-ttu-id="acc6d-120">Uživatelem definovaný typ nejde přetížit operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="acc6d-120">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="acc6d-121">Uživatelem definovaný typ však můžete definovat implicitní převod na jiného typu.</span><span class="sxs-lookup"><span data-stu-id="acc6d-121">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="acc6d-122">Tímto způsobem hodnota uživatelem definovaného typu lze přiřadit k proměnné, vlastnosti nebo elementu indexeru jiného typu.</span><span class="sxs-lookup"><span data-stu-id="acc6d-122">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="acc6d-123">Další informace najdete v tématu [implicitní](../keywords/implicit.md) článku – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="acc6d-123">For more information, see the [implicit](../keywords/implicit.md) keyword article.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="acc6d-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="acc6d-124">C# language specification</span></span>

<span data-ttu-id="acc6d-125">Další informace najdete v tématu [operátory přiřazení](~/_csharplang/spec/expressions.md#assignment-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="acc6d-125">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="acc6d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acc6d-126">See also</span></span>

- [<span data-ttu-id="acc6d-127">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="acc6d-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="acc6d-128">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="acc6d-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="acc6d-129">ref keyword</span><span class="sxs-lookup"><span data-stu-id="acc6d-129">ref keyword</span></span>](../keywords/ref.md)
