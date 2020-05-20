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
ms.openlocfilehash: a73c0731c79dea3a0c411fe27a864ec9ac4e20b2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616018"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a>ICLRAppDomainResourceMonitor::GetCurrentSurvived – metoda
Vrátí počet bajtů, které byly zachovány při posledním plném, blokování uvolnění paměti a odkazují aktuální doménu aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwAppDomainId`  
 pro ID požadované aplikační domény  
  
 `pAppDomainBytesSurvived`  
 mimo Ukazatel na počet bajtů, které byly zachovány po posledním uvolňování paměti, které jsou uloženy touto doménou aplikace. Po úplné kolekci je toto číslo přesné a úplné. Po dočasné kolekci je toto číslo potenciálně neúplné. Tento parametr může být `null` .  
  
 `pRuntimeBytesSurvived`  
 mimo Ukazatel na celkový počet bajtů, které byly zachovány z posledního uvolňování paměti. Po úplné kolekci představuje toto číslo počet bajtů, které jsou uloženy ve spravovaných haldách. Po dočasné kolekci představuje toto číslo počet bajtů, které jsou v dočasných generacích uloženy v reálném čase. Tento parametr může být `null` .  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|COR_E_APPDOMAINUNLOADED|Doména aplikace byla uvolněna nebo neexistuje.|  
  
## <a name="remarks"></a>Poznámky  
 Statistika se aktualizuje až po úplném a blokujícím uvolňování paměti. To znamená, že kolekce obsahující všechny generace a zastavuje aplikaci, když dojde ke shromažďování. Například <xref:System.GC.Collect?displayProperty=nameWithType> přetížení metody provádí úplnou, blokující kolekci. Souběžné uvolňování paměti probíhá na pozadí a neblokuje aplikaci.  
  
 `GetCurrentSurvived`Metoda je nespravovaný ekvivalent spravované <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> Vlastnosti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRAppDomainResourceMonitor – rozhraní](iclrappdomainresourcemonitor-interface.md)
- [Monitorování prostředků domény aplikace](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
- [Hostování](index.md)
