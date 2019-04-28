---
title: IHostSyncManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 200da8b87b52a29c2b075d1e06929031d3f588b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769626"
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager – rozhraní
Poskytuje metody, které umožňují common language runtime (CLR) k vytvoření synchronizací primitiv voláním hostitele namísto použití funkce synchronizace Win32.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateAutoEvent – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|Vytvoří objekt události automatického obnovení.|  
|[CreateCrst – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|Vytvoří objekt kritický oddíl pro synchronizaci.|  
|[CreateCrstWithSpinCount – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|Vytvoří objekt kritický oddíl s počtem typu číselník pro synchronizaci.|  
|[CreateManualEvent – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|Vytvoří objekt ruční obnovení události.|  
|[CreateMonitorEvent – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|Vytvoří objekt monitorovanou událost automatického obnovení.|  
|[CreateRWLockReaderEvent – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|Vytvoří objekt ruční obnovení události pro implementaci zámku čtecího modulu.|  
|[CreateRWLockWriterEvent – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|Vytvoří objekt automatického resetu pro provádění zapisovací zámek.|  
|[CreateSemaphore – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|Vytvoří [ihostsemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) objektu pro modul CLR, který chcete použít jako semafor pro události čekání.|  
|[SetCLRSyncManager – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|Nastaví [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instanci přidružit s aktuálním `IHostSyncManager` instance.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR zjistí hostitele provádění `IHostSyncManager` voláním [ihostcontrol::gethostmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) metodou `IID` z IID_IHostSyncManager.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
