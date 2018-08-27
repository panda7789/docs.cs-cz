---
title: Tabulka výchozích hodnot (referenční dokumentace jazyka C#)
description: Zjistěte, jaké jsou výchozí hodnoty jazyka C# hodnotové typy.
ms.date: 08/23/2018
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 184a9f42ddd3654a81aef0b7ce35e404de2d4bb9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935836"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="b3c1f-103">Tabulka výchozích hodnot (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b3c1f-103">Default values table (C# Reference)</span></span>

<span data-ttu-id="b3c1f-104">V následující tabulce jsou uvedeny výchozí hodnoty [typů hodnot](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="b3c1f-104">The following table shows the default values of [value types](value-types.md).</span></span>

|<span data-ttu-id="b3c1f-105">Typ hodnoty</span><span class="sxs-lookup"><span data-stu-id="b3c1f-105">Value type</span></span>|<span data-ttu-id="b3c1f-106">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="b3c1f-106">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="b3c1f-107">bool</span><span class="sxs-lookup"><span data-stu-id="b3c1f-107">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="b3c1f-108">byte</span><span class="sxs-lookup"><span data-stu-id="b3c1f-108">byte</span></span>](byte.md)|<span data-ttu-id="b3c1f-109">0</span><span class="sxs-lookup"><span data-stu-id="b3c1f-109">0</span></span>|
|[<span data-ttu-id="b3c1f-110">char</span><span class="sxs-lookup"><span data-stu-id="b3c1f-110">char</span></span>](char.md)|<span data-ttu-id="b3c1f-111">'\0'</span><span class="sxs-lookup"><span data-stu-id="b3c1f-111">'\0'</span></span>|
|[<span data-ttu-id="b3c1f-112">decimal</span><span class="sxs-lookup"><span data-stu-id="b3c1f-112">decimal</span></span>](decimal.md)|<span data-ttu-id="b3c1f-113">0M</span><span class="sxs-lookup"><span data-stu-id="b3c1f-113">0M</span></span>|
|[<span data-ttu-id="b3c1f-114">double</span><span class="sxs-lookup"><span data-stu-id="b3c1f-114">double</span></span>](double.md)|<span data-ttu-id="b3c1f-115">0.0 D</span><span class="sxs-lookup"><span data-stu-id="b3c1f-115">0.0D</span></span>|
|[<span data-ttu-id="b3c1f-116">enum</span><span class="sxs-lookup"><span data-stu-id="b3c1f-116">enum</span></span>](enum.md)|<span data-ttu-id="b3c1f-117">Hodnota vytvořený podle výrazu `(E)0`, kde `E` je identifikátor výčtu.</span><span class="sxs-lookup"><span data-stu-id="b3c1f-117">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="b3c1f-118">float</span><span class="sxs-lookup"><span data-stu-id="b3c1f-118">float</span></span>](float.md)|<span data-ttu-id="b3c1f-119">0,0 F</span><span class="sxs-lookup"><span data-stu-id="b3c1f-119">0.0F</span></span>|
|[<span data-ttu-id="b3c1f-120">int</span><span class="sxs-lookup"><span data-stu-id="b3c1f-120">int</span></span>](int.md)|<span data-ttu-id="b3c1f-121">0</span><span class="sxs-lookup"><span data-stu-id="b3c1f-121">0</span></span>|
|[<span data-ttu-id="b3c1f-122">long</span><span class="sxs-lookup"><span data-stu-id="b3c1f-122">long</span></span>](long.md)|<span data-ttu-id="b3c1f-123">0L</span><span class="sxs-lookup"><span data-stu-id="b3c1f-123">0L</span></span>|
|[<span data-ttu-id="b3c1f-124">sbyte</span><span class="sxs-lookup"><span data-stu-id="b3c1f-124">sbyte</span></span>](sbyte.md)|<span data-ttu-id="b3c1f-125">0</span><span class="sxs-lookup"><span data-stu-id="b3c1f-125">0</span></span>|
|[<span data-ttu-id="b3c1f-126">short</span><span class="sxs-lookup"><span data-stu-id="b3c1f-126">short</span></span>](short.md)|<span data-ttu-id="b3c1f-127">0</span><span class="sxs-lookup"><span data-stu-id="b3c1f-127">0</span></span>|
|[<span data-ttu-id="b3c1f-128">struct</span><span class="sxs-lookup"><span data-stu-id="b3c1f-128">struct</span></span>](struct.md)|<span data-ttu-id="b3c1f-129">Hodnota vytvořen nastavením všechna pole typu hodnoty na jejich výchozí hodnoty a všechna pole typu odkazu k `null`.</span><span class="sxs-lookup"><span data-stu-id="b3c1f-129">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="b3c1f-130">uint</span><span class="sxs-lookup"><span data-stu-id="b3c1f-130">uint</span></span>](uint.md)|<span data-ttu-id="b3c1f-131">0</span><span class="sxs-lookup"><span data-stu-id="b3c1f-131">0</span></span>|
|[<span data-ttu-id="b3c1f-132">ulong</span><span class="sxs-lookup"><span data-stu-id="b3c1f-132">ulong</span></span>](ulong.md)|<span data-ttu-id="b3c1f-133">0</span><span class="sxs-lookup"><span data-stu-id="b3c1f-133">0</span></span>|
|[<span data-ttu-id="b3c1f-134">ushort</span><span class="sxs-lookup"><span data-stu-id="b3c1f-134">ushort</span></span>](ushort.md)|<span data-ttu-id="b3c1f-135">0</span><span class="sxs-lookup"><span data-stu-id="b3c1f-135">0</span></span>|

