---
title: ICLRAppDomainResourceMonitor::GetCurrentCpuTime – metoda
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
ms.openlocfilehash: b411190ff36410c1d293f1e48b31975be8a13aee
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616031"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a>ICLRAppDomainResourceMonitor::GetCurrentCpuTime – metoda
Získá celkový čas procesoru používaný všemi vlákny při spuštění v aktuální doméně aplikace, protože byla vytvořena doména aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwAppDomainId`  
 pro ID požadované aplikační domény  
  
 `pMilliseconds`  
 mimo Ukazatel na celkový čas procesoru, který byl použit všemi vlákny při spuštění v aktuální doméně aplikace od vytvoření domény aplikace. Tento parametr může být `null` .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|COR_E_APPDOMAINUNLOADED|Doména aplikace byla uvolněna nebo neexistuje.|  
|E_FAIL|Monitorování prostředků domény aplikace není povoleno.<br /><br /> -nebo-<br /><br /> Všechny ostatní chyby.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je nespravovaný ekvivalent spravované <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> Vlastnosti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRAppDomainResourceMonitor – rozhraní](iclrappdomainresourcemonitor-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
- [Monitorování prostředků domény aplikace](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [Hostování](index.md)
