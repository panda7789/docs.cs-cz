---
title: 'Postupy: převod pole bajtů na programový průvodce pro celé C# číslo'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 96507f03a3d64b96ef6059a92459bfc7fa854372
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395690"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="f5133-102">Postupy: Převedení pole bajtů na typ int (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f5133-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>

<span data-ttu-id="f5133-103">Tento příklad ukazuje, jak použít třídu <xref:System.BitConverter> k převedení pole bajtů na typ [int](../../language-reference/builtin-types/integral-numeric-types.md) a zpět na pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="f5133-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="f5133-104">Po čtení bajtů z sítě může být nutné převést bajty z bajtů na vestavěný datový typ.</span><span class="sxs-lookup"><span data-stu-id="f5133-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="f5133-105">Kromě metody [ToInt32 – (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) v příkladu v následující tabulce jsou uvedeny metody třídy <xref:System.BitConverter>, které převádějí bajty (z pole bajtů) na jiné předdefinované typy.</span><span class="sxs-lookup"><span data-stu-id="f5133-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>

|<span data-ttu-id="f5133-106">Vrácený typ</span><span class="sxs-lookup"><span data-stu-id="f5133-106">Type returned</span></span>|<span data-ttu-id="f5133-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="f5133-107">Method</span></span>|
|-------------------|------------|
|`bool`|<span data-ttu-id="f5133-108">[ToBoolean (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f5133-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|
|`char`|<span data-ttu-id="f5133-109">[ToChar – (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f5133-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|
|`double`|<span data-ttu-id="f5133-110">[ToDouble – (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f5133-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|
|`short`|<span data-ttu-id="f5133-111">[Toint16 – (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f5133-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|
|`int`|<span data-ttu-id="f5133-112">[Toint32 – (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f5133-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|
|`long`|<span data-ttu-id="f5133-113">[Toint64 – (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f5133-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|
|`float`|<span data-ttu-id="f5133-114">[ToSingle – (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f5133-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|
|`ushort`|<span data-ttu-id="f5133-115">[Touint16 – (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f5133-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|
|`uint`|<span data-ttu-id="f5133-116">[Touint32 – (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f5133-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|
|`ulong`|<span data-ttu-id="f5133-117">[Touint64 – (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f5133-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|

## <a name="example"></a><span data-ttu-id="f5133-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5133-118">Example</span></span>

<span data-ttu-id="f5133-119">Tento příklad inicializuje pole bajtů, obrátí pole, pokud má architektura počítače Little-endian (to znamená, že je nejdříve uložený nejnižší bajt) a pak zavolá metodu [ToInt32 – (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) pro převod čtyř bajtů v pole do `int`.</span><span class="sxs-lookup"><span data-stu-id="f5133-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="f5133-120">Druhý argument [ToInt32 – (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) Určuje počáteční index pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="f5133-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="f5133-121">Výstup se může lišit v závislosti na endianess architektury počítače.</span><span class="sxs-lookup"><span data-stu-id="f5133-121">The output may differ depending on the endianess of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a><span data-ttu-id="f5133-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5133-122">Example</span></span>

<span data-ttu-id="f5133-123">V tomto příkladu je volána metoda <xref:System.BitConverter.GetBytes%28System.Int32%29> třídy <xref:System.BitConverter> pro převedení `int` na pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="f5133-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="f5133-124">Výstup se může lišit v závislosti na endianess architektury počítače.</span><span class="sxs-lookup"><span data-stu-id="f5133-124">The output may differ depending on the endianess of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a><span data-ttu-id="f5133-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5133-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="f5133-126">Typy</span><span class="sxs-lookup"><span data-stu-id="f5133-126">Types</span></span>](./index.md)
