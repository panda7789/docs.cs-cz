---
title: CorPinvokeMap – výčet
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: 199a649b0481c2a740926636345eefbda6831ef2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007543"
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap – výčet
Určuje možnosti pro volání PInvoke.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`pmNoMangle`|Použijte název každého člena podle zadání.|  
|`pmCharSetMask`|Vyhrazeno.|  
|`pmCharSetNotSpec`|Vyhrazeno.|  
|`pmCharSetAnsi`|Zařazování řetězců jako řetězce znaků s více bajty.|  
|`pmCharSetUnicode`|Zařazování řetězců jako znaků Unicode 2 bajtů.|  
|`pmCharSetAuto`|Pro cílový operační systém jsou automaticky zařazeny řetězce odpovídajícím způsobem. Výchozí hodnota je Unicode v systémech Windows NT, Windows 2000, Windows XP a Windows Server 2003. Výchozí hodnota je ANSI v systému Windows 98 a Windows Millennium.|  
|`pmBestFitUseAssem`|Vyhrazeno.|  
|`pmBestFitEnabled`|Proveďte nejvhodnější mapování znaků Unicode, u kterých chybí přesná shoda v sadě znaků ANSI.|  
|`pmBestFitDisabled`|Neprovádějte nejlepší mapování znaků Unicode. V takovém případě budou všechny nemapovatelný znaky nahrazeny znakem "?".|  
|`pmBestFitMask`|Vyhrazeno.|  
|`pmThrowOnUnmappableCharUseAssem`|Vyhrazeno.|  
|`pmThrowOnUnmappableCharEnabled`|Vyvolat výjimku, když zařazovací modul Interop nalezne nemapovatelný znak.|  
|`pmThrowOnUnmappableCharDisabled`|Nevyvolejte výjimku, když zařazovací modul Interop nalezne nemapovatelný znak.|  
|`pmThrowOnUnmappableCharMask`|Vyhrazeno|  
|`pmSupportsLastError`|Umožňuje volanému volat `SetLastError` funkci Win32 před vrácením z metody s atributy.|  
|`pmCallConvMask`|Vyhrazeno|  
|`pmCallConvWinapi`|Použijte výchozí konvenci volání platformy. Například ve Windows je výchozí nastavení `StdCall` a v systém Windows CE .NET je `Cdecl` .|  
|`pmCallConvCdecl`|Použijte `Cdecl` konvenci volání. V tomto případě volající vyčistí zásobník. To umožňuje volání funkcí s `varargs` (to znamená, funkce, které přijímají proměnný počet parametrů).|  
|`pmCallConvStdcall`|Použijte `StdCall` konvenci volání. V tomto případě volaný vyčistí zásobník. Toto je výchozí konvence pro volání nespravovaných funkcí s voláním platformy.|  
|`pmCallConvThiscall`|Použijte `ThisCall` konvenci volání. V tomto případě je prvním parametrem `this` ukazatel a je uložen v registru ecx. Další parametry jsou vloženy do zásobníku. `ThisCall`Konvence volání se používá pro volání metod u tříd exportovaných z nespravované knihovny DLL.|  
|`pmCallConvFastcall`|Vyhrazeno.|  
|`pmMaxValue`|Vyhrazeno.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
