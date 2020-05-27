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
ms.openlocfilehash: b742f717f4caa0ba23d5a4c1438ed3ce4dcc60d7
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842254"
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager – rozhraní
Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) pracovat s úlohami přes hostitele namísto použití standardních vláken operačního systému nebo funkcí vlákna.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginDelayAbort – metoda](ihosttaskmanager-begindelayabort-method.md)|Upozorňuje hostitele, že spravovaný kód vstupuje do období, ve kterém musí být aktuální úloha přerušena.|  
|[BeginThreadAffinity – metoda](ihosttaskmanager-beginthreadaffinity-method.md)|Upozorňuje hostitele, že spravovaný kód vstupuje do období, ve kterém se aktuální úloha nesmí přesunout do jiného vlákna operačního systému.|  
|[CallNeedsHostHook – metoda](ihosttaskmanager-callneedshosthook-method.md)|Umožňuje hostiteli určit, zda modul CLR (Common Language Runtime) může vložit zadané volání do nespravované funkce.|  
|[CreateTask – metoda](ihosttaskmanager-createtask-method.md)|Požaduje, aby hostitel vytvořil novou úlohu.|  
|[EndDelayAbort – metoda](ihosttaskmanager-enddelayabort-method.md)|Upozorní hostitele, že spravovaný kód ukončuje období, ve kterém nesmí být aktuální úloha přerušena po předchozím volání `BeginDelayAbort` .|  
|[EndThreadAffinity – metoda](ihosttaskmanager-endthreadaffinity-method.md)|Upozorní hostitele, že spravovaný kód ukončuje období, ve kterém nesmí být aktuální úloha přesunuta do jiného vlákna operačního systému po předchozím volání `BeginThreadAffinity` .|  
|[EnterRuntime – metoda](ihosttaskmanager-enterruntime-method.md)|Upozorňuje hostitele, že volání nespravované metody, jako je například metoda Invoke platformy, vrací řízení provádění CLR.|  
|[GetCurrentTask – metoda](ihosttaskmanager-getcurrenttask-method.md)|Získá ukazatel rozhraní na úlohu, která je aktuálně prováděna ve vlákně operačního systému, ze kterého je toto volání provedeno.|  
|[GetStackGuarantee – metoda](ihosttaskmanager-getstackguarantee-method.md)|Získá velikost prostoru zásobníku, která je zaručena k dispozici po dokončení operace zásobníku, ale před zavřením procesu.|  
|[LeaveRuntime – metoda](ihosttaskmanager-leaveruntime-method.md)|Upozorňuje hostitele, že spravovaný kód se chystá uskutečnit volání nespravované funkce.|  
|[ReverseEnterRuntime – metoda](ihosttaskmanager-reverseenterruntime-method.md)|Upozorňuje hostitele, že je provedeno volání modulu CLR (Common Language Runtime) z nespravovaného kódu.|  
|[ReverseLeaveRuntime – metoda](ihosttaskmanager-reverseleaveruntime-method.md)|Upozorňuje hostitele, že řízení opouští modul CLR a zadává nespravovanou funkci, která byla zase volána ze spravovaného kódu.|  
|[SetCLRTaskManager – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|Poskytuje hostitele s ukazatelem rozhraní na instanci [ICLRTaskManager](iclrtaskmanager-interface.md) implementované modulem CLR.|  
|[SetLocale – metoda](ihosttaskmanager-setlocale-method.md)|Upozorňuje hostitele, že modul CLR změnil národní prostředí aktuální úlohy.|  
|[SetStackGuarantee – metoda](ihosttaskmanager-setstackguarantee-method.md)|Vyhrazeno pouze pro interní použití.|  
|[SetUILocale – metoda](ihosttaskmanager-setuilocale-method.md)|Upozorňuje hostitele, že národní prostředí uživatelského rozhraní bylo u aktuální úlohy změněno.|  
|[Sleep – metoda](ihosttaskmanager-sleep-method.md)|Upozorní hostitele, že aktuální úloha přejde do režimu spánku.|  
|[SwitchToTask – metoda](ihosttaskmanager-switchtotask-method.md)|Upozorňuje hostitele, že by měl přepnout aktuální úlohu.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostTaskManager`umožňuje modulu CLR vytvářet a spravovat úlohy, aby bylo možné zajistit, aby hostitel mohl provést akci při přenosech ovládacích prvků ze spravovaného do nespravovaného kódu a naopak, a určit určité akce, které hostitel může a nemůže provést během provádění kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRTask – rozhraní](iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](ihosttask-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
