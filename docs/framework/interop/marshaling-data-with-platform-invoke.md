---
title: "Zařazování dat s voláním platformy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 24ae6da0b32cf15ee9104bd10ba5fe6bb03a9763
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-data-with-platform-invoke"></a>Zařazování dat s voláním platformy
Volání funkce exportované z nespravovaných knihovny, vyžaduje rozhraní .NET Framework aplikace funkce prototypů ve spravovaném kódu, který představuje nespravované funkce. Chcete-li vytvořit prototyp, která umožňuje platformy vyvolání zařazování dat správně, musíte provést následující:  
  
-   Použít <xref:System.Runtime.InteropServices.DllImportAttribute> atribut statickou funkci nebo metodu ve spravovaném kódu.  
  
-   Nahraďte spravované datové typy pro nespravované datové typy.  
  
 Podle dokumentace dodané s nespravované funkce můžete vytvořit ekvivalentní spravované prototypu použitím atribut s jeho nepovinná pole a nahraďte spravované datové typy pro nespravované typy. Pokyny, jak se má použít **DllImportAttribute**, najdete v části [využívání nespravovaných funkcí DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).  
  
 Tato část obsahuje vzorků, které ukazují, jak vytvořit prototypy spravovaných funkcí pro předání argumentů k a příjem návratové hodnoty z funkce exportované sadou nespravované knihovny. Ukázky také ukazují, kdy použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut a <xref:System.Runtime.InteropServices.Marshal> třídy explicitně zařazování data.  
  
## <a name="platform-invoke-data-types"></a>Datové typy vyvolání platformy  
 Následující tabulka uvádí typy dat používaných v rozhraní API Win32 (uvedené v Wtypes.h) a funkce jazyka C. Mnoho nespravované knihovny obsahují funkce, které předejte tyto datové typy jako parametry a návratové hodnoty. Třetí sloupec uvádí odpovídající typ rozhraní .NET Framework předdefinované hodnoty nebo třídu, která použijete ve spravovaném kódu. V některých případech můžete nahradit typem stejnou velikost pro typ uvedené v tabulce.  
  
|Nespravovaný typ v Wtypes.h|Nespravovaný typ jazyka C|Název spravované třídy|Popis|  
|--------------------------------|-------------------------------|------------------------|-----------------|  
|**POPISOVAČ**|**void\***|<xref:System.IntPtr?displayProperty=nameWithType>|32bitová verze na 32bitové operační systémy Windows, 64 bitů v operačních systémech Windows 64-bit.|  
|**BAJTŮ**|**unsigned char**|<xref:System.Byte?displayProperty=nameWithType>|8 bitů|  
|**KRÁTKÝ**|**short**|<xref:System.Int16?displayProperty=nameWithType>|16 bitů|  
|**WORD**|**short bez znaménka**|<xref:System.UInt16?displayProperty=nameWithType>|16 bitů|  
|**CELÁ ČÍSLA**|**int**|<xref:System.Int32?displayProperty=nameWithType>|32bitová verze|  
|**UINT**|**int bez znaménka**|<xref:System.UInt32?displayProperty=nameWithType>|32bitová verze|  
|**DLOUHÁ**|**long**|<xref:System.Int32?displayProperty=nameWithType>|32bitová verze|  
|**BOOL**|**long**|<xref:System.Byte>|32bitová verze|  
|**DWORD**|**dlouho bez znaménka**|<xref:System.UInt32?displayProperty=nameWithType>|32bitová verze|  
|**ULONG –**|**dlouho bez znaménka**|<xref:System.UInt32?displayProperty=nameWithType>|32bitová verze|  
|**CHAR –**|**char**|<xref:System.Char?displayProperty=nameWithType>|Uspořádání s ANSI.|  
|**WCHAR**|**wchar_t**|<xref:System.Char?displayProperty=nameWithType>|Uspořádání pomocí kódování Unicode.|  
|**LPSTR**|**Char\***|<xref:System.String?displayProperty=nameWithType>nebo<xref:System.Text.StringBuilder?displayProperty=nameWithType>|Uspořádání s ANSI.|  
|**LPCSTR**|**Const char\***|<xref:System.String?displayProperty=nameWithType>nebo<xref:System.Text.StringBuilder?displayProperty=nameWithType>|Uspořádání s ANSI.|  
|**LPWSTR**|**wchar_t\***|<xref:System.String?displayProperty=nameWithType>nebo<xref:System.Text.StringBuilder?displayProperty=nameWithType>|Uspořádání pomocí kódování Unicode.|  
|**LPCWSTR**|**Const wchar_t\***|<xref:System.String?displayProperty=nameWithType>nebo<xref:System.Text.StringBuilder?displayProperty=nameWithType>|Uspořádání pomocí kódování Unicode.|  
|**PLOVOUCÍ DESETINNÁ ČÁRKA**|**Plovoucí desetinná čárka**|<xref:System.Single?displayProperty=nameWithType>|32bitová verze|  
|**DOUBLE**|**Double**|<xref:System.Double?displayProperty=nameWithType>|64bitová verze|  
  
 Pro odpovídající typy v [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# a C++, najdete [Úvod do knihovně tříd rozhraní .NET Framework](../../../docs/standard/class-library-overview.md).  
  
## <a name="pinvokelibdll"></a>PinvokeLib.dll  
 Následující kód definuje funkce knihovny poskytované Pinvoke.dll. Mnoha ukázek popsané v této části volání této knihovny.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]  
  
 [!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
