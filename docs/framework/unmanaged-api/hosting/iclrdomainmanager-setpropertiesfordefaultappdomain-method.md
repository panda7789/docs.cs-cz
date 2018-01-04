---
title: "ICLRDomainManager::SetPropertiesForDefaultAppDomain – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de72568f5908dc89c9a4105c927cfba6c7366b80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a>ICLRDomainManager::SetPropertiesForDefaultAppDomain – metoda
Nastaví vlastnosti, které se použijí k chybě při inicializaci výchozí doméně aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nProperties`  
 [v] Počet položek v `pwszPropertyNames` a `pwszPropertyValues`.  
  
 `pwszPropertyNames`  
 [v] Pole názvy vlastností, nebo hodnota null, pokud nejsou k dispozici žádné vlastnosti. Název pouze vlastnosti, která je rozpoznáno tato metoda je v současné době "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".  
  
 `pwszPropertyValues`  
 [v] Pole hodnot vlastností, nebo hodnota null, pokud nejsou k dispozici žádné vlastnosti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)|`pwszPropertyNames`obsahuje název vlastnosti, která nebyla rozpoznána touto metodou.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti pro "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" je seznam sestavení, které mají podmíněného <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA) s <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> příznak, který má být provedeno viditelné pro částečně důvěryhodné volající výchozí aplikace domény.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [ICLRDomainManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
