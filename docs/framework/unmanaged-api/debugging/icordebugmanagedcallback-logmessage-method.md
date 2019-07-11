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
ms.openlocfilehash: 14b10b94f66a6b5434befeac1cd9562cb8a0f27f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761553"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a>ICorDebugManagedCallback::LogMessage – metoda
Ladicí program upozorní, že společným pojítkem language runtime (CLR) spravované volal metodu <xref:System.Diagnostics.EventLog> třídy do protokolu událostí.  
  
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
 [in] Ukazatel na objekt, který představuje doménu aplikace obsahující spravovaná vlákna, která událost zaznamenala ICorDebugAppDomain.  
  
 `pThread`  
 [in] Ukazatel na objekt ICorDebugThread, která představuje spravované vlákno.  
  
 `lLevel`  
 [in] Hodnota [logginglevelenum –](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) výčet, který indikuje úroveň závažnosti popisné zprávy, která byla zapsána do protokolu událostí.  
  
 `pLogSwitchName`  
 [in] Ukazatel na název přepínače trasování.  
  
 `pMessage`  
 [in] Ukazatel na zprávu, která byla zapsána do protokolu událostí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
