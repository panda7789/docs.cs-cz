---
title: ICorDebugController – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
ms.openlocfilehash: 27f991c12ea7786d6146b5731848ca5ad3a37e21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125373"
---
# <a name="icordebugcontroller-interface"></a>ICorDebugController – rozhraní

Představuje obor, buď <xref:System.Diagnostics.Process>, nebo <xref:System.AppDomain>, ve kterém lze ovládat kontext provádění kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Tato metoda je zastaralá.|  
|`ICorDebugController::CommitChanges`|Tato metoda je zastaralá.|  
|[Continue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|Obnoví provádění spravovaných vláken po volání metody [ICorDebugController:: stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).|  
|[Detach – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|Odpojí ladicí program od domény procesu nebo aplikace.|  
|[EnumerateThreads – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|Získá enumerátor pro aktivní spravovaná vlákna v procesu.|  
|[HasQueuedCallbacks – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|Získá hodnotu, která označuje, zda jsou pro zadané vlákno aktuálně zařazena všechna spravovaná zpětná volání.|  
|[IsRunning – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|Získá hodnotu, která označuje, zda jsou vlákna v procesu aktuálně spuštěna volně.|  
|[SetAllThreadsDebugState – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|Nastaví stav ladění pro všechna spravovaná vlákna v procesu.|  
|[Stop – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|Provede kooperativní zastavení na všech vláknech, na kterých běží spravovaný kód v procesu.|  
|[Terminate – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|Ukončí proces se zadaným ukončovacím kódem.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `ICorDebugController` řídí proces, zahrnuje obor všechny podprocesy procesu. Pokud `ICorDebugController` řídí doménu aplikace, obor obsahuje pouze vlákna této konkrétní aplikační domény.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
