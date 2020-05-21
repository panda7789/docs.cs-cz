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
ms.openlocfilehash: 419baaf64397830ef86cfd9e5c3437e3f5b57795
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763004"
---
# <a name="iclrtask-interface"></a>ICLRTask – rozhraní
Poskytuje metody, které umožňují hostiteli vytvářet požadavky na modul CLR (Common Language Runtime) nebo poskytnout oznámení modulu CLR o přidružené úloze.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Abort – metoda](iclrtask-abort-method.md)|Požaduje, aby modul CLR přerušil úlohu, kterou `ICLRTask` představuje aktuální instance.|  
|[ExitTask – metoda](iclrtask-exittask-method.md)|Upozorní modul CLR na ukončení úlohy související s aktuální `ICLRTask` instancí a pokusí se o řádné ukončení úlohy.|  
|[GetMemStats – metoda](iclrtask-getmemstats-method.md)|Získá statistické informace o použití paměťových prostředků podle úlohy reprezentované aktuální `ICLRTask` instancí.|  
|[LocksHeld – metoda](iclrtask-locksheld-method.md)|Získá počet zámků, které jsou aktuálně uchovávány na úkolu.|  
|[NeedsPriorityScheduling – metoda](iclrtask-needspriorityscheduling-method.md)|Načte hodnotu, která označuje, jestli má hostitel přiřadit vysokou prioritu pro přeplánování úlohy reprezentované aktuální `ICLRTask` instancí.|  
|[Reset – metoda](iclrtask-reset-method.md)|Informuje CLR, že hostitel dokončil úlohu, a umožňuje, aby CLR znovu používá aktuální `ICLRTask` instanci pro reprezentaci jiné úlohy.|  
|[RudeAbort – metoda](iclrtask-rudeabort-method.md)|Způsobí, že CLR ukončí úlohu představovanou aktuální `ICLRTask` instancí hned bez záruky, že se spustí finalizační metody.|  
|[SetTaskIdentifier – metoda](iclrtask-settaskidentifier-method.md)|Nastaví jedinečný identifikátor pro úlohu reprezentovanou aktuální `ICLRTask` instancí pro použití při ladění.|  
|[SwitchIn – metoda](iclrtask-switchin-method.md)|Upozorní CLR, že úkol reprezentovaný aktuální `ICLRTask` instancí je v provozuschopném stavu.|  
|[SwitchOut – metoda](iclrtask-switchout-method.md)|Upozorní CLR, že úkol reprezentovaný aktuální `ICLRTask` instancí už není v funkčním stavu.|  
|[YieldTask – metoda](iclrtask-yieldtask-method.md)|Požaduje, aby modul CLR k dispozici čas procesoru pro jiné úlohy. CLR nezaručuje, že úloha bude vložena do stavu, ve kterém může přinést dobu zpracování.|  
  
## <a name="remarks"></a>Poznámky  
 `ICLRTask`Je reprezentace úkolu pro modul CLR. V jakémkoli okamžiku při provádění kódu lze úlohu popsat buď spuštěním, nebo čekáním na spuštění. Hostitel volá `ICLRTask::SwitchIn` metodu pro informování CLR, že úloha, kterou aktuální `ICLRTask` instance představuje, je nyní v provozuschopném stavu. Po volání `ICLRTask::SwitchIn` může hostitel naplánovat úlohu v jakémkoli vlákně operačního systému, s výjimkou případů, kdy modul runtime vyžaduje spřažení vlákna, jak je určeno voláním metody [IHostTaskManager:: BeginThreadAffinity –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) a [IHostTaskManager:: EndThreadAffinity –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) . Později se operační systém může rozhodnout odebrat úlohu z vlákna a umístit ji do nespuštěného stavu. K tomu může dojít například pokaždé, když jsou bloky úkolu v rámci synchronizace nebo když čekají na dokončení vstupně-výstupních operací. Hostitel volá [přepínač](iclrtask-switchout-method.md) pro informování CLR, že úloha reprezentovaná aktuální instancí již `ICLRTask` není v funkčním stavu.  
  
 Úkol obvykle končí na konci provádění kódu. V tomto okamžiku hostitel volá `ICLRTask::ExitTask` zničení přidruženého `ICLRTask` . Úkoly lze však také recyklovat pomocí volání `ICLRTask::Reset` , což umožňuje `ICLRTask` znovu použít instanci. Tento přístup znemožňuje režii opakovaného vytváření a zničení instancí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRTaskManager – rozhraní](iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](ihosttask-interface.md)
- [IHostTaskManager – rozhraní](ihosttaskmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
- [ICLRTask2 – rozhraní](iclrtask2-interface.md)
