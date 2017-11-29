---
title: "IHostSyncManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager
helpviewer_keywords: IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 951f7808e238f514ffcf19a8dda0033b7b07172c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager – rozhraní
Poskytuje metody, které povolit modul CLR (CLR) k vytvoření synchronizace primitiv voláním hostitele místo použití funkce synchronizace Win32.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Createautoevent – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|Vytvoří objekt události automatického vynulování.|  
|[Createcrst – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|Vytvoří objekt kritická sekce modulu pro synchronizaci.|  
|[Createcrstwithspincount – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|Vytvoří objekt kritická sekce s počtem typu číselník pro synchronizaci.|  
|[Createmanualevent – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|Vytvoří objekt Ruční vynulování události.|  
|[Createmonitorevent – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|Vytvoří objekt monitorovanou událost automatického vynulování.|  
|[Createrwlockreaderevent – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|Vytvoří objekt Ruční vynulování události pro implementaci zámek pro čtení.|  
|[Createrwlockwriterevent – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|Vytvoří objekt automatickým vynulováním událostí k provádění zámek pro zápis.|  
|[Createsemaphore – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|Vytvoří [ihostsemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) objekt pro CLR, které chcete použít jako semafor pro události čekání.|  
|[Setclrsyncmanager – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|Nastaví [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance přidružení k aktuální `IHostSyncManager` instance.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR zjistí implementace hostitele `IHostSyncManager` voláním [ihostcontrol::gethostmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) metoda s `IID` z IID_IHostSyncManager.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Iclrsyncmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [Rozhraní hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
