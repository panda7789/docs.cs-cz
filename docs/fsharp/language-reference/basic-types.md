---
title: 'Základní typy (F #)'
description: 'Objevte základní typy, které se používají v jazyce F #.'
ms.date: 07/09/2018
ms.openlocfilehash: 8f948d066323527b09b1d3f9f4167b95b1c875cf
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45991009"
---
# <a name="basic-types"></a><span data-ttu-id="cea38-103">Základní typy</span><span class="sxs-lookup"><span data-stu-id="cea38-103">Basic types</span></span>

<span data-ttu-id="cea38-104">Toto téma obsahuje základní typy, které jsou definovány v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="cea38-104">This topic lists the basic types that are defined in the F# language.</span></span> <span data-ttu-id="cea38-105">Tyto typy jsou nejdůležitější v jazyce F #, které tvoří základ téměř každý program F #.</span><span class="sxs-lookup"><span data-stu-id="cea38-105">These types are the most fundamental in F#, forming the basis of nearly every F# program.</span></span> <span data-ttu-id="cea38-106">Jsou množinou primitivní typy .NET.</span><span class="sxs-lookup"><span data-stu-id="cea38-106">They are a superset of .NET primitive types.</span></span>

|<span data-ttu-id="cea38-107">Typ</span><span class="sxs-lookup"><span data-stu-id="cea38-107">Type</span></span>|<span data-ttu-id="cea38-108">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="cea38-108">.NET type</span></span>|<span data-ttu-id="cea38-109">Popis</span><span class="sxs-lookup"><span data-stu-id="cea38-109">Description</span></span>|
|----|---------|-----------|
|`bool`|<xref:System.Boolean>|<span data-ttu-id="cea38-110">Možné hodnoty jsou `true` a `false`.</span><span class="sxs-lookup"><span data-stu-id="cea38-110">Possible values are `true` and `false`.</span></span>|
|`byte`|<xref:System.Byte>|<span data-ttu-id="cea38-111">Hodnoty od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="cea38-111">Values from 0 to 255.</span></span>|
|`sbyte`|<xref:System.SByte>|<span data-ttu-id="cea38-112">Hodnoty -128 až 127.</span><span class="sxs-lookup"><span data-stu-id="cea38-112">Values from -128 to 127.</span></span>|
|`int16`|<xref:System.Int16>|<span data-ttu-id="cea38-113">Hodnoty od-32 768 do 32767.</span><span class="sxs-lookup"><span data-stu-id="cea38-113">Values from -32768 to 32767.</span></span>|
|`uint16`|<xref:System.UInt16>|<span data-ttu-id="cea38-114">Hodnoty od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="cea38-114">Values from 0 to 65535.</span></span>|
|`int`|<xref:System.Int32>|<span data-ttu-id="cea38-115">Hodnoty z-2,147,483,648 do 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="cea38-115">Values from -2,147,483,648 to 2,147,483,647.</span></span>|
|`uint32`|<xref:System.UInt32>|<span data-ttu-id="cea38-116">Hodnoty od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="cea38-116">Values from 0 to 4,294,967,295.</span></span>|
|`int64`|<xref:System.Int64>|<span data-ttu-id="cea38-117">Hodnoty z-9,223,372,036,854,775,808 9,223,372,036,854,775,807.</span><span class="sxs-lookup"><span data-stu-id="cea38-117">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|
|`uint64`|<xref:System.UInt64>|<span data-ttu-id="cea38-118">Hodnoty od 0 do 18,446,744,073,709,551,615.</span><span class="sxs-lookup"><span data-stu-id="cea38-118">Values from 0 to 18,446,744,073,709,551,615.</span></span>|
|`nativeint`|<xref:System.IntPtr>|<span data-ttu-id="cea38-119">Nativní ukazatel jako celé číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="cea38-119">A native pointer as a signed integer.</span></span>|
|`unativeint`|<xref:System.UIntPtr>|<span data-ttu-id="cea38-120">Nativní ukazatel jako celé číslo bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="cea38-120">A native pointer as an unsigned integer.</span></span>|
|`char`|<xref:System.Char>|<span data-ttu-id="cea38-121">Hodnoty znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="cea38-121">Unicode character values.</span></span>|
|`string`|<xref:System.String>|<span data-ttu-id="cea38-122">Text v kódu Unicode.</span><span class="sxs-lookup"><span data-stu-id="cea38-122">Unicode text.</span></span>|
|`decimal`|<xref:System.Decimal>|<span data-ttu-id="cea38-123">S plovoucí desetinnou čárkou datový typ, který má alespoň 28 platných číslic.</span><span class="sxs-lookup"><span data-stu-id="cea38-123">A floating point data type that has at least 28 significant digits.</span></span>|
|`unit`|<span data-ttu-id="cea38-124">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="cea38-124">not applicable</span></span>|<span data-ttu-id="cea38-125">Ukazuje na nepřítomnost skutečnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cea38-125">Indicates the absence of an actual value.</span></span> <span data-ttu-id="cea38-126">Typ má pouze jeden formální hodnotu, která je označena `()`.</span><span class="sxs-lookup"><span data-stu-id="cea38-126">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="cea38-127">Hodnota jednotka `()`, se často používá jako zástupný symbol, kdy je potřeba hodnotu, ale žádná skutečná hodnota je k dispozici nebo dává smysl.</span><span class="sxs-lookup"><span data-stu-id="cea38-127">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|
|`void`|<xref:System.Void>|<span data-ttu-id="cea38-128">Označuje žádný typ nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="cea38-128">Indicates no type or value.</span></span>|
|<span data-ttu-id="cea38-129">`float32`, `single`</span><span class="sxs-lookup"><span data-stu-id="cea38-129">`float32`, `single`</span></span>|<xref:System.Single>|<span data-ttu-id="cea38-130">Bod typ s plovoucí desetinnou čárkou 32-bit.</span><span class="sxs-lookup"><span data-stu-id="cea38-130">A 32-bit floating point type.</span></span>|
|<span data-ttu-id="cea38-131">`float`, `double`</span><span class="sxs-lookup"><span data-stu-id="cea38-131">`float`, `double`</span></span>|<xref:System.Double>|<span data-ttu-id="cea38-132">Bod typ s plovoucí desetinnou čárkou 64bitové.</span><span class="sxs-lookup"><span data-stu-id="cea38-132">A 64-bit floating point type.</span></span>|

>[!NOTE]
<span data-ttu-id="cea38-133">Můžete provést výpočty s celými čísly příliš velký pro 64bitovou celočíselnou hodnotu typu pomocí [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) typu.</span><span class="sxs-lookup"><span data-stu-id="cea38-133">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type.</span></span> <span data-ttu-id="cea38-134">`bigint` není považováno za základní typ; je zkratka pro `System.Numerics.BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="cea38-134">`bigint` is not considered a basic type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="cea38-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cea38-135">See also</span></span>

- [<span data-ttu-id="cea38-136">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="cea38-136">F# Language Reference</span></span>](index.md)
