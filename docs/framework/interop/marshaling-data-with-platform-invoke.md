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

Chcete-li volat funkce exportované z nespravované knihovny, vyžaduje aplikace rozhraní .NET Framework prototyp funkce ve spravovaném kódu, který představuje nespravovanou funkci. Chcete-li vytvořit prototyp, který umožňuje platformu vyvolat správně zařazovat data, musíte provést následující kroky:

- Použijte <xref:System.Runtime.InteropServices.DllImportAttribute> atribut na statickou funkci nebo metodu ve spravovaném kódu.

- Nahraďte spravované datové typy nespravovaným datovým typům.

Dokumentaci dodanou s nespravovanou funkcí můžete použít k vytvoření ekvivalentního spravovaného prototypu použitím atributu s volitelnými poli a nahrazením spravovaných datových typů za nespravované typy. Pokyny k použití aplikace <xref:System.Runtime.InteropServices.DllImportAttribute>naleznete v [tématu Náročné nespravované funkce dll](consuming-unmanaged-dll-functions.md).

Tato část obsahuje ukázky, které ukazují, jak vytvořit prototypy spravovaných funkcí pro předávání argumentů a přijímání vrácených hodnot z funkcí exportovaných nespravovanými knihovnami. Ukázky také ukazují, <xref:System.Runtime.InteropServices.MarshalAsAttribute> kdy použít <xref:System.Runtime.InteropServices.Marshal> atribut a třídu explicitně zařazovat data.

## <a name="platform-invoke-data-types"></a>Platforma vyvolat datové typy

V následující tabulce jsou uvedeny datové typy používané v polích WINDOWS API a ve stylu Jazyka C. Mnoho nespravovaných knihoven obsahuje funkce, které předávají tyto datové typy jako parametry a vrátí hodnoty. Třetí sloupec uvádí odpovídající typ hodnoty nebo třídu rozhraní .NET Framework, kterou používáte ve spravovaném kódu. V některých případech můžete nahradit typ stejné velikosti pro typ uvedený v tabulce.

|Nespravovaný typ v systémových apich|Nespravovaný typ jazyka C|Spravovaný typ|Popis|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|Aplikovaný na funkci, která nevrací hodnotu.|
|`HANDLE`|`void *`|<xref:System.IntPtr?displayProperty=nameWithType> nebo <xref:System.UIntPtr?displayProperty=nameWithType>|32 bitů v 32bitových operačních systémech Windows, 64 bitů v 64bitových operačních systémech Windows.|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|8 bitů|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|16 bitů|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|16 bitů|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|32 bitů|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|32 bitů|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|32 bitů|
|`BOOL`|`long`|<xref:System.Boolean?displayProperty=nameWithType> nebo <xref:System.Int32?displayProperty=nameWithType>|32 bitů|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 bitů|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 bitů|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|Ozdobte ansi.|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|Ozdobte pomocí unicode.|
|`LPSTR`|`char *`|<xref:System.String?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Ozdobte ansi.|
|`LPCSTR`|`const char *`|<xref:System.String?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Ozdobte ansi.|
|`LPWSTR`|`wchar_t *`|<xref:System.String?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Ozdobte pomocí unicode.|
|`LPCWSTR`|`const wchar_t *`|<xref:System.String?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Ozdobte pomocí unicode.|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|32 bitů|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|64 bitů|

Odpovídající typy v jazyce Visual Basic, C# a C++ naleznete [v části Úvod do knihovny tříd rozhraní .NET Framework](../../standard/class-library-overview.md#system-namespace).

## <a name="pinvokelibdll"></a>PinvokeLib.dll

Následující kód definuje funkce knihovny poskytované souborem Pinvoke.dll. Mnoho ukázek popsaných v této části volá tuto knihovnu.

### <a name="example"></a>Příklad

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
