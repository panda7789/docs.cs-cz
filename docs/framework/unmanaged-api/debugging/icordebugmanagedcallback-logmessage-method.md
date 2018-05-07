---
title: ICorDebugManagedCallback::LogMessage – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4c8494b1ffc80fc49acce01c5de0b3fd18c0f5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a>ICorDebugManagedCallback::LogMessage – metoda
Ladicí program upozorní, že běžné vlákna modulu runtime (CLR) spravované jazyk volal metodu <xref:System.Diagnostics.EventLog> třída do protokolu událostí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace obsahující spravovaných vláken, která událost zaznamenala.  
  
 `pThread`  
 [v] Ukazatel ICorDebugThread objektu, která představuje spravované vlákno.  
  
 `lLevel`  
 [v] Hodnota [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) výčtu, která určuje úroveň závažnosti popisné zprávy, která byla zapsána do protokolu událostí.  
  
 `pLogSwitchName`  
 [v] Ukazatel na název přepínače trasování.  
  
 `pMessage`  
 [v] Ukazatel na zprávu, která byla zapsána do protokolu událostí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
