---
title: ICLRAppDomainResourceMonitor::GetCurrentSurvived – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c179ba23be07e8ff77e1397ed753d4287b22440
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435282"
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRAppDomainResourceMonitor – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [Sledování prostředků domény aplikace](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
