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
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Postupy: Převedení pole bajtů na typ int (Průvodce programováním v C#)
Tento příklad ukazuje, jak používat <xref:System.BitConverter> třída pro převod pole bajtů, které mají [int](../../../csharp/language-reference/keywords/int.md) a zpět na pole bajtů. Možná budete muset převést z bajtů na typ předdefinované po přečtení bajtů mimo síť, například. Kromě [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) metoda příklad následující tabulka uvádí metody v <xref:System.BitConverter> třídu, která převést bajtů (z pole bajtů) na jiné předdefinované typy.  
  
|Typ vrácený|Metoda|  
|-------------------|------------|  
|`bool`|[ToBoolean (Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|  
|`char`|[ToChar (Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|  
|`double`|[ToDouble (Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|  
|`short`|[ToInt16 (Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|  
|`int`|[ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|  
|`long`|[ToInt64 (Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|  
|`float`|[ToSingle (Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|  
|`ushort`|[ToUInt16 (Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|  
|`uint`|[ToUInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|  
|`ulong`|[ToUInt64 (Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|  
  
## <a name="example"></a>Příklad  
 Tento příklad inicializuje pole bajtů, pokud je architektura počítačových little endian obrátí pole (který je nejméně významný bajt je uložen) a potom zavolá [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))způsobů, jak převést čtyři bajtů v poli, aby `int`. Druhý argument [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) Určuje počáteční index pole bajtů.  
  
> [!NOTE]
>  Výstup se můžou lišit v závislosti na endianess architektury vašeho počítače.  
  
 [!code-csharp[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.BitConverter.GetBytes%28System.Int32%29> metodu <xref:System.BitConverter> třídy se nazývá převést `int` na pole bajtů.  
  
> [!NOTE]
>  Výstup se můžou lišit v závislosti na endianess architektury vašeho počítače.  
  
 [!code-csharp[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.BitConverter>  
 <xref:System.BitConverter.IsLittleEndian>  
 [Typy](../../../csharp/programming-guide/types/index.md)
