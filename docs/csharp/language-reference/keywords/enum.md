---
title: enum keyword - C# Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 639a3a01c9c4da13e0212bd0230acbd2af170b25
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428518"
---
# <a name="enum-c-reference"></a><span data-ttu-id="ceb55-102">enum (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ceb55-102">enum (C# Reference)</span></span>

<span data-ttu-id="ceb55-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span><span class="sxs-lookup"><span data-stu-id="ceb55-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>

<span data-ttu-id="ceb55-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span><span class="sxs-lookup"><span data-stu-id="ceb55-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="ceb55-105">However, an enum can also be nested within a class or struct.</span><span class="sxs-lookup"><span data-stu-id="ceb55-105">However, an enum can also be nested within a class or struct.</span></span>

<span data-ttu-id="ceb55-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span><span class="sxs-lookup"><span data-stu-id="ceb55-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="ceb55-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span><span class="sxs-lookup"><span data-stu-id="ceb55-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="ceb55-108">Enumerators can use initializers to override the default values, as shown in the following example.</span><span class="sxs-lookup"><span data-stu-id="ceb55-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="ceb55-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span><span class="sxs-lookup"><span data-stu-id="ceb55-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="ceb55-110">However, including a constant that has the value of 0 is recommended.</span><span class="sxs-lookup"><span data-stu-id="ceb55-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="ceb55-111">For more information, see [Enumeration Types](../../programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="ceb55-111">For more information, see [Enumeration Types](../../programming-guide/enumeration-types.md).</span></span>

<span data-ttu-id="ceb55-112">Every enumeration type has an underlying type, which can be any [integral numeric type](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="ceb55-112">Every enumeration type has an underlying type, which can be any [integral numeric type](../builtin-types/integral-numeric-types.md).</span></span> <span data-ttu-id="ceb55-113">The [char](../builtin-types/char.md) type cannot be an underlying type of an enum.</span><span class="sxs-lookup"><span data-stu-id="ceb55-113">The [char](../builtin-types/char.md) type cannot be an underlying type of an enum.</span></span> <span data-ttu-id="ceb55-114">The default underlying type of enumeration elements is [int](../builtin-types/integral-numeric-types.md). To declare an enum of another integral type, such as [byte](../builtin-types/integral-numeric-types.md), use a colon after the identifier followed by the type, as shown in the following example.</span><span class="sxs-lookup"><span data-stu-id="ceb55-114">The default underlying type of enumeration elements is [int](../builtin-types/integral-numeric-types.md). To declare an enum of another integral type, such as [byte](../builtin-types/integral-numeric-types.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="ceb55-115">A variable of an enumeration type can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span><span class="sxs-lookup"><span data-stu-id="ceb55-115">A variable of an enumeration type can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>

<span data-ttu-id="ceb55-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span><span class="sxs-lookup"><span data-stu-id="ceb55-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>

> [!NOTE]
> <span data-ttu-id="ceb55-117">An enumerator cannot contain white space in its name.</span><span class="sxs-lookup"><span data-stu-id="ceb55-117">An enumerator cannot contain white space in its name.</span></span>

<span data-ttu-id="ceb55-118">The underlying type specifies how much storage is allocated for each enumerator.</span><span class="sxs-lookup"><span data-stu-id="ceb55-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="ceb55-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span><span class="sxs-lookup"><span data-stu-id="ceb55-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="ceb55-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../builtin-types/integral-numeric-types.md) by using a cast to convert from `enum` to `int`.</span><span class="sxs-lookup"><span data-stu-id="ceb55-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../builtin-types/integral-numeric-types.md) by using a cast to convert from `enum` to `int`.</span></span>

```csharp
int x = (int)Day.Sun;
```

<span data-ttu-id="ceb55-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span><span class="sxs-lookup"><span data-stu-id="ceb55-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="ceb55-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span><span class="sxs-lookup"><span data-stu-id="ceb55-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="ceb55-123">(See the third example.)</span><span class="sxs-lookup"><span data-stu-id="ceb55-123">(See the third example.)</span></span>

## <a name="robust-programming"></a><span data-ttu-id="ceb55-124">Robust programming</span><span class="sxs-lookup"><span data-stu-id="ceb55-124">Robust programming</span></span>

<span data-ttu-id="ceb55-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span><span class="sxs-lookup"><span data-stu-id="ceb55-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="ceb55-126">This can create potential versioning issues as described in [Constants](../../programming-guide/classes-and-structs/constants.md).</span><span class="sxs-lookup"><span data-stu-id="ceb55-126">This can create potential versioning issues as described in [Constants](../../programming-guide/classes-and-structs/constants.md).</span></span>

<span data-ttu-id="ceb55-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span><span class="sxs-lookup"><span data-stu-id="ceb55-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="ceb55-128">Enum values often are used in [switch](switch.md) statements.</span><span class="sxs-lookup"><span data-stu-id="ceb55-128">Enum values often are used in [switch](switch.md) statements.</span></span> <span data-ttu-id="ceb55-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span><span class="sxs-lookup"><span data-stu-id="ceb55-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>

<span data-ttu-id="ceb55-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span><span class="sxs-lookup"><span data-stu-id="ceb55-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>

## <a name="example"></a><span data-ttu-id="ceb55-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="ceb55-131">Example</span></span>

<span data-ttu-id="ceb55-132">In the following example, an enumeration, `Day`, is declared.</span><span class="sxs-lookup"><span data-stu-id="ceb55-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="ceb55-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span><span class="sxs-lookup"><span data-stu-id="ceb55-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a><span data-ttu-id="ceb55-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="ceb55-134">Example</span></span>

<span data-ttu-id="ceb55-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span><span class="sxs-lookup"><span data-stu-id="ceb55-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="ceb55-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span><span class="sxs-lookup"><span data-stu-id="ceb55-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a><span data-ttu-id="ceb55-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="ceb55-137">Example</span></span>

<span data-ttu-id="ceb55-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span><span class="sxs-lookup"><span data-stu-id="ceb55-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a><span data-ttu-id="ceb55-139">Komentáře</span><span class="sxs-lookup"><span data-stu-id="ceb55-139">Comments</span></span>

<span data-ttu-id="ceb55-140">If you remove `Flags`, the example displays the following values:</span><span class="sxs-lookup"><span data-stu-id="ceb55-140">If you remove `Flags`, the example displays the following values:</span></span>

`5`

`5`

## <a name="c-language-specification"></a><span data-ttu-id="ceb55-141">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ceb55-141">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ceb55-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ceb55-142">See also</span></span>

- [<span data-ttu-id="ceb55-143">C# Reference</span><span class="sxs-lookup"><span data-stu-id="ceb55-143">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ceb55-144">Výčtové typy</span><span class="sxs-lookup"><span data-stu-id="ceb55-144">Enumeration Types</span></span>](../../programming-guide/enumeration-types.md)
- [<span data-ttu-id="ceb55-145">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ceb55-145">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ceb55-146">Integral types</span><span class="sxs-lookup"><span data-stu-id="ceb55-146">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="ceb55-147">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="ceb55-147">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="ceb55-148">Enum Naming Conventions</span><span class="sxs-lookup"><span data-stu-id="ceb55-148">Enum Naming Conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
