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
ms.openlocfilehash: e96492270c403f93687245cee8b680dc16b3c787
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803127"
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager – rozhraní
Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) vytvářet primitivy synchronizace voláním hostitele namísto použití synchronizačních funkcí Win32.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateAutoEvent – metoda](ihostsyncmanager-createautoevent-method.md)|Vytvoří objekt události automatického resetování.|  
|[CreateCrst – metoda](ihostsyncmanager-createcrst-method.md)|Vytvoří objekt kritického oddílu pro synchronizaci.|  
|[CreateCrstWithSpinCount – metoda](ihostsyncmanager-createcrstwithspincount-method.md)|Vytvoří objekt kritického oddílu s počtem číselníků pro synchronizaci.|  
|[CreateManualEvent – metoda](ihostsyncmanager-createmanualevent-method.md)|Vytvoří objekt události ručního resetování.|  
|[CreateMonitorEvent – metoda](ihostsyncmanager-createmonitorevent-method.md)|Vytvoří monitorovaný objekt události automatického resetování.|  
|[CreateRWLockReaderEvent – metoda](ihostsyncmanager-createrwlockreaderevent-method.md)|Vytvoří objekt události ručního resetování pro implementaci zámku čtecího modulu.|  
|[CreateRWLockWriterEvent – metoda](ihostsyncmanager-createrwlockwriterevent-method.md)|Vytvoří objekt události automatického resetování pro implementaci zámku zapisovače.|  
|[CreateSemaphore – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|Vytvoří objekt [IHostSemaphore](ihostsemaphore-interface.md) pro CLR, který se použije jako semafor pro události čekání.|  
|[SetCLRSyncManager – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|Nastaví instanci [ICLRSyncManager](iclrsyncmanager-interface.md) k přidružení k aktuální `IHostSyncManager` instanci.|  
  
## <a name="remarks"></a>Poznámky  
 CLR zjistí implementaci hostitele `IHostSyncManager` voláním metody [IHostControl:: gethostmanager –](ihostcontrol-gethostmanager-method.md) s `IID` IID_IHostSyncManager.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRSyncManager – rozhraní](iclrsyncmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
