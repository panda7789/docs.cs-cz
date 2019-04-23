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
ms.openlocfilehash: 408ef5419fbc2081d25ad442986ec8155bcb4c62
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141541"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a>ICLRAppDomainResourceMonitor::GetCurrentSurvived – metoda
Získá počet bajtů, které zůstat naživu při poslední úplné blokující uvolňování paměti a, který je odkazováno dle aktuální domény aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwAppDomainId`  
 [in] ID domény požadované aplikace.  
  
 `pAppDomainBytesSurvived`  
 [out] Ukazatel na počet bajtů, které zůstat naživu po poslední uvolnění paměti, které jsou uloženy v této doméně aplikace. Toto číslo po celé kolekce, je přesné a úplné. Toto číslo je po dočasné kolekce, potenciálně neúplné. Tento parametr může být `null`.  
  
 `pRuntimeBytesSurvived`  
 [out] Ukazatel na celkový počet bajtů, které zůstat naživu z posledního kolekce uvolnění paměti. Po celé kolekce toto číslo představuje počet bajtů, které jsou uloženy ve spravované haldy. Po dočasné kolekce toto číslo představuje počet bajtů, které jsou uloženy v dočasné generace. Tento parametr může být `null`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|COR_E_APPDOMAINUNLOADED|Aplikační domény byl odpojen nebo neexistuje.|  
  
## <a name="remarks"></a>Poznámky  
 Statistiky jsou aktualizovány pouze po úplné blokující uvolňování paměti; To znamená, že dojde k kolekci, která obsahuje všechny generace, která ukončí aplikaci při shromažďování. Například <xref:System.GC.Collect?displayProperty=nameWithType> přetížení metody provede úplné blokující kolekce. Souběžné uvolňování paměti probíhá na pozadí a nedochází k blokování aplikace.  
  
 `GetCurrentSurvived` Metoda odpovídá nespravované spravované <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRAppDomainResourceMonitor – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [Sledování prostředků domény aplikace](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
