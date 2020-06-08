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
ms.openlocfilehash: fd3c941d89fbd93f30fc1af235f6310b23758973
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501453"
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager – rozhraní
Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) vytvářet primitivy synchronizace voláním hostitele namísto použití synchronizačních funkcí Win32.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[CreateAutoEvent – metoda](ihostsyncmanager-createautoevent-method.md)|Vytvoří objekt události automatického resetování.|  
|[CreateCrst – metoda](ihostsyncmanager-createcrst-method.md)|Vytvoří objekt kritického oddílu pro synchronizaci.|  
|[CreateCrstWithSpinCount – metoda](ihostsyncmanager-createcrstwithspincount-method.md)|Vytvoří objekt kritického oddílu s počtem číselníků pro synchronizaci.|  
|[CreateManualEvent – metoda](ihostsyncmanager-createmanualevent-method.md)|Vytvoří objekt události ručního resetování.|  
|[CreateMonitorEvent – metoda](ihostsyncmanager-createmonitorevent-method.md)|Vytvoří monitorovaný objekt události automatického resetování.|  
|[CreateRWLockReaderEvent – metoda](ihostsyncmanager-createrwlockreaderevent-method.md)|Vytvoří objekt události ručního resetování pro implementaci zámku čtecího modulu.|  
|[CreateRWLockWriterEvent – metoda](ihostsyncmanager-createrwlockwriterevent-method.md)|Vytvoří objekt události automatického resetování pro implementaci zámku zapisovače.|  
|[CreateSemaphore – metoda](ihostsyncmanager-createsemaphore-method.md)|Vytvoří objekt [IHostSemaphore](ihostsemaphore-interface.md) pro CLR, který se použije jako semafor pro události čekání.|  
|[SetCLRSyncManager – metoda](ihostsyncmanager-setclrsyncmanager-method.md)|Nastaví instanci [ICLRSyncManager](iclrsyncmanager-interface.md) k přidružení k aktuální `IHostSyncManager` instanci.|  
  
## <a name="remarks"></a>Poznámky  
 CLR zjistí implementaci hostitele `IHostSyncManager` voláním metody [IHostControl:: gethostmanager –](ihostcontrol-gethostmanager-method.md) s `IID` IID_IHostSyncManager.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRSyncManager – rozhraní](iclrsyncmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
