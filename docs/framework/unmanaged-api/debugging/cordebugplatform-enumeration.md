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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d3b8f1e869e90fd3388cc0844e608b7ff40fc89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugplatform-enumeration"></a>Výčet CorDebugPlatform
Poskytuje cílové platformy hodnoty, které jsou používány [icordebugdatatarget::getplatform –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|CORDB_PLATFORM_WINDOWS_X86|Cílové platformy je spuštěna na Intel x86 hardwaru systému Windows.|  
|CORDB_PLATFORM_WINDOWS_AMD64|Cílové platformy je 64bitová verze Windows spuštěná v AMD64 nebo podporou technologie Intel EM64T hardwaru.|  
|CORDB_PLATFORM_WINDOWS_IA64|Cílové platformy je 32bitový systém Windows systémem hardwaru Intel IA-64.|  
|CORDB_PLATFORM_MAC_PPC|Cílové platformy je operační systém Macintosh systémem PowerPC hardwaru.|  
|CORDB_PLATFORM_MAC_X86|Cílové platformy je operační systém Macintosh systémem Intel x86 hardwaru.|  
|CORDB_PLATFORM_WINDOWS_ARM|Cílové platformy je operační systém Macintosh systémem Windows ARM hardwaru.|  
|CORDB_PLATFORM_MAC_AMD64|Cílové platformy je operační systém Macintosh systémem AMD64 hardwaru.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
 `CORDB_PLATFORM_WINDOWS_ARM` a `CORDB_PLATFORM_MAC_AMD64` členové jsou k dispozici v rozhraní .NET Framework 4.5.2 a novějších verzích.  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
