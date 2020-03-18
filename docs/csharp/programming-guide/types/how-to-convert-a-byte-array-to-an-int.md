---
title: Jak převést bajtové pole na int - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 9f477649dba1b42d7a10d521c010977707daf3ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698752"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="113e1-102">Jak převést bajtové pole na int (C# Programovací průvodce)</span><span class="sxs-lookup"><span data-stu-id="113e1-102">How to convert a byte array to an int (C# Programming Guide)</span></span>

<span data-ttu-id="113e1-103">Tento příklad ukazuje, jak <xref:System.BitConverter> použít třídu převést pole bajtů [na int](../../language-reference/builtin-types/integral-numeric-types.md) a zpět na pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="113e1-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="113e1-104">Pravděpodobně bude pravděpodobně muset převést z bajtů na vestavěný datový typ po čtení bajtů mimo síť, například.</span><span class="sxs-lookup"><span data-stu-id="113e1-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="113e1-105">Kromě metody [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) v příkladu jsou v <xref:System.BitConverter> následující tabulce uvedeny metody ve třídě, které převádějí bajty (z pole bajtů) na jiné předdefinované typy.</span><span class="sxs-lookup"><span data-stu-id="113e1-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>

|<span data-ttu-id="113e1-106">Typ vrácen</span><span class="sxs-lookup"><span data-stu-id="113e1-106">Type returned</span></span>|<span data-ttu-id="113e1-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="113e1-107">Method</span></span>|
|-------------------|------------|
|`bool`|<span data-ttu-id="113e1-108">[ToBoolean(Bajt\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="113e1-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|
|`char`|<span data-ttu-id="113e1-109">[ToChar(Bajt\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="113e1-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|
|`double`|<span data-ttu-id="113e1-110">[ToDouble (Bajt\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="113e1-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|
|`short`|<span data-ttu-id="113e1-111">[ToInt16(Bajt\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="113e1-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|
|`int`|<span data-ttu-id="113e1-112">[ToInt32(Bajt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="113e1-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|
|`long`|<span data-ttu-id="113e1-113">[ToInt64(Bajt\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="113e1-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|
|`float`|<span data-ttu-id="113e1-114">[ToSingle(Bajt\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="113e1-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|
|`ushort`|<span data-ttu-id="113e1-115">[ToUInt16(Bajt\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="113e1-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|
|`uint`|<span data-ttu-id="113e1-116">[ToUInt32(Bajt\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="113e1-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|
|`ulong`|<span data-ttu-id="113e1-117">[ToUInt64(Bajt\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="113e1-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|

## <a name="example"></a><span data-ttu-id="113e1-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="113e1-118">Example</span></span>

<span data-ttu-id="113e1-119">Tento příklad inicializuje pole bajtů, obrátí pole, pokud je architektura počítače little-endian (to znamená, že je nejprve uložen nejméně významný bajt), a pak zavolá metodu [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) pro převod čtyř bajtů v poli na . `int`</span><span class="sxs-lookup"><span data-stu-id="113e1-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="113e1-120">Druhý argument [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) určuje počáteční index pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="113e1-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="113e1-121">Výstup se může lišit v závislosti na endianness architektury počítače.</span><span class="sxs-lookup"><span data-stu-id="113e1-121">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a><span data-ttu-id="113e1-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="113e1-122">Example</span></span>

<span data-ttu-id="113e1-123">V tomto příkladu <xref:System.BitConverter.GetBytes%28System.Int32%29> je <xref:System.BitConverter> metoda třídy `int` volána k převodu na pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="113e1-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="113e1-124">Výstup se může lišit v závislosti na endianness architektury počítače.</span><span class="sxs-lookup"><span data-stu-id="113e1-124">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a><span data-ttu-id="113e1-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="113e1-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="113e1-126">Typy</span><span class="sxs-lookup"><span data-stu-id="113e1-126">Types</span></span>](./index.md)
