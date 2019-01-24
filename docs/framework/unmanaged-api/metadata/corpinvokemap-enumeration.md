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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23a4c1aa25f269121dc602bbeb6b864b589318be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745957"
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap – výčet
Určuje možnosti pro volání PInvoke.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
|Člen|Popis|  
|------------|-----------------|  
|`pmNoMangle`|Každý název člena použijte uvedené.|  
|`pmCharSetMask`|Vyhrazená.|  
|`pmCharSetNotSpec`|Vyhrazená.|  
|`pmCharSetAnsi`|Zařazování řetězců v kódu jako více bajtové znaky řetězce.|  
|`pmCharSetUnicode`|Zařazování řetězců v kódu jako 2bajtové znaky kódování Unicode.|  
|`pmCharSetAuto`|Automaticky zařazovat řetězce pro cílový operační systém. Výchozí hodnota je kódování Unicode v systému Windows NT, Windows 2000, Windows XP a řady Windows Server 2003; Výchozí hodnota je ANSI na Windows 98 a Windows Me.|  
|`pmBestFitUseAssem`|Vyhrazená.|  
|`pmBestFitEnabled`|Provedení přizpůsobený mapování znaků Unicode, které nemají přesnou shodu v znakovou sadu ANSI.|  
|`pmBestFitDisabled`|Neprovádějte nejlepšího mapování znaků Unicode. V takovém případě budou nahrazeny všechny nemapovatelný znaky "?".|  
|`pmBestFitMask`|Vyhrazená.|  
|`pmThrowOnUnmappableCharUseAssem`|Vyhrazená.|  
|`pmThrowOnUnmappableCharEnabled`|Vyvolání výjimky, když se interoperační zařazovač setká nemapovatelný znak.|  
|`pmThrowOnUnmappableCharDisabled`|Když se interoperační zařazovač setká nemapovatelný znak není vyvolat výjimku.|  
|`pmThrowOnUnmappableCharMask`|Vyhrazeno|  
|`pmSupportsLastError`|Povolit volaný volání Win32 `SetLastError` funkce před návratem z metody s atributy.|  
|`pmCallConvMask`|Vyhrazeno|  
|`pmCallConvWinapi`|Používejte výchozí platformu konvence volání. Například na Windows výchozí hodnota je `StdCall` a na Windows CE .NET je `Cdecl`.|  
|`pmCallConvCdecl`|Použití `Cdecl` konvence volání. V takovém případě volající vyčistí zásobník. To umožňuje volání funkcí s `varargs` (to znamená, funkce, které přijímají proměnný počet parametrů).|  
|`pmCallConvStdcall`|Použití `StdCall` konvence volání. V takovém případě volaný vyčistí zásobník. To je výchozí konvence pro vyvolání volání nespravovaných funkcí s platformou.|  
|`pmCallConvThiscall`|Použití `ThisCall` konvence volání. V takovém případě je první parametr `this` ukazatel a je uložen v registru ECX. Další parametry jsou vloženy do zásobníku. `ThisCall` Konvence volání se používá k volání metod třídy exportované z nespravovaná knihovna DLL.|  
|`pmCallConvFastcall`|Vyhrazená.|  
|`pmMaxValue`|Vyhrazená.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
