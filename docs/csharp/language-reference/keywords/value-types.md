---
title: Value types - C# Reference
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: b264be5d2589455562a19ef55b5ddf1a4e74ce15
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428449"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="c4018-102">Value types (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="c4018-102">Value types (C# Reference)</span></span>

<span data-ttu-id="c4018-103">There are two kinds of value types:</span><span class="sxs-lookup"><span data-stu-id="c4018-103">There are two kinds of value types:</span></span>

- [<span data-ttu-id="c4018-104">Struktury</span><span class="sxs-lookup"><span data-stu-id="c4018-104">Structs</span></span>](struct.md)

- [<span data-ttu-id="c4018-105">Výčty</span><span class="sxs-lookup"><span data-stu-id="c4018-105">Enumerations</span></span>](enum.md)

## <a name="main-features-of-value-types"></a><span data-ttu-id="c4018-106">Main features of value types</span><span class="sxs-lookup"><span data-stu-id="c4018-106">Main features of value types</span></span>

<span data-ttu-id="c4018-107">A variable of a value type contains a value of the type.</span><span class="sxs-lookup"><span data-stu-id="c4018-107">A variable of a value type contains a value of the type.</span></span> <span data-ttu-id="c4018-108">For example, a variable of the `int` type might contain the value `42`.</span><span class="sxs-lookup"><span data-stu-id="c4018-108">For example, a variable of the `int` type might contain the value `42`.</span></span> <span data-ttu-id="c4018-109">This differs from a variable of a reference type, which contains a reference to an instance of the type, also known as an object.</span><span class="sxs-lookup"><span data-stu-id="c4018-109">This differs from a variable of a reference type, which contains a reference to an instance of the type, also known as an object.</span></span> <span data-ttu-id="c4018-110">When you assign a new value to a variable of a value type, that value is copied.</span><span class="sxs-lookup"><span data-stu-id="c4018-110">When you assign a new value to a variable of a value type, that value is copied.</span></span> <span data-ttu-id="c4018-111">When you assign a new value to a variable of a reference type, the reference is copied, not the object itself.</span><span class="sxs-lookup"><span data-stu-id="c4018-111">When you assign a new value to a variable of a reference type, the reference is copied, not the object itself.</span></span>

<span data-ttu-id="c4018-112">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c4018-112">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c4018-113">Unlike with reference types, you cannot derive a new type from a value type.</span><span class="sxs-lookup"><span data-stu-id="c4018-113">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="c4018-114">However, like reference types, structs can implement interfaces.</span><span class="sxs-lookup"><span data-stu-id="c4018-114">However, like reference types, structs can implement interfaces.</span></span>

<span data-ttu-id="c4018-115">Value type variables cannot be `null` by default.</span><span class="sxs-lookup"><span data-stu-id="c4018-115">Value type variables cannot be `null` by default.</span></span> <span data-ttu-id="c4018-116">However, variables of the corresponding [nullable value types](../builtin-types/nullable-value-types.md) can be `null`.</span><span class="sxs-lookup"><span data-stu-id="c4018-116">However, variables of the corresponding [nullable value types](../builtin-types/nullable-value-types.md) can be `null`.</span></span>

