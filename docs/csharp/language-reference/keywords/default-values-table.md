---
title: Default values table - C# reference
ms.custom: seodec18
description: Learn what are the default values of C# types.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 2f1ad5cc029b93261153e46d854cd8bf3e31ce92
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428538"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="d42fb-103">Default values table (C# reference)</span><span class="sxs-lookup"><span data-stu-id="d42fb-103">Default values table (C# reference)</span></span>

<span data-ttu-id="d42fb-104">The following table shows the default values of C# types:</span><span class="sxs-lookup"><span data-stu-id="d42fb-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="d42fb-105">Typ</span><span class="sxs-lookup"><span data-stu-id="d42fb-105">Type</span></span>|<span data-ttu-id="d42fb-106">Default value</span><span class="sxs-lookup"><span data-stu-id="d42fb-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="d42fb-107">Any reference type</span><span class="sxs-lookup"><span data-stu-id="d42fb-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="d42fb-108">Any [built-in integral numeric type](../builtin-types/integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="d42fb-108">Any [built-in integral numeric type](../builtin-types/integral-numeric-types.md)</span></span>|<span data-ttu-id="d42fb-109">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="d42fb-109">0 (zero)</span></span>|
|<span data-ttu-id="d42fb-110">Any [built-in floating-point numeric type](../builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="d42fb-110">Any [built-in floating-point numeric type](../builtin-types/floating-point-numeric-types.md)</span></span>|<span data-ttu-id="d42fb-111">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="d42fb-111">0 (zero)</span></span>|
|[<span data-ttu-id="d42fb-112">bool</span><span class="sxs-lookup"><span data-stu-id="d42fb-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="d42fb-113">char</span><span class="sxs-lookup"><span data-stu-id="d42fb-113">char</span></span>](../builtin-types/char.md)|<span data-ttu-id="d42fb-114">`'\0'` (U+0000)</span><span class="sxs-lookup"><span data-stu-id="d42fb-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="d42fb-115">enum</span><span class="sxs-lookup"><span data-stu-id="d42fb-115">enum</span></span>](enum.md)|<span data-ttu-id="d42fb-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span><span class="sxs-lookup"><span data-stu-id="d42fb-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="d42fb-117">struct</span><span class="sxs-lookup"><span data-stu-id="d42fb-117">struct</span></span>](struct.md)|<span data-ttu-id="d42fb-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span><span class="sxs-lookup"><span data-stu-id="d42fb-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="d42fb-119">Any [nullable value type](../builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="d42fb-119">Any [nullable value type](../builtin-types/nullable-value-types.md)</span></span>|<span data-ttu-id="d42fb-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span><span class="sxs-lookup"><span data-stu-id="d42fb-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="d42fb-121">That default value is also known as the *null* value of a nullable value type.</span><span class="sxs-lookup"><span data-stu-id="d42fb-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="d42fb-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span><span class="sxs-lookup"><span data-stu-id="d42fb-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="d42fb-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span><span class="sxs-lookup"><span data-stu-id="d42fb-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="d42fb-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span><span class="sxs-lookup"><span data-stu-id="d42fb-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a><span data-ttu-id="d42fb-125">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d42fb-125">C# language specification</span></span>

<span data-ttu-id="d42fb-126">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="d42fb-126">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="d42fb-127">Default values</span><span class="sxs-lookup"><span data-stu-id="d42fb-127">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="d42fb-128">Default constructors</span><span class="sxs-lookup"><span data-stu-id="d42fb-128">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="d42fb-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d42fb-129">See also</span></span>

- [<span data-ttu-id="d42fb-130">C# reference</span><span class="sxs-lookup"><span data-stu-id="d42fb-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d42fb-131">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d42fb-131">C# keywords</span></span>](index.md)
- [<span data-ttu-id="d42fb-132">Built-in types table</span><span class="sxs-lookup"><span data-stu-id="d42fb-132">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="d42fb-133">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="d42fb-133">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
