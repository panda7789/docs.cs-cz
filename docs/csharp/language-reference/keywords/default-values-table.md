---
title: Výchozí hodnoty tabulka – C# odkaz
ms.custom: seodec18
description: Zjistěte, jaké jsou výchozí hodnoty C# typů.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 48aa294fa9e37e2e138444e493faa5474011097e
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74551826"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="a3322-103">Tabulka výchozích hodnot (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="a3322-103">Default values table (C# reference)</span></span>

<span data-ttu-id="a3322-104">Následující tabulka ukazuje výchozí hodnoty C# typů:</span><span class="sxs-lookup"><span data-stu-id="a3322-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="a3322-105">Type</span><span class="sxs-lookup"><span data-stu-id="a3322-105">Type</span></span>|<span data-ttu-id="a3322-106">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="a3322-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="a3322-107">Libovolný typ odkazu</span><span class="sxs-lookup"><span data-stu-id="a3322-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="a3322-108">Libovolný [vestavěný celočíselný numerický typ](../builtin-types/integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="a3322-108">Any [built-in integral numeric type](../builtin-types/integral-numeric-types.md)</span></span>|<span data-ttu-id="a3322-109">0 (nula)</span><span class="sxs-lookup"><span data-stu-id="a3322-109">0 (zero)</span></span>|
|<span data-ttu-id="a3322-110">Libovolný [vestavěný číselný typ s plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou</span><span class="sxs-lookup"><span data-stu-id="a3322-110">Any [built-in floating-point numeric type](../builtin-types/floating-point-numeric-types.md)</span></span>|<span data-ttu-id="a3322-111">0 (nula)</span><span class="sxs-lookup"><span data-stu-id="a3322-111">0 (zero)</span></span>|
|[<span data-ttu-id="a3322-112">bool</span><span class="sxs-lookup"><span data-stu-id="a3322-112">bool</span></span>](../builtin-types/bool.md)|`false`|
|[<span data-ttu-id="a3322-113">char</span><span class="sxs-lookup"><span data-stu-id="a3322-113">char</span></span>](../builtin-types/char.md)|<span data-ttu-id="a3322-114">`'\0'` (U + 0000)</span><span class="sxs-lookup"><span data-stu-id="a3322-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="a3322-115">enum</span><span class="sxs-lookup"><span data-stu-id="a3322-115">enum</span></span>](enum.md)|<span data-ttu-id="a3322-116">Hodnota vytvořená výrazem `(E)0`, kde `E` je identifikátor výčtu.</span><span class="sxs-lookup"><span data-stu-id="a3322-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="a3322-117">struct</span><span class="sxs-lookup"><span data-stu-id="a3322-117">struct</span></span>](struct.md)|<span data-ttu-id="a3322-118">Hodnota vytvořená nastavením všech polí typu hodnoty na jejich výchozí hodnoty a všechna pole typu odkaz na `null`.</span><span class="sxs-lookup"><span data-stu-id="a3322-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="a3322-119">Libovolný [typ hodnoty s možnou hodnotou null](../builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="a3322-119">Any [nullable value type](../builtin-types/nullable-value-types.md)</span></span>|<span data-ttu-id="a3322-120">Instance, pro kterou je vlastnost <xref:System.Nullable%601.HasValue%2A> `false` a vlastnost <xref:System.Nullable%601.Value%2A> není definována.</span><span class="sxs-lookup"><span data-stu-id="a3322-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="a3322-121">Tato výchozí hodnota je také známá jako hodnota *null* typu hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="a3322-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="a3322-122">Použijte [výchozí operátor](../operators/default.md) k vytvoření výchozí hodnoty typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="a3322-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="a3322-123">Počínaje C# 7,1 můžete použít [literál`default`](../operators/default.md#default-literal) k inicializaci proměnné s výchozí hodnotou svého typu:</span><span class="sxs-lookup"><span data-stu-id="a3322-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="a3322-124">Pro typ hodnoty, implicitní konstruktor bez parametrů vytvoří také výchozí hodnotu typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="a3322-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a><span data-ttu-id="a3322-125">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a3322-125">C# language specification</span></span>

<span data-ttu-id="a3322-126">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="a3322-126">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="a3322-127">Výchozí hodnoty</span><span class="sxs-lookup"><span data-stu-id="a3322-127">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="a3322-128">Výchozí konstruktory</span><span class="sxs-lookup"><span data-stu-id="a3322-128">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="a3322-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3322-129">See also</span></span>

- [<span data-ttu-id="a3322-130">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="a3322-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a3322-131">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a3322-131">C# keywords</span></span>](index.md)
- [<span data-ttu-id="a3322-132">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="a3322-132">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="a3322-133">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="a3322-133">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
