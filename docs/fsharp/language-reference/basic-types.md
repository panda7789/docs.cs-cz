---
title: Základní typy
description: 'Objevte základní základní typy, které se používají v jazyce F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 659ac8424c62985affcca1741e1b2a74c9c3ee8d
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557695"
---
# <a name="basic-types"></a><span data-ttu-id="ecea3-103">Základní typy</span><span class="sxs-lookup"><span data-stu-id="ecea3-103">Basic types</span></span>

<span data-ttu-id="ecea3-104">Toto téma obsahuje seznam základních typů, které jsou definovány v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="ecea3-104">This topic lists the basic types that are defined in the F# language.</span></span> <span data-ttu-id="ecea3-105">Tyto typy jsou nejdůležitější v jazyce F #, který vytváří základ skoro každého programu F #.</span><span class="sxs-lookup"><span data-stu-id="ecea3-105">These types are the most fundamental in F#, forming the basis of nearly every F# program.</span></span> <span data-ttu-id="ecea3-106">Jsou nadmnožinou primitivních typů .NET.</span><span class="sxs-lookup"><span data-stu-id="ecea3-106">They are a superset of .NET primitive types.</span></span>

|<span data-ttu-id="ecea3-107">Typ</span><span class="sxs-lookup"><span data-stu-id="ecea3-107">Type</span></span>|<span data-ttu-id="ecea3-108">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="ecea3-108">.NET type</span></span>|<span data-ttu-id="ecea3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ecea3-109">Description</span></span>|<span data-ttu-id="ecea3-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ecea3-110">Example</span></span>|
|----|---------|-----------|-------|
|`bool`|<xref:System.Boolean>|<span data-ttu-id="ecea3-111">Možné hodnoty jsou `true` a `false` .</span><span class="sxs-lookup"><span data-stu-id="ecea3-111">Possible values are `true` and `false`.</span></span>|`true`/`false`|
|`byte`|<xref:System.Byte>|<span data-ttu-id="ecea3-112">Hodnoty od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="ecea3-112">Values from 0 to 255.</span></span>|`1uy`|
|`sbyte`|<xref:System.SByte>|<span data-ttu-id="ecea3-113">Hodnoty od-128 do 127.</span><span class="sxs-lookup"><span data-stu-id="ecea3-113">Values from -128 to 127.</span></span>|`1y`|
|`int16`|<xref:System.Int16>|<span data-ttu-id="ecea3-114">Hodnoty od-32768 do 32767.</span><span class="sxs-lookup"><span data-stu-id="ecea3-114">Values from -32768 to 32767.</span></span>|`1s`|
|`uint16`|<xref:System.UInt16>|<span data-ttu-id="ecea3-115">Hodnoty od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="ecea3-115">Values from 0 to 65535.</span></span>|`1us`|
|`int`|<xref:System.Int32>|<span data-ttu-id="ecea3-116">Hodnoty od-2 147 483 648 do 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="ecea3-116">Values from -2,147,483,648 to 2,147,483,647.</span></span>|`1`|
|`uint`|<xref:System.UInt32>|<span data-ttu-id="ecea3-117">Hodnoty od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="ecea3-117">Values from 0 to 4,294,967,295.</span></span>|`1u`|
|`int64`|<xref:System.Int64>|<span data-ttu-id="ecea3-118">Hodnoty od-9223372036854775808 do 9 223 372 036 854 775 807.</span><span class="sxs-lookup"><span data-stu-id="ecea3-118">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|`1L`|
|`uint64`|<xref:System.UInt64>|<span data-ttu-id="ecea3-119">Hodnoty od 0 do 18446744073709551615.</span><span class="sxs-lookup"><span data-stu-id="ecea3-119">Values from 0 to 18,446,744,073,709,551,615.</span></span>|`1UL`|
|`nativeint`|<xref:System.IntPtr>|<span data-ttu-id="ecea3-120">Nativní ukazatel jako celé číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="ecea3-120">A native pointer as a signed integer.</span></span>|`nativeint 1`|
|`unativeint`|<xref:System.UIntPtr>|<span data-ttu-id="ecea3-121">Nativní ukazatel jako unsigned integer.</span><span class="sxs-lookup"><span data-stu-id="ecea3-121">A native pointer as an unsigned integer.</span></span>|`unativeint 1`|
|`decimal`|<xref:System.Decimal>|<span data-ttu-id="ecea3-122">Datový typ s plovoucí desetinnou čárkou, který má alespoň 28 platných číslic.</span><span class="sxs-lookup"><span data-stu-id="ecea3-122">A floating point data type that has at least 28 significant digits.</span></span>|`1.0`|
|<span data-ttu-id="ecea3-123">`float`, `double`</span><span class="sxs-lookup"><span data-stu-id="ecea3-123">`float`, `double`</span></span>|<xref:System.Double>|<span data-ttu-id="ecea3-124">64 typ s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="ecea3-124">A 64-bit floating point type.</span></span>|`1.0`|
|<span data-ttu-id="ecea3-125">`float32`, `single`</span><span class="sxs-lookup"><span data-stu-id="ecea3-125">`float32`, `single`</span></span>|<xref:System.Single>|<span data-ttu-id="ecea3-126">32 typ s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="ecea3-126">A 32-bit floating point type.</span></span>|`1.0f`|
|`char`|<xref:System.Char>|<span data-ttu-id="ecea3-127">Hodnoty znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="ecea3-127">Unicode character values.</span></span>|`'c'`|
|`string`|<xref:System.String>|<span data-ttu-id="ecea3-128">Text v kódu Unicode.</span><span class="sxs-lookup"><span data-stu-id="ecea3-128">Unicode text.</span></span>|`"str"`|
|`unit`|<span data-ttu-id="ecea3-129">nelze použít</span><span class="sxs-lookup"><span data-stu-id="ecea3-129">not applicable</span></span>|<span data-ttu-id="ecea3-130">Označuje absenci skutečné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ecea3-130">Indicates the absence of an actual value.</span></span> <span data-ttu-id="ecea3-131">Typ má pouze jednu formální hodnotu, která je označena `()` .</span><span class="sxs-lookup"><span data-stu-id="ecea3-131">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="ecea3-132">Hodnota jednotky, `()` , se často používá jako zástupný symbol, kde je hodnota potřebná, ale není k dispozici žádná skutečná hodnota, ani smysl.</span><span class="sxs-lookup"><span data-stu-id="ecea3-132">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|`()`|

> [!NOTE]
> <span data-ttu-id="ecea3-133">Můžete provádět výpočty s celými čísly, která jsou příliš velká pro 64 celočíselný typ Integer pomocí typu [bigint](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-bigint.html) .</span><span class="sxs-lookup"><span data-stu-id="ecea3-133">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-bigint.html) type.</span></span> <span data-ttu-id="ecea3-134">`bigint` není považován za základní typ; Jedná se o zkratku pro `System.Numerics.BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="ecea3-134">`bigint` is not considered a basic type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ecea3-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecea3-135">See also</span></span>

- [<span data-ttu-id="ecea3-136">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="ecea3-136">F# Language Reference</span></span>](index.md)
