---
title: ICLRAppDomainResourceMonitor – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
ms.openlocfilehash: 08dc0f0891d960cb7b402b30455e606aaff7bcea
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616005"
---
# <a name="iclrappdomainresourcemonitor-interface"></a>ICLRAppDomainResourceMonitor – rozhraní
Poskytuje metody, které kontrolují paměť a využití procesoru v doméně aplikace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetCurrentAllocated – metoda](iclrappdomainresourcemonitor-getcurrentallocated-method.md)|Získá celkovou velikost přidělení paměti (v bajtech), která byla vytvořena aplikační doménou od jejího vytvoření, bez odčítání paměti, která byla uvolněna do paměti.|  
|[GetCurrentSurvived – metoda](iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|Vrátí počet bajtů, které byly zachovány při posledním plném, blokování uvolnění paměti a odkazují aktuální doménu aplikace.|  
|[GetCurrentCpuTime – metoda](iclrappdomainresourcemonitor-getcurrentcputime-method.md)|Získá celkový čas procesoru používaný všemi vlákny při spuštění v aktuální doméně aplikace, protože byla vytvořena doména aplikace.|  
  
## <a name="remarks"></a>Poznámky  
 `ICLRAppDomainResourceMonitor`Rozhraní poskytuje funkce, které jsou podobné následujícím spravovaným vlastnostem:  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [\<appDomainResourceMonitoring – element>](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [Monitorování prostředků domény aplikace](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
- [Hostování](index.md)
