---
title: Zařazování dat s voláním platformy
ms.date: 07/31/2018
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae8fbb47986e5baaecb919ce79ae384a8427737a
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032228"
---
# <a name="marshaling-data-with-platform-invoke"></a>Zařazování dat s voláním platformy
Volání funkcí exportovaných z nespravovaná knihovna, vyžaduje aplikaci rozhraní .NET Framework prototypu funkce ve spravovaném kódu, který představuje nespravované funkci. K vytvoření prototypu, který umožňuje platformu vyvolání zařazování dat správně, musíte provést následující:  
  
-   Použít <xref:System.Runtime.InteropServices.DllImportAttribute> atribut statické funkce nebo metody ve spravovaném kódu.  
  
-   Nahraďte spravované datové typy pro nespravované datové typy.  
  
 Podle dokumentace dodané s nespravovanou funkci můžete použít k vytvoření odpovídající spravovaný prototyp použitím atribut s jeho volitelná pole a nahrazování spravované datové typy pro nespravované typy. Pokyny o tom, jak aplikovat **DllImportAttribute**, naleznete v tématu [používání nespravovaných funkcí DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).  
  
 Tato část obsahuje ukázky, které ukazují, jak vytvářet prototypy spravované funkce pro předávání argumentů do a z funkcí exportovaných knihovnou nespravovaných knihoven příjem návratové hodnoty. Ukázky také ukazují, kdy se má použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut a <xref:System.Runtime.InteropServices.Marshal> třídy explicitně zařazování dat.  
  
## <a name="platform-invoke-data-types"></a>Datové typy vyvolání platformy  
 V následující tabulce jsou uvedeny datové typy používané v rozhraní API systému Win32 (uvedené v Wtypes.h) a funkce C-style. Mnoho nespravovaných knihoven obsahují funkce, které jako parametry předat těchto datových typů a návratových hodnot. Třetí sloupec uvádí odpovídající rozhraní .NET Framework předdefinovaného hodnotového typu nebo třídy, která používáte ve spravovaném kódu. V některých případech můžete nahradit typ stejné velikosti typu uvedené v tabulce.  
  
|Nespravovaný typ v Wtypes.h|Nespravovaný typ jazyka C|Název spravované třídy|Popis|  
|--------------------------------|-------------------------------|------------------------|-----------------|  
|**TYP VOID**|**void**|<xref:System.Void?displayProperty=nameWithType>|Použít pro funkci, která nevrací hodnotu.|
|**POPISOVAČ**|**Typ void \***|<xref:System.IntPtr?displayProperty=nameWithType>|32 bitů na 32bitové operační systémy Windows, 64 bitů v operačních systémech Windows 64-bit.|  
|**BAJTŮ**|**unsigned char**|<xref:System.Byte?displayProperty=nameWithType>|8 bitů|  
|**KRÁTKÉ**|**short**|<xref:System.Int16?displayProperty=nameWithType>|16 bitů|  
|**WORD**|**short bez znaménka**|<xref:System.UInt16?displayProperty=nameWithType>|16 bitů|  
|**INT**|**int**|<xref:System.Int32?displayProperty=nameWithType>|32 bitů|  
|**UINT**|**unsigned int**|<xref:System.UInt32?displayProperty=nameWithType>|32 bitů|  
|**LONG**|**long**|<xref:System.Int32?displayProperty=nameWithType>|32 bitů|  
|**BOOL**|**long**|<xref:System.Byte>|32 bitů|  
|**DWORD**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32 bitů|  
|**ULONG**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32 bitů|  
|**CHAR**|**char**|<xref:System.Char?displayProperty=nameWithType>|Uspořádání s ANSI.|  
|**WCHAR**|**wchar_t**|<xref:System.Char?displayProperty=nameWithType>|Vyplnění pomocí kódování Unicode.|  
|**LPSTR**|**Char &ast;**|<xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Uspořádání s ANSI.|  
|**LPCSTR**|**const char &ast;**|<xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Uspořádání s ANSI.|  
|**LPWSTR**|**wchar_t &ast;**|<xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Vyplnění pomocí kódování Unicode.|  
|**LPCWSTR**|**Const wchar_t &ast;**|<xref:System.String?displayProperty=nameWithType> Nebo <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Vyplnění pomocí kódování Unicode.|  
|**PLOVOUCÍ DESETINNOU ČÁRKOU**|**plovoucí desetinnou čárkou**|<xref:System.Single?displayProperty=nameWithType>|32 bitů|  
|**DOUBLE**|**Double**|<xref:System.Double?displayProperty=nameWithType>|64 bitů|  
  
 Pro odpovídající typy v [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# a C++, naleznete [Úvod do knihovny tříd rozhraní .NET Framework](../../../docs/standard/class-library-overview.md).  
  
## <a name="pinvokelibdll"></a>PinvokeLib.dll  
 Následující kód definuje funkce knihovny poskytované Pinvoke.dll. Mnoho vzorků popsané v této části volání této knihovny.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]  
  
 [!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
