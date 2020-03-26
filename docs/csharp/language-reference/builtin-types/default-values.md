---
title: Výchozí hodnoty typů jazyka C# – odkaz jazyka C#
description: Naučte se výchozí hodnoty c# typy jako bool, char, int, float, double a další.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 5e34d291ec15c738f3bc9409df321ede454b6710
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507253"
---
# <a name="default-values-of-c-types-c-reference"></a><span data-ttu-id="c37a5-103">Výchozí hodnoty typů jazyka C# (odkaz jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c37a5-103">Default values of C# types (C# reference)</span></span>

<span data-ttu-id="c37a5-104">V následující tabulce jsou uvedeny výchozí hodnoty typů jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="c37a5-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="c37a5-105">Typ</span><span class="sxs-lookup"><span data-stu-id="c37a5-105">Type</span></span>|<span data-ttu-id="c37a5-106">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="c37a5-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="c37a5-107">Jakýkoli typ odkazu</span><span class="sxs-lookup"><span data-stu-id="c37a5-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="c37a5-108">Jakýkoli [vestavěný integrální číselný typ](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="c37a5-108">Any [built-in integral numeric type](integral-numeric-types.md)</span></span>|<span data-ttu-id="c37a5-109">0 (nula)</span><span class="sxs-lookup"><span data-stu-id="c37a5-109">0 (zero)</span></span>|
|<span data-ttu-id="c37a5-110">Jakýkoli [vestavěný číselný typ s plovoucí desetinnou desetinnou desetinnou stoužek](floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="c37a5-110">Any [built-in floating-point numeric type](floating-point-numeric-types.md)</span></span>|<span data-ttu-id="c37a5-111">0 (nula)</span><span class="sxs-lookup"><span data-stu-id="c37a5-111">0 (zero)</span></span>|
|[<span data-ttu-id="c37a5-112">bool</span><span class="sxs-lookup"><span data-stu-id="c37a5-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="c37a5-113">char</span><span class="sxs-lookup"><span data-stu-id="c37a5-113">char</span></span>](char.md)|<span data-ttu-id="c37a5-114">`'\0'`(U+0000)</span><span class="sxs-lookup"><span data-stu-id="c37a5-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="c37a5-115">Výčtu</span><span class="sxs-lookup"><span data-stu-id="c37a5-115">enum</span></span>](enum.md)|<span data-ttu-id="c37a5-116">Hodnota vytvořená výrazem `(E)0` `E` , kde je identifikátor výčtu.</span><span class="sxs-lookup"><span data-stu-id="c37a5-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="c37a5-117">Struct</span><span class="sxs-lookup"><span data-stu-id="c37a5-117">struct</span></span>](struct.md)|<span data-ttu-id="c37a5-118">Hodnota vytvořená nastavením všech polí typu hodnoty na jejich výchozí `null`hodnoty a všechna pole typu odkazu na .</span><span class="sxs-lookup"><span data-stu-id="c37a5-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="c37a5-119">Jakýkoli [typ hodnoty s možnou hodnotou null](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="c37a5-119">Any [nullable value type](nullable-value-types.md)</span></span>|<span data-ttu-id="c37a5-120">Instance, pro <xref:System.Nullable%601.HasValue%2A> kterou `false` je <xref:System.Nullable%601.Value%2A> vlastnost a vlastnost není definována.</span><span class="sxs-lookup"><span data-stu-id="c37a5-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="c37a5-121">Tato výchozí hodnota je také známá jako *hodnota null* typu hodnoty s možnou hodnotou, kterou lze hodnotit.</span><span class="sxs-lookup"><span data-stu-id="c37a5-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="c37a5-122">Pomocí [ `default` operátoru](../operators/default.md#default-operator) můžete vytvořit výchozí hodnotu typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="c37a5-122">Use the [`default` operator](../operators/default.md#default-operator) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="c37a5-123">Počínaje C# 7.1, můžete použít [ `default` literál](../operators/default.md#default-literal) k inicializaci proměnné s výchozí hodnotou jejího typu:</span><span class="sxs-lookup"><span data-stu-id="c37a5-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="c37a5-124">Pro typ hodnoty implicitní konstruktor bez parametrů také vytvoří výchozí hodnotu typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="c37a5-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="c37a5-125">Za běhu, pokud <xref:System.Type?displayProperty=nameWithType> instance představuje typ hodnoty, <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> můžete použít metodu k vyvolání konstruktoru bez parametrů k získání výchozí hodnoty typu.</span><span class="sxs-lookup"><span data-stu-id="c37a5-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c37a5-126">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c37a5-126">C# language specification</span></span>

<span data-ttu-id="c37a5-127">Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="c37a5-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="c37a5-128">Výchozí hodnoty</span><span class="sxs-lookup"><span data-stu-id="c37a5-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="c37a5-129">Výchozí konstruktory</span><span class="sxs-lookup"><span data-stu-id="c37a5-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="c37a5-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="c37a5-130">See also</span></span>

- [<span data-ttu-id="c37a5-131">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="c37a5-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c37a5-132">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="c37a5-132">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
