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
ms.openlocfilehash: b8c4e9d835db044912d1cbed92a14dd05e7de658
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399936"
---
# <a name="marshaling-data-with-platform-invoke"></a>Zařazování dat s voláním platformy

Chcete-li volat funkce exportované z nespravované knihovny, aplikace .NET Framework vyžaduje prototyp funkce ve spravovaném kódu, který představuje nespravovanou funkci. Chcete-li vytvořit prototyp, který umožňuje vyvolání platformy pro správné zařazování dat, je nutné provést následující:

- Použijte <xref:System.Runtime.InteropServices.DllImportAttribute> atribut pro statickou funkci nebo metodu ve spravovaném kódu.

- Nahraďte spravované datové typy pro nespravované datové typy.

Dokumentaci dodanou s nespravovanou funkcí můžete použít k vytvoření ekvivalentního spravovaného prototypu použitím atributu s jeho nepovinnými poli a nahrazením spravovaných datových typů pro nespravované typy. Pokyny k použití <xref:System.Runtime.InteropServices.DllImportAttribute>naleznete v tématu [spotřebovávání nespravovaných funkcí DLL](consuming-unmanaged-dll-functions.md).

V této části jsou uvedeny ukázky, které ukazují, jak vytvořit prototypy spravované funkce pro předávání argumentů a přijímání návratových hodnot z funkcí exportovaných nespravovanými knihovnami. Ukázky také ukazují, kdy použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut a <xref:System.Runtime.InteropServices.Marshal> třídu k explicitnímu zařazování dat.

## <a name="platform-invoke-data-types"></a>Datové typy vyvolání platformy

V následující tabulce jsou uvedeny datové typy používané ve funkcích rozhraní API systému Windows a ve stylu jazyka C. Mnoho nespravovaných knihoven obsahuje funkce, které tyto datové typy předají jako parametry a návratové hodnoty. Třetí sloupec uvádí odpovídající .NET Framework typ hodnoty nebo třídu, která se používá ve spravovaném kódu. V některých případech můžete nahradit typ stejné velikosti pro typ uvedený v tabulce.

|Nespravovaný typ v rozhraních API systému Windows|Nespravovaný typ jazyka C|Spravovaný typ|Popis|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|Používá se pro funkci, která nevrací hodnotu.|
|`HANDLE`|`void *`|<xref:System.IntPtr?displayProperty=nameWithType> nebo <xref:System.UIntPtr?displayProperty=nameWithType>|32 bitů v systémech Windows 32, 64 bitů v systémech Windows 64 v 16bitovém operačním systému Windows.|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|8 bitů|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|16 bitů|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|16 bitů|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|32 bitů|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|32 bitů|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|32 bitů|
|`BOOL`|`long`|<xref:System.Boolean?displayProperty=nameWithType> nebo <xref:System.Int32?displayProperty=nameWithType>|32 bitů|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 bitů|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 bitů|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|Upravte pomocí ANSI.|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|Upravte pomocí kódování Unicode.|
|`LPSTR`|`char *`|<xref:System.String?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Upravte pomocí ANSI.|
|`LPCSTR`|`const char *`|<xref:System.String?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Upravte pomocí ANSI.|
|`LPWSTR`|`wchar_t *`|<xref:System.String?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Upravte pomocí kódování Unicode.|
|`LPCWSTR`|`const wchar_t *`|<xref:System.String?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Upravte pomocí kódování Unicode.|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|32 bitů|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|64 bitů|

Odpovídající typy v Visual Basic, C# a C++ naleznete v tématu [Úvod do knihovny tříd .NET Framework](../../standard/class-library-overview.md#system-namespace).

## <a name="pinvokelibdll"></a>PinvokeLib.dll

Následující kód definuje funkce knihovny, které poskytuje PInvoke. dll. Mnoho ukázek popsaných v této části volá tuto knihovnu.

### <a name="example"></a>Příklad

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
