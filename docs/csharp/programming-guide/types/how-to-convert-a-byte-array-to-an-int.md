---
title: 'Postupy: Převod bajtového pole na int – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 6d272a1a20cc5eb35edc7f6d971cbffbd9bfdbae
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588410"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Postupy: Převod bajtového pole na int (C# Průvodce programováním)
Tento příklad ukazuje, jak použít <xref:System.BitConverter> třídu k převedení pole bajtů na typ [int](../../language-reference/builtin-types/integral-numeric-types.md) a zpět na pole bajtů. Po čtení bajtů z sítě může být nutné převést bajty z bajtů na vestavěný datový typ. Kromě metody [ToInt32 – (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) v příkladu v následující tabulce jsou uvedeny metody <xref:System.BitConverter> třídy, které převádějí bajty (z pole bajtů) na jiné předdefinované typy.  
  
|Vrácený typ|Metoda|  
|-------------------|------------|  
|`bool`|[ToBoolean (Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|  
|`char`|[ToChar – (Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|  
|`double`|[ToDouble – (Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|  
|`short`|[ToInt16 – (Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|  
|`int`|[ToInt32 – (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|  
|`long`|[ToInt64 – (Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|  
|`float`|[ToSingle – (Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|  
|`ushort`|[ToUInt16 – (Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|  
|`uint`|[ToUInt32 – (Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|  
|`ulong`|[ToUInt64 – (Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|  
  
## <a name="example"></a>Příklad  
 Tento příklad inicializuje pole bajtů, pokud je architektura počítače ve formátu Little endian (to znamená, že je nejdříve uložený nejméně významný bajt) a pak zavolá metodu [ToInt32 – (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) pro převod čtyři bajty v poli do `int`. Druhý argument pro [ToInt32 – (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) Určuje počáteční index pole bajtů.  
  
> [!NOTE]
>  Výstup se může lišit v závislosti na endianess architektury počítače.  
  
 [!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.BitConverter.GetBytes%28System.Int32%29> jevolána<xref:System.BitConverter> Metoda třídy pro převod napolebajtů.`int`  
  
> [!NOTE]
>  Výstup se může lišit v závislosti na endianess architektury počítače.  
  
 [!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [Typy](./index.md)
