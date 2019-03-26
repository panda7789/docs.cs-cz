---
title: Zařazování dat s voláním platformy
ms.date: 03/20/2019
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cb310dc6d786c3c7711f4c194c6623324c777dd
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412393"
---
# <a name="marshaling-data-with-platform-invoke"></a>Zařazování dat s voláním platformy

Volání funkcí exportovaných z nespravovaná knihovna, vyžaduje aplikaci rozhraní .NET Framework prototypu funkce ve spravovaném kódu, který představuje nespravované funkci. K vytvoření prototypu, který umožňuje platformu vyvolání zařazování dat správně, musíte provést následující:

- Použít <xref:System.Runtime.InteropServices.DllImportAttribute> atribut statické funkce nebo metody ve spravovaném kódu.

- Nahraďte spravované datové typy pro nespravované datové typy.

Podle dokumentace dodané s nespravovanou funkci můžete použít k vytvoření odpovídající spravovaný prototyp použitím atribut s jeho volitelná pole a nahrazování spravované datové typy pro nespravované typy. Pokyny o tom, jak aplikovat <xref:System.Runtime.InteropServices.DllImportAttribute>, naleznete v tématu [používání nespravovaných funkcí DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).

Tato část obsahuje ukázky, které ukazují, jak vytvářet prototypy spravované funkce pro předávání argumentů do a z funkcí exportovaných knihovnou nespravovaných knihoven příjem návratové hodnoty. Ukázky také ukazují, kdy se má použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut a <xref:System.Runtime.InteropServices.Marshal> třídy explicitně zařazování dat.

## <a name="platform-invoke-data-types"></a>Datové typy vyvolání platformy

V následující tabulce jsou uvedeny datové typy používané v rozhraní Windows API a funkce C-style. Mnoho nespravovaných knihoven obsahují funkce, které jako parametry předat těchto datových typů a návratových hodnot. Třetí sloupec uvádí odpovídající rozhraní .NET Framework předdefinovaného hodnotového typu nebo třídy, která používáte ve spravovaném kódu. V některých případech můžete nahradit typ stejné velikosti typu uvedené v tabulce.

|Nespravovaný typ v rozhraní Windows API|Nespravovaný typ jazyka C|Spravovaného typu|Popis|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|Použít pro funkci, která nevrací hodnotu.|
|`HANDLE`|`void *`|<xref:System.IntPtr?displayProperty=nameWithType> Nebo <xref:System.UIntPtr?displayProperty=nameWithType>|32 bitů na 32bitové operační systémy Windows, 64 bitů v operačních systémech Windows 64-bit.|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|8 bitů|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|16 bitů|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|16 bitů|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|32 bitů|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|32 bitů|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|32 bitů|
|`BOOL`|`long`|<xref:System.Boolean?displayProperty=nameWithType> Nebo <xref:System.Int32?displayProperty=nameWithType>|32 bitů|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 bitů|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 bitů|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|Uspořádání s ANSI.|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|Vyplnění pomocí kódování Unicode.|
|`LPSTR`|`char *`|<xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Uspořádání s ANSI.|
|`LPCSTR`|`const char *`|<xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Uspořádání s ANSI.|
|`LPWSTR`|`wchar_t *`|<xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Vyplnění pomocí kódování Unicode.|
|`LPCWSTR`|`const wchar_t *`|<xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Vyplnění pomocí kódování Unicode.|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|32 bitů|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|64 bitů|

Pro odpovídající typy v jazyce Visual Basic C#a C++, naleznete v tématu [Úvod do knihovny tříd rozhraní .NET Framework](../../standard/class-library-overview.md#system-namespace).

## <a name="pinvokelibdll"></a>PinvokeLib.dll

Následující kód definuje funkce knihovny poskytované Pinvoke.dll. Mnoho vzorků popsané v této části volání této knihovny.

### <a name="example"></a>Příklad

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
