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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad580f7cab81323e09a24dc12db39f223be3aeb4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973060"
---
# <a name="ihostmanualevent-interface"></a>IHostManualEvent – rozhraní
Poskytuje implementaci hostitele reprezentace Ruční vynulování události.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|Obnoví aktuální `IHostManualEvent` instance do nesignálového stavu.|  
|[Set – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|Nastaví aktuální `IHostManualEvent` instance do signalizovaného stavu.|  
|[Wait – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|Způsobí, že aktuální `IHostManualEvent` instance počkat, dokud je ve vlastnictví nebo zadaného množství času po uplynutí předem.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostAutoEvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [IHostSemaphore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
