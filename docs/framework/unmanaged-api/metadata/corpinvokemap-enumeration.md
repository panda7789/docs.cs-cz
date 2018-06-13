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
ms.openlocfilehash: edb45c9ceefb242e5a72e8602dc93ecd39b2df09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447951"
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
|`pmNoMangle`|Každý název členu použijte jako zadaný.|  
|`pmCharSetMask`|Vyhrazena.|  
|`pmCharSetNotSpec`|Vyhrazena.|  
|`pmCharSetAnsi`|Zařazování řetězců jako více bajtové znakové řetězce.|  
|`pmCharSetUnicode`|Zařazování řetězců jako 2bajtová znaky znakové sady Unicode.|  
|`pmCharSetAuto`|Automaticky zařazování řetězců pro cílový operační systém. Výchozí hodnota je kódování Unicode v systému Windows NT, Windows 2000, Windows XP a řady Windows Server 2003; Výchozí hodnota je ANSI na Windows 98 a Windows Me.|  
|`pmBestFitUseAssem`|Vyhrazena.|  
|`pmBestFitEnabled`|Proveďte přizpůsobená mapování znaky Unicode, která nemají přesnou shodu v znakovou sadu ANSI.|  
|`pmBestFitDisabled`|Neprovádějte přizpůsobený mapování znaky Unicode. V takovém případě budou nahrazeny všechny unmappable znaky '?'.|  
|`pmBestFitMask`|Vyhrazena.|  
|`pmThrowOnUnmappableCharUseAssem`|Vyhrazena.|  
|`pmThrowOnUnmappableCharEnabled`|Způsobí výjimku, když dojde spolupráce vláken unmappable znak.|  
|`pmThrowOnUnmappableCharDisabled`|Když spolupráce vláken dojde unmappable znak není vyvolána výjimka.|  
|`pmThrowOnUnmappableCharMask`|Vyhrazené|  
|`pmSupportsLastError`|Povolit volaného volání Win32 `SetLastError` funkce před návratem od metodu s atributy.|  
|`pmCallConvMask`|Vyhrazené|  
|`pmCallConvWinapi`|Použijte výchozí platformu konvence volání. Například v systému Windows, výchozí hodnota je `StdCall` a na Windows CE .NET je `Cdecl`.|  
|`pmCallConvCdecl`|Použití `Cdecl` konvence volání. V takovém případě volající vyčistí zásobníku. To umožňuje volání funkcí s `varargs` (to znamená, funkce, které přijímají proměnný počet parametrů).|  
|`pmCallConvStdcall`|Použití `StdCall` konvence volání. V takovém případě volaného vyčistí zásobníku. Toto je výchozí konvenci pro vyvolání volání nespravovaných funkcí s platformou.|  
|`pmCallConvThiscall`|Použití `ThisCall` konvence volání. V takovém případě je první parametr `this` ukazatel a je uložen v registru ECX. Další parametry jsou nabídnutých v zásobníku. `ThisCall` Konvence volání se používá k volání metody na třídách exportovány z nespravovaných knihovny DLL.|  
|`pmCallConvFastcall`|Vyhrazena.|  
|`pmMaxValue`|Vyhrazena.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
