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
ms.openlocfilehash: e494bbb24e8f2245593e7945625e72e70ae1dde5
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892770"
---
# <a name="icordebugcontroller-interface"></a>ICorDebugController – rozhraní

Představuje obor, buď <xref:System.Diagnostics.Process> nebo <xref:System.AppDomain>, ve kterém lze ovládat kontext provádění kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Tato metoda je zastaralá.|  
|`ICorDebugController::CommitChanges`|Tato metoda je zastaralá.|  
|[Continue – metoda](icordebugcontroller-continue-method.md)|Obnoví provádění spravovaných vláken po volání metody [ICorDebugController:: stop](icordebugcontroller-stop-method.md).|  
|[Detach – metoda](icordebugcontroller-detach-method.md)|Odpojí ladicí program od domény procesu nebo aplikace.|  
|[EnumerateThreads – metoda](icordebugcontroller-enumeratethreads-method.md)|Získá enumerátor pro aktivní spravovaná vlákna v procesu.|  
|[HasQueuedCallbacks – metoda](icordebugcontroller-hasqueuedcallbacks-method.md)|Získá hodnotu, která označuje, zda jsou pro zadané vlákno aktuálně zařazena všechna spravovaná zpětná volání.|  
|[IsRunning – metoda](icordebugcontroller-isrunning-method.md)|Získá hodnotu, která označuje, zda jsou vlákna v procesu aktuálně spuštěna volně.|  
|[SetAllThreadsDebugState – metoda](icordebugcontroller-setallthreadsdebugstate-method.md)|Nastaví stav ladění pro všechna spravovaná vlákna v procesu.|  
|[Stop – metoda](icordebugcontroller-stop-method.md)|Provede kooperativní zastavení na všech vláknech, na kterých běží spravovaný kód v procesu.|  
|[Terminate – metoda](icordebugcontroller-terminate-method.md)|Ukončí proces se zadaným ukončovacím kódem.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `ICorDebugController` řízení procesu řídí, obor zahrnuje všechna vlákna procesu. Pokud `ICorDebugController` aplikace řídí doménu aplikace, zahrnuje obor pouze vlákna této konkrétní aplikační domény.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
