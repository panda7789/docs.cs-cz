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
ms.openlocfilehash: c4f27a73022b0495b2772c0485c14a1b007dc883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132636"
---
# <a name="iclrtask-interface"></a>ICLRTask – rozhraní
Poskytuje metody, které umožňují hostiteli vytvářet požadavky na modul CLR (Common Language Runtime) nebo poskytnout oznámení modulu CLR o přidružené úloze.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Abort – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|Požaduje, aby modul CLR přerušil úlohu, kterou představuje aktuální instance `ICLRTask`.|  
|[ExitTask – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|Upozorní modul CLR na ukončení úkolu přidruženého k aktuální instanci `ICLRTask` a pokusí se o řádné ukončení úlohy.|  
|[GetMemStats – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|Získá statistické informace o používání prostředků paměti podle úkolu reprezentovaného aktuální instancí `ICLRTask`.|  
|[LocksHeld – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|Získá počet zámků, které jsou aktuálně uchovávány na úkolu.|  
|[NeedsPriorityScheduling – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|Získá hodnotu, která označuje, jestli má hostitel přiřadit vysokou prioritu pro přeplánování úlohy reprezentované aktuální instancí `ICLRTask`.|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|Informuje CLR, že hostitel dokončil úlohu, a umožňuje, aby CLR znovu používá aktuální instanci `ICLRTask` k tomu, aby reprezentovala jinou úlohu.|  
|[RudeAbort – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|Způsobí, že modul CLR přeruší úlohu představovanou aktuální instancí `ICLRTask` hned bez záruky, že se spustí finalizační metody.|  
|[SetTaskIdentifier – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|Nastaví jedinečný identifikátor pro úlohu reprezentovanou aktuální instancí `ICLRTask` pro použití při ladění.|  
|[SwitchIn – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|Upozorní CLR, že úkol reprezentovaný aktuální instancí `ICLRTask` je v provozuschopném stavu.|  
|[SwitchOut – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|Upozorní CLR, že úkol reprezentovaný aktuální `ICLRTask` instance už není v funkčním stavu.|  
|[YieldTask – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|Požaduje, aby modul CLR k dispozici čas procesoru pro jiné úlohy. CLR nezaručuje, že úloha bude vložena do stavu, ve kterém může přinést dobu zpracování.|  
  
## <a name="remarks"></a>Poznámky  
 `ICLRTask` je reprezentace úlohy pro modul CLR. V jakémkoli okamžiku při provádění kódu lze úlohu popsat buď spuštěním, nebo čekáním na spuštění. Hostitel volá metodu `ICLRTask::SwitchIn` pro informování CLR, že úloha, kterou aktuální instance `ICLRTask` představuje, je nyní v provozuschopném stavu. Po volání `ICLRTask::SwitchIn`může hostitel naplánovat úlohu v jakémkoli vlákně operačního systému, s výjimkou případů, kdy modul runtime vyžaduje spřažení vlákna, jak je určeno voláním metody [IHostTaskManager:: BeginThreadAffinity –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) a [IHostTaskManager:: Metody EndThreadAffinity –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) . Později se operační systém může rozhodnout odebrat úlohu z vlákna a umístit ji do nespuštěného stavu. K tomu může dojít například pokaždé, když jsou bloky úkolu v rámci synchronizace nebo když čekají na dokončení vstupně-výstupních operací. Hostitel volá [přepínač](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md) pro informování CLR, že úloha reprezentovaná aktuální instancí `ICLRTask` již není v provozuschopném stavu.  
  
 Úkol obvykle končí na konci provádění kódu. V tomto okamžiku hostitel volá `ICLRTask::ExitTask` k zničení přidružené `ICLRTask`. Úlohy však lze také recyklovat pomocí volání `ICLRTask::Reset`, což umožňuje znovu použít instanci `ICLRTask`. Tento přístup znemožňuje režii opakovaného vytváření a zničení instancí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ICLRTask2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
