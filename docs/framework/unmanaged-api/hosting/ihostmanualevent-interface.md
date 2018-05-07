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
ms.openlocfilehash: 53aaf4c23861666962e5567a6cf9eb9fffc6292f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ihostmanualevent-interface"></a>IHostManualEvent – rozhraní
Poskytuje implementaci hostitele reprezentace Ruční vynulování události.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|Obnoví aktuální `IHostManualEvent` instance do stavu signál.|  
|[Set – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|Nastaví aktuální `IHostManualEvent` instance do signalizovaného stavu.|  
|[Wait – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|Způsobí, že aktuální `IHostManualEvent` instance počkat, dokud je vlastněná nebo zadaného množství času po uplynutí předem.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostAutoEvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [IHostSemaphore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
