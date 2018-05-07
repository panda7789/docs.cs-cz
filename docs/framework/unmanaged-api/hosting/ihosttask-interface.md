---
title: IHostTask – rozhraní
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df1fb24c4003f77523ef01a4029fd19cc55a3fef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttask-interface"></a>IHostTask – rozhraní
Poskytuje metody, které povolit modul CLR (CLR) ke komunikaci s hostitelem ke správě úloh.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Alert – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|Požadavky, že hostitel wake úlohu reprezentována aktuální `IHostTask` instance, takže úlohu můžete byl zrušen.|  
|[GetPriority – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|Získá přístup z více vláken úroveň priority úlohy reprezentována aktuální `IHostTask` instance.|  
|[Join – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|Blokuje volání úkolů dokud je úloha reprezentována aktuální `IHostTask` instance dokončí, uplynutí zadaného časového intervalu nebo [ihosttask::alert –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) je volána.|  
|[SetCLRTask – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|Přidruží [iclrtask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s aktuálním `IHostTask` instance.|  
|[SetPriority – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|Požadavky, že hostitel upravit prioritu podprocesu úrovně pro úlohu reprezentována aktuální `IHostTask` instance.|  
|[Start – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|Požadavky, že hostitel move – úloha reprezentována aktuální `IHostTask` instance z režimu spánku za provozu stavu, ve kterém můžete spustit kód.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR volá metody, které jsou definované `IHostTask` Pokud chcete spustit úlohu, nastavit její prioritu podprocesu úroveň, a tak dále.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
