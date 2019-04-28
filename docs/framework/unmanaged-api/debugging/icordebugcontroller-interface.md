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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7628aa0ad10398f92d475c4c776810e13fac22b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749498"
---
# <a name="icordebugcontroller-interface"></a>ICorDebugController – rozhraní

Představuje rozsah buď <xref:System.Diagnostics.Process> nebo <xref:System.AppDomain>, ve které provádění kódu lze ovládat kontext.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Tato metoda je zastaralá.|  
|`ICorDebugController::CommitChanges`|Tato metoda je zastaralá.|  
|[Continue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|Pokračuje v provádění spravovaná vlákna po volání [icordebugcontroller::stop –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).|  
|[Detach – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|Odpojí ladicí program z domény, procesu nebo aplikace.|  
|[EnumerateThreads – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|Získá enumerátor pro aktivní spravovaná vlákna v procesu.|  
|[HasQueuedCallbacks – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|Získá hodnotu určující, zda všechny spravované zpětná volání jsou právě ve frontě pro zadaný podproces.|  
|[IsRunning – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|Získá hodnotu, která označuje, zda vlákna v procesu jsou aktuálně spuštěna bez omezení.|  
|[SetAllThreadsDebugState – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|Nastaví stav ladění všechna spravovaná vlákna v procesu.|  
|[Stop – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|Provádí kooperativní stop na všech vláknech, na kterých běží spravovaný kód v procesu.|  
|[Terminate – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|Ukončí proces s uvedený ukončovací kód.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `ICorDebugController` je proces řízení, oborem, který zahrnuje všechna vlákna procesu. Pokud `ICorDebugController` je řízení doménu aplikace, oborem, který zahrnuje pouze vlákna této konkrétní aplikační domény.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