## <a name="remarks"></a><span data-ttu-id="b3c1f-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3c1f-136">Remarks</span></span>

<span data-ttu-id="b3c1f-137">Neinicializované proměnné nelze použít v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="b3c1f-137">You cannot use uninitialized variables in C#.</span></span> <span data-ttu-id="b3c1f-138">Můžete inicializovat proměnné s výchozí hodnotou jeho typu.</span><span class="sxs-lookup"><span data-stu-id="b3c1f-138">You can initialize a variable with the default value of its type.</span></span> <span data-ttu-id="b3c1f-139">Také vám pomůže výchozí hodnota typu zadat výchozí hodnotu z metody [nepovinný argument](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments).</span><span class="sxs-lookup"><span data-stu-id="b3c1f-139">You also can use the default value of a type to specify the default value of a method's [optional argument](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments).</span></span>

<span data-ttu-id="b3c1f-140">Použití [výchozí hodnota výrazu](../../programming-guide/statements-expressions-operators/default-value-expressions.md) vytvoří výchozí hodnota typu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b3c1f-140">Use the [default value expression](../../programming-guide/statements-expressions-operators/default-value-expressions.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="b3c1f-141">Od verze C# 7.1, můžete použít [ `default` literálu](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) inicializace proměnné s výchozí hodnotou typu:</span><span class="sxs-lookup"><span data-stu-id="b3c1f-141">Beginning with C# 7.1, you can use the [`default` literal](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="b3c1f-142">Jak ukazuje následující příklad vytvoří výchozí hodnota typu hodnoty, můžete použít také výchozí konstruktor nebo implicitní výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="b3c1f-142">You also can use the default constructor or the implicit default constructor to produce the default value of a value type, as the following example shows.</span></span> <span data-ttu-id="b3c1f-143">Další informace o konstruktorech naleznete v tématu [konstruktory](../../programming-guide/classes-and-structs/constructors.md) článku.</span><span class="sxs-lookup"><span data-stu-id="b3c1f-143">For more information about constructors, see the [Constructors](../../programming-guide/classes-and-structs/constructors.md) article.</span></span>

```csharp
int a = new int();
```

<span data-ttu-id="b3c1f-144">Zadejte výchozí hodnotu kterékoli [odkazovat na typ](reference-types.md) je `null`.</span><span class="sxs-lookup"><span data-stu-id="b3c1f-144">The default value of any [reference type](reference-types.md) is `null`.</span></span> <span data-ttu-id="b3c1f-145">Výchozí hodnota [typ připouštějící hodnotu Null](../../programming-guide/nullable-types/index.md) u kterého je instance <xref:System.Nullable%601.HasValue%2A> vlastnost `false` a <xref:System.Nullable%601.Value%2A> vlastnost není definována.</span><span class="sxs-lookup"><span data-stu-id="b3c1f-145">The default value of a [nullable type](../../programming-guide/nullable-types/index.md) is an instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3c1f-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3c1f-146">See also</span></span>

- [<span data-ttu-id="b3c1f-147">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b3c1f-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b3c1f-148">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b3c1f-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b3c1f-149">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b3c1f-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b3c1f-150">Referenční tabulky pro typy</span><span class="sxs-lookup"><span data-stu-id="b3c1f-150">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="b3c1f-151">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="b3c1f-151">Value types</span></span>](value-types.md)
- [<span data-ttu-id="b3c1f-152">Tabulka typů hodnot</span><span class="sxs-lookup"><span data-stu-id="b3c1f-152">Value types table</span></span>](value-types-table.md)
- [<span data-ttu-id="b3c1f-153">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="b3c1f-153">Built-in types table</span></span>](built-in-types-table.md)
