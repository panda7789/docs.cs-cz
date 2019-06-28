---
title: Tabulka výchozích hodnot - C# odkaz
ms.custom: seodec18
description: Zjistěte, jaké jsou výchozí hodnoty jazyka C# hodnotové typy.
ms.date: 08/23/2018
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- parameterless constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], parameterless constructor
- types [C#], parameterless constructor return values
ms.openlocfilehash: dfab5107d4a0ad14c3ffbfc6a5f3c4317b44d17c
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424223"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="97d28-103">Tabulka výchozích hodnot (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="97d28-103">Default values table (C# Reference)</span></span>

<span data-ttu-id="97d28-104">V následující tabulce jsou uvedeny výchozí hodnoty [typů hodnot](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="97d28-104">The following table shows the default values of [value types](value-types.md).</span></span>

|<span data-ttu-id="97d28-105">Typ hodnoty</span><span class="sxs-lookup"><span data-stu-id="97d28-105">Value type</span></span>|<span data-ttu-id="97d28-106">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="97d28-106">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="97d28-107">bool</span><span class="sxs-lookup"><span data-stu-id="97d28-107">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="97d28-108">byte</span><span class="sxs-lookup"><span data-stu-id="97d28-108">byte</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="97d28-109">0</span><span class="sxs-lookup"><span data-stu-id="97d28-109">0</span></span>|
|[<span data-ttu-id="97d28-110">char</span><span class="sxs-lookup"><span data-stu-id="97d28-110">char</span></span>](char.md)|<span data-ttu-id="97d28-111">'\0'</span><span class="sxs-lookup"><span data-stu-id="97d28-111">'\0'</span></span>|
|[<span data-ttu-id="97d28-112">decimal</span><span class="sxs-lookup"><span data-stu-id="97d28-112">decimal</span></span>](decimal.md)|<span data-ttu-id="97d28-113">0M</span><span class="sxs-lookup"><span data-stu-id="97d28-113">0M</span></span>|
|[<span data-ttu-id="97d28-114">double</span><span class="sxs-lookup"><span data-stu-id="97d28-114">double</span></span>](double.md)|<span data-ttu-id="97d28-115">0.0 D</span><span class="sxs-lookup"><span data-stu-id="97d28-115">0.0D</span></span>|
|[<span data-ttu-id="97d28-116">enum</span><span class="sxs-lookup"><span data-stu-id="97d28-116">enum</span></span>](enum.md)|<span data-ttu-id="97d28-117">Hodnota vytvořený podle výrazu `(E)0`, kde `E` je identifikátor výčtu.</span><span class="sxs-lookup"><span data-stu-id="97d28-117">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="97d28-118">float</span><span class="sxs-lookup"><span data-stu-id="97d28-118">float</span></span>](float.md)|<span data-ttu-id="97d28-119">0,0 F</span><span class="sxs-lookup"><span data-stu-id="97d28-119">0.0F</span></span>|
|[<span data-ttu-id="97d28-120">int</span><span class="sxs-lookup"><span data-stu-id="97d28-120">int</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="97d28-121">0</span><span class="sxs-lookup"><span data-stu-id="97d28-121">0</span></span>|
|[<span data-ttu-id="97d28-122">long</span><span class="sxs-lookup"><span data-stu-id="97d28-122">long</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="97d28-123">0L</span><span class="sxs-lookup"><span data-stu-id="97d28-123">0L</span></span>|
|[<span data-ttu-id="97d28-124">sbyte</span><span class="sxs-lookup"><span data-stu-id="97d28-124">sbyte</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="97d28-125">0</span><span class="sxs-lookup"><span data-stu-id="97d28-125">0</span></span>|
|[<span data-ttu-id="97d28-126">short</span><span class="sxs-lookup"><span data-stu-id="97d28-126">short</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="97d28-127">0</span><span class="sxs-lookup"><span data-stu-id="97d28-127">0</span></span>|
|[<span data-ttu-id="97d28-128">struct</span><span class="sxs-lookup"><span data-stu-id="97d28-128">struct</span></span>](struct.md)|<span data-ttu-id="97d28-129">Hodnota vytvořen nastavením všechna pole typu hodnoty na jejich výchozí hodnoty a všechna pole typu odkazu k `null`.</span><span class="sxs-lookup"><span data-stu-id="97d28-129">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="97d28-130">uint</span><span class="sxs-lookup"><span data-stu-id="97d28-130">uint</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="97d28-131">0</span><span class="sxs-lookup"><span data-stu-id="97d28-131">0</span></span>|
|[<span data-ttu-id="97d28-132">ulong</span><span class="sxs-lookup"><span data-stu-id="97d28-132">ulong</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="97d28-133">0</span><span class="sxs-lookup"><span data-stu-id="97d28-133">0</span></span>|
|[<span data-ttu-id="97d28-134">ushort</span><span class="sxs-lookup"><span data-stu-id="97d28-134">ushort</span></span>](../builtin-types/integral-numeric-types.md)|<span data-ttu-id="97d28-135">0</span><span class="sxs-lookup"><span data-stu-id="97d28-135">0</span></span>|

## <a name="remarks"></a><span data-ttu-id="97d28-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97d28-136">Remarks</span></span>

<span data-ttu-id="97d28-137">Neinicializované proměnné nelze použít v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="97d28-137">You cannot use uninitialized variables in C#.</span></span> <span data-ttu-id="97d28-138">Můžete inicializovat proměnné s výchozí hodnotou jeho typu.</span><span class="sxs-lookup"><span data-stu-id="97d28-138">You can initialize a variable with the default value of its type.</span></span> <span data-ttu-id="97d28-139">Také vám pomůže výchozí hodnota typu zadat výchozí hodnotu z metody [nepovinný argument](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments).</span><span class="sxs-lookup"><span data-stu-id="97d28-139">You also can use the default value of a type to specify the default value of a method's [optional argument](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments).</span></span>

<span data-ttu-id="97d28-140">Použití [výchozí hodnota výrazu](../../programming-guide/statements-expressions-operators/default-value-expressions.md) vytvoří výchozí hodnota typu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="97d28-140">Use the [default value expression](../../programming-guide/statements-expressions-operators/default-value-expressions.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="97d28-141">Od verze C# 7.1, můžete použít [ `default` literálu](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) inicializace proměnné s výchozí hodnotou typu:</span><span class="sxs-lookup"><span data-stu-id="97d28-141">Beginning with C# 7.1, you can use the [`default` literal](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="97d28-142">Jak ukazuje následující příklad vytvoří výchozí hodnota typu hodnoty, můžete použít také konstruktor bez parametrů nebo implicitní konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="97d28-142">You also can use the parameterless constructor or the implicit parameterless constructor to produce the default value of a value type, as the following example shows.</span></span> <span data-ttu-id="97d28-143">Další informace o konstruktorech naleznete v tématu [konstruktory](../../programming-guide/classes-and-structs/constructors.md) článku.</span><span class="sxs-lookup"><span data-stu-id="97d28-143">For more information about constructors, see the [Constructors](../../programming-guide/classes-and-structs/constructors.md) article.</span></span>

```csharp
int a = new int();
```

<span data-ttu-id="97d28-144">Zadejte výchozí hodnotu kterékoli [odkazovat na typ](reference-types.md) je `null`.</span><span class="sxs-lookup"><span data-stu-id="97d28-144">The default value of any [reference type](reference-types.md) is `null`.</span></span> <span data-ttu-id="97d28-145">Výchozí hodnota [typ připouštějící hodnotu Null](../../programming-guide/nullable-types/index.md) u kterého je instance <xref:System.Nullable%601.HasValue%2A> vlastnost `false` a <xref:System.Nullable%601.Value%2A> vlastnost není definována.</span><span class="sxs-lookup"><span data-stu-id="97d28-145">The default value of a [nullable type](../../programming-guide/nullable-types/index.md) is an instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>

## <a name="see-also"></a><span data-ttu-id="97d28-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97d28-146">See also</span></span>

- [<span data-ttu-id="97d28-147">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="97d28-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="97d28-148">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="97d28-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="97d28-149">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="97d28-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="97d28-150">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="97d28-150">Value types</span></span>](value-types.md)
- [<span data-ttu-id="97d28-151">Tabulka typů hodnot</span><span class="sxs-lookup"><span data-stu-id="97d28-151">Value types table</span></span>](value-types-table.md)
- [<span data-ttu-id="97d28-152">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="97d28-152">Built-in types table</span></span>](built-in-types-table.md)
