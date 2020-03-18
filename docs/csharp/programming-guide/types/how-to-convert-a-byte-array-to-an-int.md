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
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Jak převést bajtové pole na int (C# Programovací průvodce)

Tento příklad ukazuje, jak <xref:System.BitConverter> použít třídu převést pole bajtů [na int](../../language-reference/builtin-types/integral-numeric-types.md) a zpět na pole bajtů. Pravděpodobně bude pravděpodobně muset převést z bajtů na vestavěný datový typ po čtení bajtů mimo síť, například. Kromě metody [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) v příkladu jsou v <xref:System.BitConverter> následující tabulce uvedeny metody ve třídě, které převádějí bajty (z pole bajtů) na jiné předdefinované typy.

|Typ vrácen|Metoda|
|-------------------|------------|
|`bool`|[ToBoolean(Bajt\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|
|`char`|[ToChar(Bajt\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|
|`double`|[ToDouble (Bajt\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|
|`short`|[ToInt16(Bajt\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|
|`int`|[ToInt32(Bajt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|
|`long`|[ToInt64(Bajt\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|
|`float`|[ToSingle(Bajt\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|
|`ushort`|[ToUInt16(Bajt\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|
|`uint`|[ToUInt32(Bajt\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|
|`ulong`|[ToUInt64(Bajt\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|

## <a name="example"></a>Příklad

Tento příklad inicializuje pole bajtů, obrátí pole, pokud je architektura počítače little-endian (to znamená, že je nejprve uložen nejméně významný bajt), a pak zavolá metodu [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) pro převod čtyř bajtů v poli na . `int` Druhý argument [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) určuje počáteční index pole bajtů.

> [!NOTE]
> Výstup se může lišit v závislosti na endianness architektury počítače.

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a>Příklad

V tomto příkladu <xref:System.BitConverter.GetBytes%28System.Int32%29> je <xref:System.BitConverter> metoda třídy `int` volána k převodu na pole bajtů.

> [!NOTE]
> Výstup se může lišit v závislosti na endianness architektury počítače.

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a>Viz také

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [Typy](./index.md)
