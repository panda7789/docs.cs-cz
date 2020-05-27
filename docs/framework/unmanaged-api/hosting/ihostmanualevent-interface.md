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
ms.openlocfilehash: 7c46f00063cdf9281a5f1080594e8d6dbc6c101e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804598"
---
# <a name="ihostmanualevent-interface"></a>IHostManualEvent – rozhraní
Poskytuje implementaci reprezentace události ručního resetování hostitele.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Reset – metoda](ihostmanualevent-reset-method.md)|Obnoví aktuální `IHostManualEvent` instanci na stav bez signalizace.|  
|[Set – metoda](ihostmanualevent-set-method.md)|Nastaví aktuální `IHostManualEvent` instanci na signálový stav.|  
|[Wait – metoda](ihostmanualevent-wait-method.md)|Způsobí, že aktuální `IHostManualEvent` instance počká, až bude ve vlastnictví, nebo zadanou dobu uplyne.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRSyncManager – rozhraní](iclrsyncmanager-interface.md)
- [IHostAutoEvent – rozhraní](ihostautoevent-interface.md)
- [IHostSemaphore – rozhraní](ihostsemaphore-interface.md)
- [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
