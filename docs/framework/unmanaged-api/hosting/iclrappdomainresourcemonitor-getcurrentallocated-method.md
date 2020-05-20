---
title: ICLRAppDomainResourceMonitor::GetCurrentAllocated – metoda
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type:
- apiref
ms.openlocfilehash: 685d303b31b8f8c20cbbdb8aec6fc127650aa32a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616044"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a>ICLRAppDomainResourceMonitor::GetCurrentAllocated – metoda
Získá celkovou velikost přidělení paměti (v bajtech), která byla vytvořena aplikační doménou od jejího vytvoření, bez odčítání paměti, která byla uvolněna do paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwAppDomainId`  
 pro ID požadované aplikační domény  
  
 `pBytesAllocated`  
 mimo Ukazatel na celkovou velikost všech přidělení paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|COR_E_APPDOMAINUNLOADED|Doména aplikace byla uvolněna nebo neexistuje.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je nespravovaný ekvivalent spravované <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> Vlastnosti.  
  
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
