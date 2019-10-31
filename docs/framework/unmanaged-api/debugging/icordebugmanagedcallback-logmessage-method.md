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
ms.openlocfilehash: d95662167dbc8fcda049fb6a7b3e6ff1dfb6e736
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130709"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a>ICorDebugManagedCallback::LogMessage – metoda
Oznamuje ladicímu programu, že spravované vlákno modulu CLR (Common Language Runtime) volalo metodu ve třídě <xref:System.Diagnostics.EventLog> k zaznamenání události.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující spravované vlákno, které událost zaznamenal.  
  
 `pThread`  
 pro Ukazatel na objekt ICorDebugThread, který představuje spravované vlákno.  
  
 `lLevel`  
 pro Hodnota výčtu [LoggingLevelEnum –](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) , která určuje úroveň závažnosti popisné zprávy, která byla zapsána do protokolu událostí.  
  
 `pLogSwitchName`  
 pro Ukazatel na název sledovacího přepínače.  
  
 `pMessage`  
 pro Ukazatel na zprávu, která byla zapsána do protokolu událostí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
