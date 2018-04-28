---
title: Primitivní typy (F#)
description: 'Zjistit základní primitivní typy, které se používají v jazyce F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 7832151ee211f56547ecad98fc31f1454cb18870
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="primitive-types"></a><span data-ttu-id="02083-103">Primitivní typy</span><span class="sxs-lookup"><span data-stu-id="02083-103">Primitive Types</span></span>

<span data-ttu-id="02083-104">Toto téma obsahuje základní primitivní typy, které se používají v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="02083-104">This topic lists the fundamental primitive types that are used in the F# language.</span></span> <span data-ttu-id="02083-105">Poskytuje taky odpovídající typy .NET a minimální a maximální hodnoty pro každý typ.</span><span class="sxs-lookup"><span data-stu-id="02083-105">It also provides the corresponding .NET types and the minimum and maximum values for each type.</span></span>

## <a name="summary-of-primitive-types"></a><span data-ttu-id="02083-106">Souhrn primitivní typy</span><span class="sxs-lookup"><span data-stu-id="02083-106">Summary of Primitive Types</span></span>
<span data-ttu-id="02083-107">Následující tabulka shrnuje vlastnosti primitivních typů F #.</span><span class="sxs-lookup"><span data-stu-id="02083-107">The following table summarizes the properties of the primitive F# types.</span></span>

|<span data-ttu-id="02083-108">Typ</span><span class="sxs-lookup"><span data-stu-id="02083-108">Type</span></span>|<span data-ttu-id="02083-109">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="02083-109">.NET type</span></span>|<span data-ttu-id="02083-110">Popis</span><span class="sxs-lookup"><span data-stu-id="02083-110">Description</span></span>|
|----|---------|-----------|
|`bool`|`System.Boolean`|<span data-ttu-id="02083-111">Možné hodnoty jsou `true` a `false`.</span><span class="sxs-lookup"><span data-stu-id="02083-111">Possible values are `true` and `false`.</span></span>|
|`byte`|`System.Byte`|<span data-ttu-id="02083-112">Hodnoty od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="02083-112">Values from 0 to 255.</span></span>|
|`sbyte`|`System.SByte`|<span data-ttu-id="02083-113">Hodnoty z -128 127 znaků.</span><span class="sxs-lookup"><span data-stu-id="02083-113">Values from -128 to 127.</span></span>|
|`int16`|`System.Int16`|<span data-ttu-id="02083-114">Hodnoty z-32 768 do 32 767.</span><span class="sxs-lookup"><span data-stu-id="02083-114">Values from -32768 to 32767.</span></span>|
|`uint16`|`System.UInt16`|<span data-ttu-id="02083-115">Hodnoty od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="02083-115">Values from 0 to 65535.</span></span>|
|`int`|`System.Int32`|<span data-ttu-id="02083-116">Hodnoty z-2,147,483,648 na 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="02083-116">Values from -2,147,483,648 to 2,147,483,647.</span></span>|
|`uint32`|`System.UInt32`|<span data-ttu-id="02083-117">Hodnoty od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="02083-117">Values from 0 to 4,294,967,295.</span></span>|
|`int64`|`System.Int64`|<span data-ttu-id="02083-118">Hodnoty z-9,223,372,036,854,775,808 9,223,372,036,854,775,807.</span><span class="sxs-lookup"><span data-stu-id="02083-118">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|
|`uint64`|`System.UInt64`|<span data-ttu-id="02083-119">Hodnoty od 0 do 18,446,744,073,709,551,615.</span><span class="sxs-lookup"><span data-stu-id="02083-119">Values from 0 to 18,446,744,073,709,551,615.</span></span>|
|`nativeint`|`System.IntPtr`|<span data-ttu-id="02083-120">Nativní ukazatel jako znaménkem.</span><span class="sxs-lookup"><span data-stu-id="02083-120">A native pointer as a signed integer.</span></span>|
|`unativeint`|`System.UIntPtr`|<span data-ttu-id="02083-121">Nativní ukazatel jako celé číslo bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="02083-121">A native pointer as an unsigned integer.</span></span>|
|`char`|`System.Char`|<span data-ttu-id="02083-122">Hodnoty znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="02083-122">Unicode character values.</span></span>|
|`string`|`System.String`|<span data-ttu-id="02083-123">Text v kódu Unicode.</span><span class="sxs-lookup"><span data-stu-id="02083-123">Unicode text.</span></span>|
|`decimal`|`System.Decimal`|<span data-ttu-id="02083-124">Plovoucí bodu datový typ, který obsahuje alespoň 28 platných číslic.</span><span class="sxs-lookup"><span data-stu-id="02083-124">A floating point data type that has at least 28 significant digits.</span></span>|
|`unit`|<span data-ttu-id="02083-125">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="02083-125">not applicable</span></span>|<span data-ttu-id="02083-126">Ukazuje na nepřítomnost skutečnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="02083-126">Indicates the absence of an actual value.</span></span> <span data-ttu-id="02083-127">Typ s jedinou hodnotou formální, které je označené `()`.</span><span class="sxs-lookup"><span data-stu-id="02083-127">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="02083-128">Hodnotu jednotek `()`, se často používá jako zástupný znak, kde je potřeba hodnotu, ale je k dispozici žádná skutečná hodnota nebo smysl.</span><span class="sxs-lookup"><span data-stu-id="02083-128">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|
|`void`|`System.Void`|<span data-ttu-id="02083-129">Označuje žádný typ nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="02083-129">Indicates no type or value.</span></span>|
|`float32, single`|`System.Single`|<span data-ttu-id="02083-130">32-bit plovoucí bod typu.</span><span class="sxs-lookup"><span data-stu-id="02083-130">A 32-bit floating point type.</span></span>|
|`float, double`|`System.Double`|<span data-ttu-id="02083-131">64bitová verze plovoucí bod typu.</span><span class="sxs-lookup"><span data-stu-id="02083-131">A 64-bit floating point type.</span></span>|

>[!NOTE]
<span data-ttu-id="02083-132">Výpočty s celými čísly příliš velký pro typ 64bitové celé číslo můžete provádět pomocí [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) typu.</span><span class="sxs-lookup"><span data-stu-id="02083-132">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type.</span></span> <span data-ttu-id="02083-133">`bigint` není považována za primitivní typ; je zkratkou pro `System.Numerics.BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="02083-133">`bigint` is not considered a primitive type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="02083-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="02083-134">See Also</span></span>
[<span data-ttu-id="02083-135">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="02083-135">F# Language Reference</span></span>](index.md)
