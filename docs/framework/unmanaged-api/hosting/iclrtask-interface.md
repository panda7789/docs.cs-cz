---
title: ICLRTask – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask
helpviewer_keywords:
- ICLRTask interface [.NET Framework hosting]
ms.assetid: b3a44df3-578a-4451-b55e-70c8e7695f5e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ba53e4af114773a347d15b7308dc4c3567154e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435703"
---
# <a name="iclrtask-interface"></a>ICLRTask – rozhraní
Poskytuje metody, které umožňují hostitel provádět požadavky na common language runtime (CLR), nebo k poskytování oznámení CLR o související úlohy.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Abort – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|Požadavky, modul CLR přerušit úlohu, aktuální `ICLRTask` instance představuje.|  
|[ExitTask – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|Upozorní CLR, které úlohy spojené s aktuálním `ICLRTask` instance ukončuje a pokusí se korektně vypnout úlohu.|  
|[GetMemStats – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|Získá statistické informace o použití paměťových prostředků úlohou reprezentována aktuální `ICLRTask` instance.|  
|[LocksHeld – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|Získá počet uzamčení aktuálně uchovávat v úloze.|  
|[NeedsPriorityScheduling – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|Získá hodnotu označující, zda hostitel vysokou prioritu má přiřadit změnou plánu úlohy reprezentována aktuální `ICLRTask` instance.|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|Informuje o modulu CLR, že byla dokončena úloha hostitele a umožňuje CLR znovu použít aktuální `ICLRTask` instance představují jiná úloha.|  
|[RudeAbort – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|Způsobí, že CLR na zrušení úlohy reprezentována aktuální `ICLRTask` instance okamžitě, bez záruku, že bude proveden finalizační metody.|  
|[SetTaskIdentifier – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|Nastaví jedinečný identifikátor pro úlohu reprezentována aktuální `ICLRTask` instance pro použití při ladění.|  
|[SwitchIn – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|Upozorní CLR, která úloha reprezentována aktuální `ICLRTask` instance je ve stavu spustitelného.|  
|[SwitchOut – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|Upozorní CLR, která úloha reprezentována aktuální `ICLRTask` instance je již v spustitelného stavu.|  
|[YieldTask – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|Požadavky, které procesorového času zkontrolujte CLR k dispozici pro jiné úlohy. Modul CLR je zaručeno, že úloha bude přepnut ve stavu, kde přispět doba zpracování.|  
  
## <a name="remarks"></a>Poznámky  
 `ICLRTask` Je reprezentace úlohu pro modulu CLR. Kdykoli během provádění kódu lze popsat úlohu buď jako spuštěna nebo k čekání na spuštění. Volání hostitele `ICLRTask::SwitchIn` metoda oznámit modulu CLR, úlohy, aktuální `ICLRTask` představuje instanci je nyní v spustitelného stavu. Po volání `ICLRTask::SwitchIn`, hostiteli můžete naplánovat úlohu na všech vláknu operačního systému, s výjimkou v případech, kde vyžaduje modul runtime spřažení vláken, podle specifikace volání [ihosttaskmanager::beginthreadaffinity –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) a [Ihosttaskmanager::endthreadaffinity –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) metody. Některé později, operační systém rozhodnout odebrat úlohu z vlákna a umístěte ji ve stavu není spuštěná. Například k tomu může dojít vždy, když blokuje na synchronizace primitiv úlohu nebo čeká na dokončení vstupně-výstupních operací. Volání hostitele [switchout –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md) oznámit CLR, která úloha reprezentována aktuální `ICLRTask` instance je již v spustitelného stavu.  
  
 Úloha se obvykle ukončí na konci provádění kódu. V ten moment se volá hostitele `ICLRTask::ExitTask` zrušení přidruženého `ICLRTask`. Také však recyklované úlohy pomocí volání `ICLRTask::Reset`, což umožňuje `ICLRTask` instance, který se má použít znovu. Tento přístup zabraňuje režii opakovaně vytváření a zničení instancí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [ICLRTask2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
