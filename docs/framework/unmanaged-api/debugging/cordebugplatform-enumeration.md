---
title: Výčet CorDebugPlatform
ms.date: 03/30/2017
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
ms.openlocfilehash: 5d66503487e1b997e2b8cc7d3d46e210a4dbbe05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132754"
---
# <a name="cordebugplatform-enumeration"></a>Výčet CorDebugPlatform
Poskytuje hodnoty cílové platformy, které jsou používány metodou [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|CORDB_PLATFORM_WINDOWS_X86|Cílová platforma je systémem Windows spuštěná na hardwaru Intel x86.|  
|CORDB_PLATFORM_WINDOWS_AMD64|Cílová platforma je 64 bitových oken běžících na hardwaru AMD64 nebo Intel EM64T.|  
|CORDB_PLATFORM_WINDOWS_IA64|Cílová platforma je 32 bitových oken běžících na hardwaru Intel IA-64.|  
|CORDB_PLATFORM_MAC_PPC|Cílová platforma je operační systém Macintosh běžící na hardwaru PowerPC.|  
|CORDB_PLATFORM_MAC_X86|Cílová platforma je operační systém Macintosh běžící na hardwaru Intel x86.|  
|CORDB_PLATFORM_WINDOWS_ARM|Cílová platforma je operační systém Macintosh běžící na hardwaru Windows ARM.|  
|CORDB_PLATFORM_MAC_AMD64|Cílová platforma je operační systém Macintosh běžící na hardwaru AMD64.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
 Členové `CORDB_PLATFORM_WINDOWS_ARM` a `CORDB_PLATFORM_MAC_AMD64` jsou k dispozici v .NET Framework 4.5.2 a novějších verzích.  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
