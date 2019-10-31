---
title: IHostTaskManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
ms.openlocfilehash: 470e2ac06f433dc12d66f6cac97337a6de1d8183
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133023"
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager – rozhraní
Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) pracovat s úlohami přes hostitele namísto použití standardních vláken operačního systému nebo funkcí vlákna.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginDelayAbort – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|Upozorňuje hostitele, že spravovaný kód vstupuje do období, ve kterém musí být aktuální úloha přerušena.|  
|[BeginThreadAffinity – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|Upozorňuje hostitele, že spravovaný kód vstupuje do období, ve kterém se aktuální úloha nesmí přesunout do jiného vlákna operačního systému.|  
|[CallNeedsHostHook – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|Umožňuje hostiteli určit, zda modul CLR (Common Language Runtime) může vložit zadané volání do nespravované funkce.|  
|[CreateTask – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|Požaduje, aby hostitel vytvořil novou úlohu.|  
|[EndDelayAbort – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|Upozorní hostitele, že spravovaný kód ukončuje období, ve kterém nesmí být aktuální úloha přerušena, po předchozím volání `BeginDelayAbort`.|  
|[EndThreadAffinity – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|Upozorní hostitele, že spravovaný kód ukončuje období, ve kterém nesmí být aktuální úloha přesunuta do jiného vlákna operačního systému za předchozích volání `BeginThreadAffinity`.|  
|[EnterRuntime – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|Upozorňuje hostitele, že volání nespravované metody, jako je například metoda Invoke platformy, vrací řízení provádění CLR.|  
|[GetCurrentTask – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|Získá ukazatel rozhraní na úlohu, která je aktuálně prováděna ve vlákně operačního systému, ze kterého je toto volání provedeno.|  
|[GetStackGuarantee – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|Získá velikost prostoru zásobníku, která je zaručena k dispozici po dokončení operace zásobníku, ale před zavřením procesu.|  
|[LeaveRuntime – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|Upozorňuje hostitele, že spravovaný kód se chystá uskutečnit volání nespravované funkce.|  
|[ReverseEnterRuntime – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|Upozorňuje hostitele, že je provedeno volání modulu CLR (Common Language Runtime) z nespravovaného kódu.|  
|[ReverseLeaveRuntime – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|Upozorňuje hostitele, že řízení opouští modul CLR a zadává nespravovanou funkci, která byla zase volána ze spravovaného kódu.|  
|[SetCLRTaskManager – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|Poskytuje hostitele s ukazatelem rozhraní na instanci [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) implementované modulem CLR.|  
|[SetLocale – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|Upozorňuje hostitele, že modul CLR změnil národní prostředí aktuální úlohy.|  
|[SetStackGuarantee – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|Vyhrazeno pouze pro interní použití.|  
|[SetUILocale – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|Upozorňuje hostitele, že národní prostředí uživatelského rozhraní bylo u aktuální úlohy změněno.|  
|[Sleep – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|Upozorní hostitele, že aktuální úloha přejde do režimu spánku.|  
|[SwitchToTask – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|Upozorňuje hostitele, že by měl přepnout aktuální úlohu.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostTaskManager` umožňuje modulu CLR vytvářet a spravovat úlohy, aby bylo možné zajistit, aby hostitel mohl provést akci při přesunu řízení z spravovaného do nespravovaného kódu a naopak, a určit určité akce, které hostitel může a nemůže provést během provádění kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
