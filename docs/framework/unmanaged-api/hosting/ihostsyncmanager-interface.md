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
ms.openlocfilehash: 02a59b8ef63f7e866e419db4e3232da7eec19558
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132632"
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager – rozhraní
Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) vytvářet primitivy synchronizace voláním hostitele namísto použití synchronizačních funkcí Win32.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateAutoEvent – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|Vytvoří objekt události automatického resetování.|  
|[CreateCrst – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|Vytvoří objekt kritického oddílu pro synchronizaci.|  
|[CreateCrstWithSpinCount – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|Vytvoří objekt kritického oddílu s počtem číselníků pro synchronizaci.|  
|[CreateManualEvent – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|Vytvoří objekt události ručního resetování.|  
|[CreateMonitorEvent – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|Vytvoří monitorovaný objekt události automatického resetování.|  
|[CreateRWLockReaderEvent – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|Vytvoří objekt události ručního resetování pro implementaci zámku čtecího modulu.|  
|[CreateRWLockWriterEvent – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|Vytvoří objekt události automatického resetování pro implementaci zámku zapisovače.|  
|[CreateSemaphore – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|Vytvoří objekt [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) pro CLR, který se použije jako semafor pro události čekání.|  
|[SetCLRSyncManager – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|Nastaví instanci [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) k přidružení k aktuální instanci `IHostSyncManager`.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR zjistí implementaci `IHostSyncManager` hostitele voláním metody [IHostControl:: GetHostManager –](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) s `IID` IID_IHostSyncManager.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
