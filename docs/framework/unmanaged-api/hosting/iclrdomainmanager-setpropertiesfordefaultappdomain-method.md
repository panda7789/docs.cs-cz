---
title: ICLRDomainManager::SetPropertiesForDefaultAppDomain – metoda
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
ms.openlocfilehash: 37919be2d0ebd7d243615bc5845b0781ac13e574
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129315"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a>ICLRDomainManager::SetPropertiesForDefaultAppDomain – metoda
Nastaví vlastnosti, které se použijí k inicializaci výchozí domény aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nProperties`  
 pro Počet položek v `pwszPropertyNames` a `pwszPropertyValues`.  
  
 `pwszPropertyNames`  
 pro Pole názvů vlastností nebo hodnotu null, pokud nejsou k dispozici žádné vlastnosti. V současné době je jediným názvem vlastnosti, který je rozpoznáván touto metodou, "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".  
  
 `pwszPropertyValues`  
 pro Pole hodnot vlastnosti nebo hodnotu null, pokud nejsou k dispozici žádné vlastnosti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)|`pwszPropertyNames` obsahuje název vlastnosti, který tato metoda nerozpoznala.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" je seznam sestavení, která mají atribut podmíněného <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) s příznakem <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType>, který má být viditelný pro částečně důvěryhodné volající ve výchozí doméně aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
