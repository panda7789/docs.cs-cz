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
ms.openlocfilehash: 8216dc3030b18428ab52fbf8385d392f81057aa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176146"
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
  
|Člen|Popis|  
|------------|-----------------|  
|`pmNoMangle`|Použijte každý název člena, jak je zadáno.|  
|`pmCharSetMask`|Vyhrazeno.|  
|`pmCharSetNotSpec`|Vyhrazeno.|  
|`pmCharSetAnsi`|Řetězce marshaljako vícebajtové řetězce znaků.|  
|`pmCharSetUnicode`|Řetězce marshal jako dvoubajtové znaky Unicode.|  
|`pmCharSetAuto`|Automaticky zařazují řetězce vhodně pro cílový operační systém. Výchozí hodnota je Unicode v systémech Windows NT, Windows 2000, Windows XP a Windows Server 2003; Výchozí hodnota je ANSI v systémech Windows 98 a Windows ME.|  
|`pmBestFitUseAssem`|Vyhrazeno.|  
|`pmBestFitEnabled`|Proveďte nejvhodnější mapování znaků Unicode, které v znakové sadě ANSI nemají přesnou shodu.|  
|`pmBestFitDisabled`|Neprovádějte nejvhodnější mapování znaků Unicode. V tomto případě budou všechny nezamísťující znaky nahrazeny znakem '?'.|  
|`pmBestFitMask`|Vyhrazeno.|  
|`pmThrowOnUnmappableCharUseAssem`|Vyhrazeno.|  
|`pmThrowOnUnmappableCharEnabled`|Vyvolání výjimky, když interop zařazovač narazí na nemappable znak.|  
|`pmThrowOnUnmappableCharDisabled`|Nevyvolávejte výjimku, když interop zařazovač narazí na nemappable znak.|  
|`pmThrowOnUnmappableCharMask`|Vyhrazeno|  
|`pmSupportsLastError`|Povolte volavce volat funkci `SetLastError` Win32 před návratem z přiřazené metody.|  
|`pmCallConvMask`|Vyhrazeno|  
|`pmCallConvWinapi`|Použijte výchozí konvence volání platformy. Například v systému `StdCall` Windows výchozí je a `Cdecl`na Windows CE .NET je .|  
|`pmCallConvCdecl`|Použijte `Cdecl` konvence volání. V tomto případě volající čistí zásobníku. To umožňuje volání `varargs` funkcí s (to znamená, že funkce, které přijímají proměnný počet parametrů).|  
|`pmCallConvStdcall`|Použijte `StdCall` konvence volání. V tomto případě volaný čistí zásobníku. Toto je výchozí konvence pro volání nespravovaných funkcí s vyvolání platformy.|  
|`pmCallConvThiscall`|Použijte `ThisCall` konvence volání. V tomto případě je prvním `this` parametrem ukazatel a je uložen v registru ECX. Ostatní parametry jsou tlačeny do zásobníku. Konvence `ThisCall` volání se používá k volání metod na třídy exportované z nespravované dll.|  
|`pmCallConvFastcall`|Vyhrazeno.|  
|`pmMaxValue`|Vyhrazeno.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
