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
ms.openlocfilehash: 1baeac5db41aa64380d694ebab5419229d8adb4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763539"
---
# <a name="iclrtask-interface"></a>ICLRTask – rozhraní
Poskytuje metody, které umožňují hostitele k podání žádostí o modulu common language runtime (CLR), nebo k poskytování oznámení o přidružené úloze modulu CLR.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Abort – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|Požadavky, že modul CLR přerušit úlohu, která aktuální `ICLRTask` instance představuje.|  
|[ExitTask – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|Upozorní CLR, který úlohy spojené s aktuálním `ICLRTask` instance ukončuje a pokusí se řádně úlohu ukončit.|  
|[GetMemStats – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|Získá statistické informace týkající se použití paměťových prostředků úlohou reprezentované aktuální `ICLRTask` instance.|  
|[LocksHeld – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|Získá počet zámků právě načtený v úloze.|  
|[NeedsPriorityScheduling – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|Získá hodnotu označující, zda hostitel s vysokou prioritou má přiřadit změnou plánu úlohy reprezentované aktuální `ICLRTask` instance.|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|Informuje o tom CLR, že byla dokončena úloha hostitele a umožňuje modulu CLR pro opětovné použití aktuální `ICLRTask` instance k reprezentování jiného úkolu.|  
|[RudeAbort – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|Způsobí, že modul CLR na zrušení úlohy reprezentované aktuální `ICLRTask` instance okamžitě, bez záruky, že se spustí finalizační metody.|  
|[SetTaskIdentifier – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|Nastaví jedinečný identifikátor pro úlohu reprezentované aktuální `ICLRTask` instance pro použití v ladění.|  
|[SwitchIn – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|Upozorní CLR, která úloha je reprezentována aktuální `ICLRTask` instance je do provozuschopného stavu.|  
|[SwitchOut – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|Upozorní CLR, která úloha je reprezentována aktuální `ICLRTask` instance již provozuschopného stavu.|  
|[YieldTask – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|Požadavky procesorového času zkontrolujte CLR k dispozici pro jiné úlohy. Modul CLR je zaručeno, že úlohy budou umístěny ve stavu, ve kterém se může přinést doba zpracování.|  
  
## <a name="remarks"></a>Poznámky  
 `ICLRTask` Je reprezentace úlohu pro modul CLR. Kdykoli během provádění kódu lze popsat úkol buď jako spuštěna nebo k čekání na spuštění. Volání hostitele `ICLRTask::SwitchIn` metoda upozornit modul CLR, která úkol, který aktuální `ICLRTask` představuje instanci je teď v provozuschopného stavu. Po volání `ICLRTask::SwitchIn`, hostitele můžete naplánovat úlohu v libovolném vlákně operačního systému, s výjimkou v případech, kdy vyžaduje, aby modul runtime spřažení vláken, jak je uvedeno ve volání [ihosttaskmanager::beginthreadaffinity –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) a [Ihosttaskmanager::endthreadaffinity –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) metody. Později, operační systém rozhodnout odebrat úlohu z vlákna a umístěte ho do jiné spuštěném stavu. Například k tomu může dojít pokaždé, když se úkol zablokuje v primitivních elementů synchronizace nebo čeká na dokončení vstupně-výstupních operací. Volání hostitele [switchout –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md) upozornit modul CLR, která úloha je reprezentována aktuální `ICLRTask` instance již provozuschopného stavu.  
  
 Úloha obvykle ukončí provádění kódu na konci. V tu chvíli hostitele volá `ICLRTask::ExitTask` ke zničení přidruženého `ICLRTask`. Také však recyklaci úlohy s použitím volání `ICLRTask::Reset`, což umožňuje `ICLRTask` instance se použije znovu. Tento postup brání režijní náklady na opakované vytváření a ničení instancí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ICLRTask2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
