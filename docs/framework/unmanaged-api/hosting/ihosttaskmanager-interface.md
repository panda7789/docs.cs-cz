---
title: "IHostTaskManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9573891a2c27a2a92eccd0522f84175effa8037a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager – rozhraní
Poskytuje metody, které povolit modul CLR (CLR) pro práci s úkoly prostřednictvím hostitele místo použití funkce dělení na vlákna nebo fiber standardní operační systém.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginDelayAbort – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|Upozorní, že hostitele, který spravovaný kód je zadání období, ve kterém nesmí přerušil aktuální úlohy.|  
|[BeginThreadAffinity – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|Upozorní, že hostitele, který spravovaný kód je zadání období, ve kterém nesmí být aktuální úlohy přesunout do jiné vlákno operačního systému.|  
|[CallNeedsHostHook – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|Umožňuje zadat, zda modul common language runtime můžete vložené zadaný volání nespravovaného funkce hostiteli.|  
|[CreateTask – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|Požadavky, že hostitel vytvořit novou úlohu.|  
|[EndDelayAbort – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|Upozorní hostitele, který je spravovaný kód je ukončení období, ve kterém nesmí být aktuální úloha byla přerušena, následující starší volání `BeginDelayAbort`.|  
|[EndThreadAffinity – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|Upozorní hostitele, který je spravovaný kód je ukončení období, ve kterém nesmí být aktuální úlohy přesunout do jiné vlákno operačního systému, následující starší volání `BeginThreadAffinity`.|  
|[EnterRuntime – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|Upozorní hostitele, že volání pro metodu nespravované, jako je platforma vyvolání metody vrací řízení provádění modulu CLR.|  
|[GetCurrentTask – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|Získá ukazatele rozhraní pro úlohu, která je aktuálně spuštěných ve vláknu operačního systému, ze kterého přišla tato žádost.|  
|[GetStackGuarantee – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|Získá velikost zásobníku místa, které se musí být k dispozici po dokončení operace zásobníku, ale před zavřením procesu.|  
|[LeaveRuntime – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|Upozorní, že hostitele, který spravovaného kódu se chystá provést volání do nespravované funkce.|  
|[ReverseEnterRuntime – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|Upozorní hostitele, že se provádí volání do common language runtime (CLR) z nespravovaného kódu.|  
|[ReverseLeaveRuntime – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|Hostitel upozorní, že je ovládací prvek ponechat modulu CLR a zadáním nespravované funkci, která byla, pak volané ze spravovaného kódu.|  
|[SetCLRTaskManager – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|Poskytuje ukazatele rozhraní na hostiteli [iclrtaskmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implementované modulu CLR.|  
|[SetLocale – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|Upozorní hostitele, že modulu CLR se změnila národního prostředí na aktuální úlohy.|  
|[SetStackGuarantee – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|Vyhrazeno pouze pro interní použití.|  
|[SetUILocale – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|Upozorní hostitele, národní prostředí uživatelského rozhraní se změnil na aktuální úlohy.|  
|[Sleep – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|Upozorní hostitele, že aktuální úlohy přechází do režimu spánku.|  
|[SwitchToTask – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|Upozorní hostitele, musí přepnout na aktuální úlohy.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostTaskManager`Umožňuje CLR vytvořit a spravovat úlohy, k poskytování háky pro hostitele zásah, kdy dojde k řízení přenosu ze spravovaného na nespravovaný kód a naopak a chcete zadat některé akce hostitele může a nelze provést během provádění kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
