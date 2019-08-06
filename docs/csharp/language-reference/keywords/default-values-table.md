---
title: Výchozí hodnoty tabulka – C# odkaz
ms.custom: seodec18
description: Zjistěte, jaké jsou výchozí hodnoty C# typů.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: d9889ce389eed73a9af0a3f72dcca6ec476cae15
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796494"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="cdae9-103">Tabulka výchozích hodnot (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="cdae9-103">Default values table (C# reference)</span></span>

<span data-ttu-id="cdae9-104">Následující tabulka ukazuje výchozí hodnoty C# typů:</span><span class="sxs-lookup"><span data-stu-id="cdae9-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="cdae9-105">type</span><span class="sxs-lookup"><span data-stu-id="cdae9-105">Type</span></span>|<span data-ttu-id="cdae9-106">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="cdae9-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="cdae9-107">Libovolný typ odkazu</span><span class="sxs-lookup"><span data-stu-id="cdae9-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="cdae9-108">Libovolný [vestavěný celočíselný numerický typ](../builtin-types/integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="cdae9-108">Any [built-in integral numeric type](../builtin-types/integral-numeric-types.md)</span></span>|<span data-ttu-id="cdae9-109">0 (nula)</span><span class="sxs-lookup"><span data-stu-id="cdae9-109">0 (zero)</span></span>|
|<span data-ttu-id="cdae9-110">Libovolný [vestavěný číselný typ s plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou</span><span class="sxs-lookup"><span data-stu-id="cdae9-110">Any [built-in floating-point numeric type](../builtin-types/floating-point-numeric-types.md)</span></span>|<span data-ttu-id="cdae9-111">0 (nula)</span><span class="sxs-lookup"><span data-stu-id="cdae9-111">0 (zero)</span></span>|
|[<span data-ttu-id="cdae9-112">bool</span><span class="sxs-lookup"><span data-stu-id="cdae9-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="cdae9-113">char</span><span class="sxs-lookup"><span data-stu-id="cdae9-113">char</span></span>](char.md)|<span data-ttu-id="cdae9-114">`'\0'`(U + 0000)</span><span class="sxs-lookup"><span data-stu-id="cdae9-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="cdae9-115">enum</span><span class="sxs-lookup"><span data-stu-id="cdae9-115">enum</span></span>](enum.md)|<span data-ttu-id="cdae9-116">Hodnota vytvořená výrazem `(E)0`, kde `E` je identifikátor výčtu.</span><span class="sxs-lookup"><span data-stu-id="cdae9-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="cdae9-117">struct</span><span class="sxs-lookup"><span data-stu-id="cdae9-117">struct</span></span>](struct.md)|<span data-ttu-id="cdae9-118">Hodnota vytvořená nastavením všech polí typu hodnoty na jejich výchozí hodnoty a všechna pole typu odkaz na `null`.</span><span class="sxs-lookup"><span data-stu-id="cdae9-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="cdae9-119">Libovolný [typ hodnoty s možnou hodnotou null](../../programming-guide/nullable-types/index.md)</span><span class="sxs-lookup"><span data-stu-id="cdae9-119">Any [nullable value type](../../programming-guide/nullable-types/index.md)</span></span>|<span data-ttu-id="cdae9-120">Instance, pro kterou <xref:System.Nullable%601.HasValue%2A> je `false` vlastnost a <xref:System.Nullable%601.Value%2A> vlastnost není definována.</span><span class="sxs-lookup"><span data-stu-id="cdae9-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="cdae9-121">Tato výchozí hodnota je také známá jako hodnota *null* typu hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="cdae9-121">That default value is also known as the *null* value of the nullable value type.</span></span>|

<span data-ttu-id="cdae9-122">Použijte [výchozí operátor](../operators/default.md) k vytvoření výchozí hodnoty typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="cdae9-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="cdae9-123">Počínaje C# 7,1 můžete použít [ `default` literál](../operators/default.md#default-literal) k inicializaci proměnné s výchozí hodnotou jeho typu:</span><span class="sxs-lookup"><span data-stu-id="cdae9-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="cdae9-124">Pro typ hodnoty, implicitní konstruktor bez parametrů vytvoří také výchozí hodnotu typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="cdae9-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a><span data-ttu-id="cdae9-125">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cdae9-125">C# language specification</span></span>

<span data-ttu-id="cdae9-126">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="cdae9-126">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="cdae9-127">Výchozí hodnoty</span><span class="sxs-lookup"><span data-stu-id="cdae9-127">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="cdae9-128">Výchozí konstruktory</span><span class="sxs-lookup"><span data-stu-id="cdae9-128">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="cdae9-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdae9-129">See also</span></span>

- [<span data-ttu-id="cdae9-130">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="cdae9-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="cdae9-131">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cdae9-131">C# keywords</span></span>](index.md)
- [<span data-ttu-id="cdae9-132">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="cdae9-132">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="cdae9-133">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="cdae9-133">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
