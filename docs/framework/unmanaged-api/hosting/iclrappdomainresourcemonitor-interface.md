---
title: "ICLRAppDomainResourceMonitor – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor
helpviewer_keywords: ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bebd39fce4f6aa6f570b3af348332bf7bcc87ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrappdomainresourcemonitor-interface"></a>ICLRAppDomainResourceMonitor – rozhraní
Poskytuje metody, které zkontrolovat doménu aplikace využití paměti a procesoru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetCurrentAllocated – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|Získá celková velikost v bajtech přidělených paměti, které jste provedli pro doménu aplikace, protože byl vytvořen bez odečtením paměti, která byla uvolněna.|  
|[GetCurrentSurvived – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|Získá počet bajtů, který zůstal naživu poslední úplné, blokování uvolňování paměti a který se odkazuje aktuální doménu aplikace.|  
|[GetCurrentCpuTime – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|Získá celkový procesorového času, který byl použit pro všechna vlákna při provádění v aktuální doméně aplikace, že se od vytvoření domény aplikace.|  
  
## <a name="remarks"></a>Poznámky  
 `ICLRAppDomainResourceMonitor` Rozhraní poskytuje funkce, které je podobná následující spravované vlastnosti:  
  
-   <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [\<appdomainresourcemonitoring – > elementu](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [Sledování prostředků domény aplikace](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
