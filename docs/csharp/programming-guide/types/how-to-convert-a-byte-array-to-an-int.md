---
title: "Postupy: Převedení pole bajtů na typ int (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ee51cd94e961c7274286c812cb6900d26c6ce033
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="3b315-102">Postupy: Převedení pole bajtů na typ int (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="3b315-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>
<span data-ttu-id="3b315-103">Tento příklad ukazuje, jak používat <xref:System.BitConverter> třída pro převod pole bajtů, které mají [int](../../../csharp/language-reference/keywords/int.md) a zpět na pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="3b315-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../../csharp/language-reference/keywords/int.md) and back to an array of bytes.</span></span> <span data-ttu-id="3b315-104">Možná budete muset převést z bajtů na typ předdefinované po přečtení bajtů mimo síť, například.</span><span class="sxs-lookup"><span data-stu-id="3b315-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="3b315-105">Kromě [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) metoda příklad následující tabulka uvádí metody v <xref:System.BitConverter> třídu, která převést bajtů (z pole bajtů) na jiné předdefinované typy.</span><span class="sxs-lookup"><span data-stu-id="3b315-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>  
  
|<span data-ttu-id="3b315-106">Typ vrácený</span><span class="sxs-lookup"><span data-stu-id="3b315-106">Type returned</span></span>|<span data-ttu-id="3b315-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="3b315-107">Method</span></span>|  
|-------------------|------------|  
|`bool`|<span data-ttu-id="3b315-108">[ToBoolean (Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3b315-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|  
|`char`|<span data-ttu-id="3b315-109">[ToChar (Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3b315-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|  
|`double`|<span data-ttu-id="3b315-110">[ToDouble (Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3b315-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|  
|`short`|<span data-ttu-id="3b315-111">[ToInt16 (Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3b315-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|  
|`int`|<span data-ttu-id="3b315-112">[ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3b315-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|  
|`long`|<span data-ttu-id="3b315-113">[ToInt64 (Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3b315-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|  
|`float`|<span data-ttu-id="3b315-114">[ToSingle (Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3b315-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|  
|`ushort`|<span data-ttu-id="3b315-115">[ToUInt16 (Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3b315-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|  
|`uint`|<span data-ttu-id="3b315-116">[ToUInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3b315-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|  
|`ulong`|<span data-ttu-id="3b315-117">[ToUInt64 (Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3b315-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3b315-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b315-118">Example</span></span>  
 <span data-ttu-id="3b315-119">Tento příklad inicializuje pole bajtů, pokud je architektura počítačových little endian obrátí pole (který je nejméně významný bajt je uložen) a potom zavolá [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))způsobů, jak převést čtyři bajtů v poli, aby `int`.</span><span class="sxs-lookup"><span data-stu-id="3b315-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="3b315-120">Druhý argument [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) Určuje počáteční index pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="3b315-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b315-121">Výstup se můžou lišit v závislosti na endianess architektury vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="3b315-121">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="3b315-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b315-122">Example</span></span>  
 <span data-ttu-id="3b315-123">V tomto příkladu <xref:System.BitConverter.GetBytes%28System.Int32%29> metodu <xref:System.BitConverter> třídy se nazývá převést `int` na pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="3b315-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b315-124">Výstup se můžou lišit v závislosti na endianess architektury vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="3b315-124">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3b315-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b315-125">See Also</span></span>  
 <xref:System.BitConverter>  
 <xref:System.BitConverter.IsLittleEndian>  
 [<span data-ttu-id="3b315-126">Typy</span><span class="sxs-lookup"><span data-stu-id="3b315-126">Types</span></span>](../../../csharp/programming-guide/types/index.md)
