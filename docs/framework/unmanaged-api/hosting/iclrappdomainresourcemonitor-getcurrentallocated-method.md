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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4011881e98c109458bf87efcc1b09463c064f23f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a>ICLRAppDomainResourceMonitor::GetCurrentAllocated – metoda
Získá celková velikost v bajtech přidělených paměti, které jste provedli pro doménu aplikace, protože byl vytvořen bez odečtením paměti, která byla uvolněna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwAppDomainId`  
 [v] ID domény požadovaná aplikace.  
  
 `pBytesAllocated`  
 [out] Ukazatel na celkovou velikost všech přidělení paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|COR_E_APPDOMAINUNLOADED|Doména aplikace byl odpojen nebo neexistuje.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je ekvivalentem nespravované spravované <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> vlastnost.  
  
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
