---
title: Výchozí hodnoty C# typů – C# referenční informace
description: Seznamte se s výchozími hodnotami C# typů, jako jsou bool, char, int, float, Double a more.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 2447db25e837cdcd6d67847b8677d7d44da551a9
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964942"
---
# <a name="default-values-of-c-types-c-reference"></a><span data-ttu-id="42e0f-103">Výchozí hodnoty C# typů (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="42e0f-103">Default values of C# types (C# reference)</span></span>

<span data-ttu-id="42e0f-104">Následující tabulka ukazuje výchozí hodnoty C# typů:</span><span class="sxs-lookup"><span data-stu-id="42e0f-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="42e0f-105">Type</span><span class="sxs-lookup"><span data-stu-id="42e0f-105">Type</span></span>|<span data-ttu-id="42e0f-106">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="42e0f-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="42e0f-107">Libovolný typ odkazu</span><span class="sxs-lookup"><span data-stu-id="42e0f-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="42e0f-108">Libovolný [vestavěný celočíselný numerický typ](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="42e0f-108">Any [built-in integral numeric type](integral-numeric-types.md)</span></span>|<span data-ttu-id="42e0f-109">0 (nula)</span><span class="sxs-lookup"><span data-stu-id="42e0f-109">0 (zero)</span></span>|
|<span data-ttu-id="42e0f-110">Libovolný [vestavěný číselný typ s plovoucí desetinnou](floating-point-numeric-types.md) čárkou</span><span class="sxs-lookup"><span data-stu-id="42e0f-110">Any [built-in floating-point numeric type](floating-point-numeric-types.md)</span></span>|<span data-ttu-id="42e0f-111">0 (nula)</span><span class="sxs-lookup"><span data-stu-id="42e0f-111">0 (zero)</span></span>|
|[<span data-ttu-id="42e0f-112">bool</span><span class="sxs-lookup"><span data-stu-id="42e0f-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="42e0f-113">char</span><span class="sxs-lookup"><span data-stu-id="42e0f-113">char</span></span>](char.md)|<span data-ttu-id="42e0f-114">`'\0'` (U + 0000)</span><span class="sxs-lookup"><span data-stu-id="42e0f-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="42e0f-115">enum</span><span class="sxs-lookup"><span data-stu-id="42e0f-115">enum</span></span>](enum.md)|<span data-ttu-id="42e0f-116">Hodnota vytvořená výrazem `(E)0`, kde `E` je identifikátor výčtu.</span><span class="sxs-lookup"><span data-stu-id="42e0f-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="42e0f-117">struct</span><span class="sxs-lookup"><span data-stu-id="42e0f-117">struct</span></span>](../keywords/struct.md)|<span data-ttu-id="42e0f-118">Hodnota vytvořená nastavením všech polí typu hodnoty na jejich výchozí hodnoty a všechna pole typu odkaz na `null`.</span><span class="sxs-lookup"><span data-stu-id="42e0f-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="42e0f-119">Libovolný [typ hodnoty s možnou hodnotou null](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="42e0f-119">Any [nullable value type](nullable-value-types.md)</span></span>|<span data-ttu-id="42e0f-120">Instance, pro kterou je vlastnost <xref:System.Nullable%601.HasValue%2A> `false` a vlastnost <xref:System.Nullable%601.Value%2A> není definována.</span><span class="sxs-lookup"><span data-stu-id="42e0f-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="42e0f-121">Tato výchozí hodnota je také známá jako hodnota *null* typu hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="42e0f-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="42e0f-122">Použijte [výchozí operátor](../operators/default.md) k vytvoření výchozí hodnoty typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="42e0f-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="42e0f-123">Počínaje C# 7,1 můžete použít [literál`default`](../operators/default.md#default-literal) k inicializaci proměnné s výchozí hodnotou svého typu:</span><span class="sxs-lookup"><span data-stu-id="42e0f-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="42e0f-124">Pro typ hodnoty, implicitní konstruktor bez parametrů vytvoří také výchozí hodnotu typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="42e0f-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="42e0f-125">V době běhu, pokud <xref:System.Type?displayProperty=nameWithType> instance představuje typ hodnoty, lze použít metodu <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> k vyvolání konstruktoru bez parametrů k získání výchozí hodnoty typu.</span><span class="sxs-lookup"><span data-stu-id="42e0f-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="42e0f-126">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="42e0f-126">C# language specification</span></span>

<span data-ttu-id="42e0f-127">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="42e0f-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="42e0f-128">Výchozí hodnoty</span><span class="sxs-lookup"><span data-stu-id="42e0f-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="42e0f-129">Výchozí konstruktory</span><span class="sxs-lookup"><span data-stu-id="42e0f-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="42e0f-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42e0f-130">See also</span></span>

- [<span data-ttu-id="42e0f-131">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="42e0f-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="42e0f-132">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="42e0f-132">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)