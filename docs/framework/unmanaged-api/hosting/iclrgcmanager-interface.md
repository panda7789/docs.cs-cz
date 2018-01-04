---
title: "ICLRGCManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager
helpviewer_keywords: ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6cc6c84d57e4114a28a8b363b99b98f3c4d21410
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager – rozhraní
Poskytuje metody, které umožňují hostitele k interakci s systém kolekce paměti modul common language runtime.  
  
> [!NOTE]
>  Od verze [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], můžete použít [iclrgcmanager2::setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metodu a nastavit velikost segment kolekce paměti a maximální velikost systém kolekce paměti generace 0 hodnoty větší než `DWORD` omezení, která je dáno [setgcstartuplimits –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) metoda.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Collect – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|Vynutí uvolnění paměti pro zadané generaci.|  
|[GetStats – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|Získá sadu aktuální statistické údaje o kolekci systém uvolňování paměti.|  
|[SetGCStartupLimits – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|Nastaví velikost segment kolekce paměti a maximální velikost systém kolekce paměti generace 0.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR (CLR) implementuje mechanismus kolekce jeho paměti s spravovaný <xref:System.GC> typu. Další informace o systém kolekce paměti najdete v tématu [uvolňování paměti](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Automatická správa paměti](../../../../docs/standard/automatic-memory-management.md)  
 [COR_GC_STATS – struktura](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Rozhraní pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
