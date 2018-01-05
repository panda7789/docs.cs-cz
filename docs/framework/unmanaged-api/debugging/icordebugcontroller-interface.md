---
title: ICorDebugController Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController
helpviewer_keywords: ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bde0ef86ff6304c696ad8c68fc81c0a339ed6e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontroller-interface1"></a>ICorDebugController Interface1
Představuje obor, buď <xref:System.Diagnostics.Process> nebo <xref:System.AppDomain>, ve které provádění kódu se dá řídit kontextu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Tato metoda je zastaralá.|  
|`ICorDebugController::CommitChanges`|Tato metoda je zastaralá.|  
|[Continue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|Pokračuje v provádění spravovaných vláknech po volání [icordebugcontroller::stop –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).|  
|[Detach – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|Umožňuje odpojit ladicí program z domény procesů nebo aplikace.|  
|[EnumerateThreads – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|Získá enumerátor pro aktivní spravovaných vláken v procesu.|  
|[HasQueuedCallbacks – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|Získá hodnotu, která určuje, zda všechny spravované zpětná volání jsou aktuálně ve frontě pro zadaný vlákno.|  
|[IsRunning – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|Získá hodnotu, která určuje, zda vláken v procesu jsou aktuálně spuštěny volně.|  
|[SetAllThreadsDebugState – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|Nastaví ladění stav všech spravovaných vláken v procesu.|  
|[Stop – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|Provede spolupráci zastavení všech vláken, které jsou spuštěny spravovaného kódu v procesu.|  
|[Terminate – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|Ukončí proces uvedený ukončovací kód.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `ICorDebugController` je proces řízení, oboru zahrnuje všechny podprocesy procesu. Pokud `ICorDebugController` je řízení doménu aplikace, rozsah obsahuje pouze vláken této domény konkrétní aplikace.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
