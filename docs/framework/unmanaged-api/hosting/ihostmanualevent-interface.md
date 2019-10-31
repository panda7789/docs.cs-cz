---
title: IHostManualEvent – rozhraní
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
ms.openlocfilehash: 8eba189d6dfca3781c28631a72a9af3c037efeda
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136785"
---
# <a name="ihostmanualevent-interface"></a>IHostManualEvent – rozhraní
Poskytuje implementaci reprezentace události ručního resetování hostitele.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|Obnoví aktuální instanci `IHostManualEvent` na stav bez signalizace.|  
|[Set – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|Nastaví aktuální instanci `IHostManualEvent` na signálový stav.|  
|[Wait – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|Způsobí, že aktuální instance `IHostManualEvent` počká, dokud není vlastněná, nebo dokud neuplyne zadaný čas.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostAutoEvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [IHostSemaphore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
