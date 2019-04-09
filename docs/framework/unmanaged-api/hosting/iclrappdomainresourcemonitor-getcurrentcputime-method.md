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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8022428c7f803f96e2fa150588edf95542bf19b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169855"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a>ICLRAppDomainResourceMonitor::GetCurrentCpuTime – metoda
Získá celkový procesorový čas, který byl použit pro všemi vlákny při provádění v aktuální doméně aplikace, od vytvoření domény aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwAppDomainId`  
 [in] ID domény požadované aplikace.  
  
 `pMilliseconds`  
 [out] Ukazatel na celkový procesorový čas, který byl použit všemi vlákny při provádění v aktuální doméně aplikace, od vytvoření domény aplikace. Tento parametr může být `null`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|COR_E_APPDOMAINUNLOADED|Aplikační domény byl odpojen nebo neexistuje.|  
|E_FAIL|Sledování prostředků domény aplikace není povoleno.<br /><br /> -nebo-<br /><br /> Všechny ostatní chyby.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda odpovídá nespravované spravované <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRAppDomainResourceMonitor – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [Rozhraní hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Sledování prostředků domény aplikace](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
