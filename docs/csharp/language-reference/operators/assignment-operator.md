---
title: = – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 85182acb84ea79cb00a9edb315c3954f440305f4
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758364"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e34ff-102">= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e34ff-102">= Operator (C# Reference)</span></span>

<span data-ttu-id="e34ff-103">Operátor přiřazení `=` hodnota jeho operandu pravé přiřadí proměnné, [vlastnost](../../programming-guide/classes-and-structs/properties.md), nebo [indexer](../../../csharp/programming-guide/indexers/index.md) element Dal jeho levý operand.</span><span class="sxs-lookup"><span data-stu-id="e34ff-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../../csharp/programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="e34ff-104">Výsledkem výrazu přiřazení je hodnota přiřazená k levý operand.</span><span class="sxs-lookup"><span data-stu-id="e34ff-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="e34ff-105">Typ operandu pravé musí být stejný jako typ levý operand nebo implicitně převeditelné na ni.</span><span class="sxs-lookup"><span data-stu-id="e34ff-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="e34ff-106">Operátor přiřazení je asociativní zprava, to znamená, výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="e34ff-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="e34ff-107">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="e34ff-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="e34ff-108">Následující příklad ukazuje použití operátoru přiřazení k přiřazení hodnot k místní proměnné, vlastnosti a elementu indexeru:</span><span class="sxs-lookup"><span data-stu-id="e34ff-108">The following example demonstrates the usage of the assignment operator to assign values to a local variable, a property, and an indexer element:</span></span>

[!code-csharp-interactive[assignment operator](~/samples/csharp/language-reference/operators/AssignmentExamples.cs#Assignments)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="e34ff-109">operátoru přiřazení odkazu</span><span class="sxs-lookup"><span data-stu-id="e34ff-109">ref assignment operator</span></span>

<span data-ttu-id="e34ff-110">Počínaje C# 7.3, můžete pomocí operátoru přiřazení odkazu `= ref` přiřazení [lokální proměnná podle odkazu](../keywords/ref.md#ref-locals) nebo [lokální proměnná podle odkazu jen pro čtení](../keywords/ref.md#ref-readonly-locals) proměnné.</span><span class="sxs-lookup"><span data-stu-id="e34ff-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="e34ff-111">Následující příklad ukazuje použití operátoru přiřazení odkazu:</span><span class="sxs-lookup"><span data-stu-id="e34ff-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentExamples.cs#RefAssignment)]

<span data-ttu-id="e34ff-112">V případě operátoru přiřazení odkazu typ levého operandu a pravý operand musí být stejné.</span><span class="sxs-lookup"><span data-stu-id="e34ff-112">In the case of the ref assignment operator, the type of the left operand and the right operand must be the same.</span></span>

<span data-ttu-id="e34ff-113">Další informace najdete v tématu [Poznámka návrh funkce](../../../../_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="e34ff-113">For more information, see the [feature proposal note](../../../../_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="e34ff-114">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="e34ff-114">Operator overloadability</span></span>

<span data-ttu-id="e34ff-115">Uživatelem definovaný typ nejde přetížit operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="e34ff-115">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="e34ff-116">Uživatelem definovaný typ však můžete definovat implicitní převod na jiného typu.</span><span class="sxs-lookup"><span data-stu-id="e34ff-116">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="e34ff-117">Tímto způsobem hodnota uživatelem definovaného typu lze přiřadit k proměnné, vlastnosti nebo elementu indexeru jiného typu.</span><span class="sxs-lookup"><span data-stu-id="e34ff-117">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="e34ff-118">Další informace najdete v tématu [implicitní](../keywords/implicit.md) článku – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e34ff-118">For more information, see the [implicit](../keywords/implicit.md) keyword article.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e34ff-119">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e34ff-119">C# language specification</span></span>

<span data-ttu-id="e34ff-120">Další informace najdete v tématu [jednoduché přiřazení](~/_csharplang/spec/expressions.md#simple-assignment) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e34ff-120">For more information, see the [Simple assignment](~/_csharplang/spec/expressions.md#simple-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e34ff-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e34ff-121">See also</span></span>

- [<span data-ttu-id="e34ff-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e34ff-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e34ff-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e34ff-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e34ff-124">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e34ff-124">C# Operators</span></span>](index.md)
- [<span data-ttu-id="e34ff-125">ref keyword</span><span class="sxs-lookup"><span data-stu-id="e34ff-125">ref keyword</span></span>](../keywords/ref.md)
