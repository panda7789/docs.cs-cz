---
title: IHostSemaphore – rozhraní
ms.date: 03/30/2017
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
ms.openlocfilehash: 8345d85502087568cb05dd262cccf181e3ca07ac
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803692"
---
# <a name="ihostsemaphore-interface"></a>IHostSemaphore – rozhraní
Představuje implementaci semaforu pro vlákno.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ReleaseSemaphore – metoda](ihostsemaphore-releasesemaphore-method.md)|Zvýší počet aktuálních `IHostSemaphore` instancí o zadanou hodnotu.|  
|[Wait – metoda](ihostsemaphore-wait-method.md)|Způsobí, že aktuální `IHostSemaphore` instance počká, dokud je nevlastní nebo zadaná doba uplynula.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRSyncManager – rozhraní](iclrsyncmanager-interface.md)
- [IHostAutoEvent – rozhraní](ihostautoevent-interface.md)
- [IHostManualEvent – rozhraní](ihostmanualevent-interface.md)
- [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
