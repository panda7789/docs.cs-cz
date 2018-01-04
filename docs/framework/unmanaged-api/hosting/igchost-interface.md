---
title: "IGCHost – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost
helpviewer_keywords: IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 77a2cab35785aa39571d39bdd369fa26cdbcd1d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="igchost-interface"></a>IGCHost – rozhraní
Poskytuje metody pro získání informací o systém kolekce paměti a řízení některých aspektů uvolňování paměti.  
  
> [!NOTE]
>  Od verze [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], můžete použít [igchost2::setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metodu a nastavit velikost segment kolekce paměti a maximální velikost systém kolekce paměti generace 0 hodnoty větší než `DWORD` omezení, která je dáno [setgcstartuplimits –](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) metoda.  
  
> [!NOTE]
>  Toto rozhraní je pouze odborné využití. Pokud použili nesprávně může ovlivnit výkon aplikace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Collect – metoda](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|Vynutí kolekci vyskytují pro danou generaci, bez ohledu na stav v aktuální kolekci paměti.|  
|[GetStats – metoda](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|Získá statistiku pro aktuální stav kolekce systém uvolňování paměti.|  
|[GetThreadStats – metoda](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|Získá statistiku objektů vlákno pro uvolňování paměti.|  
|[SetGCStartupLimits – metoda](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|Nastaví velikost segmentu a maximální velikost pro generování 0.|  
|[SetVirtualMemLimit – metoda](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|Nastaví maximální velikost virtuální paměti modulu runtime.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** GCHost.idl, GCHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CorRuntimeHost – třída typu coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