<span data-ttu-id="c4018-117">Each value type has an implicit parameterless constructor that initializes the default value of that type.</span><span class="sxs-lookup"><span data-stu-id="c4018-117">Each value type has an implicit parameterless constructor that initializes the default value of that type.</span></span> <span data-ttu-id="c4018-118">For information about default values of value types, see [Default values table](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="c4018-118">For information about default values of value types, see [Default values table](default-values-table.md).</span></span>

## <a name="simple-types"></a><span data-ttu-id="c4018-119">Simple types</span><span class="sxs-lookup"><span data-stu-id="c4018-119">Simple types</span></span>

<span data-ttu-id="c4018-120">The *simple types* are a set of predefined struct types provided by C# and comprise the following types:</span><span class="sxs-lookup"><span data-stu-id="c4018-120">The *simple types* are a set of predefined struct types provided by C# and comprise the following types:</span></span>

- <span data-ttu-id="c4018-121">[Integral types](../builtin-types/integral-numeric-types.md): integer numeric types and the [char](../builtin-types/char.md) type</span><span class="sxs-lookup"><span data-stu-id="c4018-121">[Integral types](../builtin-types/integral-numeric-types.md): integer numeric types and the [char](../builtin-types/char.md) type</span></span>
- [<span data-ttu-id="c4018-122">Floating-point types</span><span class="sxs-lookup"><span data-stu-id="c4018-122">Floating-point types</span></span>](../builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="c4018-123">bool</span><span class="sxs-lookup"><span data-stu-id="c4018-123">bool</span></span>](bool.md)

<span data-ttu-id="c4018-124">The simple types are identified through keywords, but these keywords are simply aliases for predefined struct types in the <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="c4018-124">The simple types are identified through keywords, but these keywords are simply aliases for predefined struct types in the <xref:System> namespace.</span></span> <span data-ttu-id="c4018-125">For example, [int](../builtin-types/integral-numeric-types.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c4018-125">For example, [int](../builtin-types/integral-numeric-types.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c4018-126">For a complete list of aliases, see [Built-in types table](built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="c4018-126">For a complete list of aliases, see [Built-in types table](built-in-types-table.md).</span></span>

<span data-ttu-id="c4018-127">The simple types differ from other struct types in that they permit certain additional operations:</span><span class="sxs-lookup"><span data-stu-id="c4018-127">The simple types differ from other struct types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="c4018-128">Simple types can be initialized by using literals.</span><span class="sxs-lookup"><span data-stu-id="c4018-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="c4018-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span><span class="sxs-lookup"><span data-stu-id="c4018-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="c4018-130">You can declare constants of the simple types with the [const](const.md) keyword.</span><span class="sxs-lookup"><span data-stu-id="c4018-130">You can declare constants of the simple types with the [const](const.md) keyword.</span></span> <span data-ttu-id="c4018-131">It's not possible to have constants of other struct types.</span><span class="sxs-lookup"><span data-stu-id="c4018-131">It's not possible to have constants of other struct types.</span></span>

- <span data-ttu-id="c4018-132">Constant expressions, whose operands are all simple type constants, are evaluated at compile time.</span><span class="sxs-lookup"><span data-stu-id="c4018-132">Constant expressions, whose operands are all simple type constants, are evaluated at compile time.</span></span>

<span data-ttu-id="c4018-133">For more information, see the [Simple types](~/_csharplang/spec/types.md#simple-types) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="c4018-133">For more information, see the [Simple types](~/_csharplang/spec/types.md#simple-types) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="initializing-value-types"></a><span data-ttu-id="c4018-134">Initializing value types</span><span class="sxs-lookup"><span data-stu-id="c4018-134">Initializing value types</span></span>

<span data-ttu-id="c4018-135">Local variables in C# must be initialized before they are used.</span><span class="sxs-lookup"><span data-stu-id="c4018-135">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="c4018-136">For example, you might declare a local variable without initialization as in the following example:</span><span class="sxs-lookup"><span data-stu-id="c4018-136">For example, you might declare a local variable without initialization as in the following example:</span></span>

```csharp
int myInt;
```

<span data-ttu-id="c4018-137">You cannot use it before you initialize it.</span><span class="sxs-lookup"><span data-stu-id="c4018-137">You cannot use it before you initialize it.</span></span> <span data-ttu-id="c4018-138">You can initialize it using the following statement:</span><span class="sxs-lookup"><span data-stu-id="c4018-138">You can initialize it using the following statement:</span></span>

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

<span data-ttu-id="c4018-139">This statement is equivalent to the following statement:</span><span class="sxs-lookup"><span data-stu-id="c4018-139">This statement is equivalent to the following statement:</span></span>

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

<span data-ttu-id="c4018-140">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span><span class="sxs-lookup"><span data-stu-id="c4018-140">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="c4018-141">–or–</span><span class="sxs-lookup"><span data-stu-id="c4018-141">–or–</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="c4018-142">Using the [new](../operators/new-operator.md) operator calls the parameterless constructor of the specific type and assigns the default value to the variable.</span><span class="sxs-lookup"><span data-stu-id="c4018-142">Using the [new](../operators/new-operator.md) operator calls the parameterless constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="c4018-143">In the preceding example, the parameterless constructor assigned the value `0` to `myInt`.</span><span class="sxs-lookup"><span data-stu-id="c4018-143">In the preceding example, the parameterless constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="c4018-144">For more information about values assigned by calling parameterless constructors, see [Default values table](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="c4018-144">For more information about values assigned by calling parameterless constructors, see [Default values table](default-values-table.md).</span></span>

<span data-ttu-id="c4018-145">With user-defined types, use [new](../operators/new-operator.md) to invoke the parameterless constructor.</span><span class="sxs-lookup"><span data-stu-id="c4018-145">With user-defined types, use [new](../operators/new-operator.md) to invoke the parameterless constructor.</span></span> <span data-ttu-id="c4018-146">For example, the following statement invokes the parameterless constructor of the `Point` struct:</span><span class="sxs-lookup"><span data-stu-id="c4018-146">For example, the following statement invokes the parameterless constructor of the `Point` struct:</span></span>

```csharp
var p = new Point(); // Invoke parameterless constructor for the struct.
```

<span data-ttu-id="c4018-147">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span><span class="sxs-lookup"><span data-stu-id="c4018-147">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>

<span data-ttu-id="c4018-148">For more information about the `new` operator, see [new](../operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c4018-148">For more information about the `new` operator, see [new](../operators/new-operator.md).</span></span>

<span data-ttu-id="c4018-149">For information about formatting the output of numeric types, see [Formatting numeric results table](formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="c4018-149">For information about formatting the output of numeric types, see [Formatting numeric results table](formatting-numeric-results-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4018-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4018-150">See also</span></span>

- [<span data-ttu-id="c4018-151">C# reference</span><span class="sxs-lookup"><span data-stu-id="c4018-151">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c4018-152">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c4018-152">C# keywords</span></span>](index.md)
- [<span data-ttu-id="c4018-153">Reference types</span><span class="sxs-lookup"><span data-stu-id="c4018-153">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="c4018-154">Nullable value types</span><span class="sxs-lookup"><span data-stu-id="c4018-154">Nullable value types</span></span>](../builtin-types/nullable-value-types.md)
