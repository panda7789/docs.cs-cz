---
title: "ICLRAppDomainResourceMonitor::GetCurrentSurvived – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 612e27120196d2920b75c030929af1807d4a336f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a>ICLRAppDomainResourceMonitor::GetCurrentSurvived – metoda
Získá počet bajtů, který zůstal naživu poslední úplné, blokování uvolňování paměti a který se odkazuje aktuální doménu aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwAppDomainId`  
 [v] ID domény požadovaná aplikace.  
  
 `pAppDomainBytesSurvived`  
 [out] Ukazatel na počet bajtů, které zůstal naživu po poslední uvolnění paměti, které jsou uložené tato doména aplikace. Toto číslo po úplnou kolekci, je přesné a úplné. Toto číslo je po dočasné kolekce, potenciálně neúplné. Tento parametr může být `null`.  
  
 `pRuntimeBytesSurvived`  
 [out] Ukazatel na celkový počet bajtů, které zůstal naživu z poslední uvolnění paměti. Po kompletní sadu toto číslo představuje počet bajtů, které jsou uložené ve spravovaných haldách. Po dočasné kolekce toto číslo představuje počet bajtů, které jsou uložené v dočasných generace za provozu. Tento parametr může být `null`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|COR_E_APPDOMAINUNLOADED|Doména aplikace byl odpojen nebo neexistuje.|  
  
## <a name="remarks"></a>Poznámky  
 Se statistika aktualizuje až po úplné, blokování uvolňování; To znamená dojde k kolekci, která obsahuje všechny generace a který ukončí aplikaci při kolekce. Například <xref:System.GC.Collect?displayProperty=nameWithType> přetížení metody provede úplnou, blokování kolekce. Souběžné uvolňování probíhá na pozadí a neblokuje aplikace.  
  
 `GetCurrentSurvived` Metoda je ekvivalentem nespravované spravované <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRAppDomainResourceMonitor – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [Sledování prostředků domény aplikace](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
