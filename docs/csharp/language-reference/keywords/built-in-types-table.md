---
title: Tabulka předdefinovaných typů (referenční dokumentace jazyka C#)
description: Klíčová slova pro předdefinované typy jazyka C#
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: fd9ba878d77bdb219542db55bb38023c60c7bec4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507309"
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="34677-103">Tabulka předdefinovaných typů (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="34677-103">Built-in types table (C# Reference)</span></span>

<span data-ttu-id="34677-104">V následující tabulce jsou uvedeny klíčová slova pro vestavěné C# typy, které jsou aliasy předdefinovaných typů v <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="34677-104">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace.</span></span>  
  
|<span data-ttu-id="34677-105">Typ jazyka C#</span><span class="sxs-lookup"><span data-stu-id="34677-105">C# type</span></span>|<span data-ttu-id="34677-106">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="34677-106">.NET type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="34677-107">bool</span><span class="sxs-lookup"><span data-stu-id="34677-107">bool</span></span>](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[<span data-ttu-id="34677-108">byte</span><span class="sxs-lookup"><span data-stu-id="34677-108">byte</span></span>](byte.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[<span data-ttu-id="34677-109">sbyte</span><span class="sxs-lookup"><span data-stu-id="34677-109">sbyte</span></span>](sbyte.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[<span data-ttu-id="34677-110">char</span><span class="sxs-lookup"><span data-stu-id="34677-110">char</span></span>](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[<span data-ttu-id="34677-111">decimal</span><span class="sxs-lookup"><span data-stu-id="34677-111">decimal</span></span>](decimal.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[<span data-ttu-id="34677-112">double</span><span class="sxs-lookup"><span data-stu-id="34677-112">double</span></span>](double.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[<span data-ttu-id="34677-113">float</span><span class="sxs-lookup"><span data-stu-id="34677-113">float</span></span>](float.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[<span data-ttu-id="34677-114">int</span><span class="sxs-lookup"><span data-stu-id="34677-114">int</span></span>](int.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[<span data-ttu-id="34677-115">uint</span><span class="sxs-lookup"><span data-stu-id="34677-115">uint</span></span>](uint.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[<span data-ttu-id="34677-116">long</span><span class="sxs-lookup"><span data-stu-id="34677-116">long</span></span>](long.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[<span data-ttu-id="34677-117">ulong</span><span class="sxs-lookup"><span data-stu-id="34677-117">ulong</span></span>](ulong.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[<span data-ttu-id="34677-118">object</span><span class="sxs-lookup"><span data-stu-id="34677-118">object</span></span>](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[<span data-ttu-id="34677-119">short</span><span class="sxs-lookup"><span data-stu-id="34677-119">short</span></span>](short.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[<span data-ttu-id="34677-120">ushort</span><span class="sxs-lookup"><span data-stu-id="34677-120">ushort</span></span>](ushort.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[<span data-ttu-id="34677-121">string</span><span class="sxs-lookup"><span data-stu-id="34677-121">string</span></span>](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a><span data-ttu-id="34677-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34677-122">Remarks</span></span>

<span data-ttu-id="34677-123">Všechny typy v tabulce, s výjimkou `object` a `string`, jsou označovány jako jednoduché typy.</span><span class="sxs-lookup"><span data-stu-id="34677-123">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>  
  
<span data-ttu-id="34677-124">Jazyce C# zadejte klíčová slova a jejich aliasy jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="34677-124">The C# type keywords and their aliases are interchangeable.</span></span> <span data-ttu-id="34677-125">Například je možné deklarovat celočíselné proměnné pomocí některé z následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="34677-125">For example, you can declare an integer variable by using either of the following declarations:</span></span>  

```csharp
int x = 123;
System.Int32 y = 123;
```

<span data-ttu-id="34677-126">Použití [typeof](typeof.md) operátor zobrazíte <xref:System.Type?displayProperty=nameWithType> instanci, která představuje zadaný typ:</span><span class="sxs-lookup"><span data-stu-id="34677-126">Use the [typeof](typeof.md) operator to get the <xref:System.Type?displayProperty=nameWithType> instance that represents the specified type:</span></span>

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a><span data-ttu-id="34677-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34677-127">See also</span></span>

- [<span data-ttu-id="34677-128">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="34677-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="34677-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="34677-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="34677-130">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="34677-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="34677-131">Referenční tabulky pro typy</span><span class="sxs-lookup"><span data-stu-id="34677-131">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="34677-132">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="34677-132">Value types</span></span>](value-types.md)
- [<span data-ttu-id="34677-133">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="34677-133">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="34677-134">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="34677-134">Default values table</span></span>](default-values-table.md)
- [<span data-ttu-id="34677-135">dynamic</span><span class="sxs-lookup"><span data-stu-id="34677-135">dynamic</span></span>](dynamic.md)
