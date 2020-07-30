---
title: Postup převodu bajtového pole na int-C# Průvodce programováním
description: Přečtěte si, jak převést pole bajtů na int. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 24037a5e212326cf5e670214a6774eff52bd8faf
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381564"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Postup převodu pole bajtů na typ int (Průvodce programováním v C#)

Tento příklad ukazuje, jak použít <xref:System.BitConverter> třídu k převedení pole bajtů na typ [int](../../language-reference/builtin-types/integral-numeric-types.md) a zpět na pole bajtů. Po čtení bajtů z sítě může být nutné převést bajty z bajtů na vestavěný datový typ. Kromě metody [ToInt32 – (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) v příkladu v následující tabulce jsou uvedeny metody <xref:System.BitConverter> třídy, které převádějí bajty (z pole bajtů) na jiné předdefinované typy.

|Vrácený typ|Metoda|
|-------------------|------------|
|`bool`|[ToBoolean (Byte \[ \] , Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|
|`char`|[ToChar – (Byte \[ \] , Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|
|`double`|[ToDouble – (Byte \[ \] , Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|
|`short`|[Toint16 – (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|
|`int`|[Toint32 – (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|
|`long`|[Toint64 – (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|
|`float`|[ToSingle – (Byte \[ \] , Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|
|`ushort`|[Touint16 – (Byte \[ \] , Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|
|`uint`|[Touint32 – (Byte \[ \] , Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|
|`ulong`|[Touint64 – (Byte \[ \] , Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|

## <a name="example"></a>Příklad

Tento příklad inicializuje pole bajtů, obrátí pole, pokud je architektura počítače Little-endian (to znamená, že je nejdříve uložen nejméně významný bajt), a poté zavolá metodu [ToInt32 – (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) pro převod čtyř bajtů v poli na `int` . Druhý argument pro [ToInt32 – (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) Určuje počáteční index pole bajtů.

> [!NOTE]
> Výstup se může lišit v závislosti na endian vaší architektury počítače.

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a>Příklad

V tomto příkladu <xref:System.BitConverter.GetBytes%28System.Int32%29> <xref:System.BitConverter> je volána metoda třídy pro převod `int` na pole bajtů.

> [!NOTE]
> Výstup se může lišit v závislosti na endian vaší architektury počítače.

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a>Viz také:

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [Typy](./index.md)
