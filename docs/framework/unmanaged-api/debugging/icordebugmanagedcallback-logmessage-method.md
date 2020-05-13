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
ms.openlocfilehash: c60af0ccfb143e68be3b987b0caf92fe3d992b4d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212705"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a>ICorDebugManagedCallback::LogMessage – metoda
Oznamuje ladicímu programu, že spravované vlákno modulu CLR (Common Language Runtime) zavolalo do <xref:System.Diagnostics.EventLog> protokolu události metodu ve třídě.  
  
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
 pro Hodnota výčtu [LoggingLevelEnum –](logginglevelenum-enumeration.md) , která určuje úroveň závažnosti popisné zprávy, která byla zapsána do protokolu událostí.  
  
 `pLogSwitchName`  
 pro Ukazatel na název sledovacího přepínače.  
  
 `pMessage`  
 pro Ukazatel na zprávu, která byla zapsána do protokolu událostí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
