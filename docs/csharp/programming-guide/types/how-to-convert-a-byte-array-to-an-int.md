---
title: 'Postupy: Převedení pole bajtů na typ int - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 39a34539fbd9623d4ae3c6bddf55e50e3502db61
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692347"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="6631f-102">Postupy: Převedení pole bajtů na typ int (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="6631f-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>
<span data-ttu-id="6631f-103">Tento příklad ukazuje, jak používat <xref:System.BitConverter> pro převod pole bajtů, které mají [int](../../../csharp/language-reference/keywords/int.md) a zpět na pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="6631f-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../../csharp/language-reference/keywords/int.md) and back to an array of bytes.</span></span> <span data-ttu-id="6631f-104">Bude pravděpodobně nutné převést bajty integrované datový typ po třeba číst bajty připojen k síti.</span><span class="sxs-lookup"><span data-stu-id="6631f-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="6631f-105">Kromě [ToInt32 – (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) metoda v příkladu v následující tabulce jsou uvedeny metody v <xref:System.BitConverter> třídu, která převést bajty (z pole bajtů) do ostatních předdefinovaných typů.</span><span class="sxs-lookup"><span data-stu-id="6631f-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>  
  
|<span data-ttu-id="6631f-106">Typ vrácený</span><span class="sxs-lookup"><span data-stu-id="6631f-106">Type returned</span></span>|<span data-ttu-id="6631f-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="6631f-107">Method</span></span>|  
|-------------------|------------|  
|`bool`|<span data-ttu-id="6631f-108">[ToBoolean (Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6631f-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|  
|`char`|<span data-ttu-id="6631f-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6631f-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|  
|`double`|<span data-ttu-id="6631f-110">[Todouble – (Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6631f-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|  
|`short`|<span data-ttu-id="6631f-111">[Toint16 – (Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6631f-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|  
|`int`|<span data-ttu-id="6631f-112">[ToInt32 – (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6631f-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|  
|`long`|<span data-ttu-id="6631f-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6631f-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|  
|`float`|<span data-ttu-id="6631f-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6631f-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|  
|`ushort`|<span data-ttu-id="6631f-115">[Touint16 – (Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6631f-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|  
|`uint`|<span data-ttu-id="6631f-116">[Touint32 – (Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6631f-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|  
|`ulong`|<span data-ttu-id="6631f-117">[Touint64 – (Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6631f-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6631f-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="6631f-118">Example</span></span>  
 <span data-ttu-id="6631f-119">Tento příklad inicializuje pole bajtů, vrátí pole, pokud architektura počítače je ve formátu little endian (to znamená, že nejméně významný bajt je uložen) a pak zavolá [ToInt32 – (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))způsobů, jak převést čtyři bajty v poli, aby `int`.</span><span class="sxs-lookup"><span data-stu-id="6631f-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="6631f-120">Druhý argument [ToInt32 – (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) Určuje počáteční index pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="6631f-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6631f-121">Výstup se může lišit v závislosti na endianess architektuy počítače.</span><span class="sxs-lookup"><span data-stu-id="6631f-121">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="6631f-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="6631f-122">Example</span></span>  
 <span data-ttu-id="6631f-123">V tomto příkladu <xref:System.BitConverter.GetBytes%28System.Int32%29> metodu <xref:System.BitConverter> třídy je volána pro převod `int` na pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="6631f-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6631f-124">Výstup se může lišit v závislosti na endianess architektuy počítače.</span><span class="sxs-lookup"><span data-stu-id="6631f-124">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6631f-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6631f-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="6631f-126">Typy</span><span class="sxs-lookup"><span data-stu-id="6631f-126">Types</span></span>](../../../csharp/programming-guide/types/index.md)
