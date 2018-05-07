---
title: ICorRuntimeHost::CreateDomainEx – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e851cf16e4b23b1f8510c4d96b23c01eb726a77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorruntimehostcreatedomainex-method"></a>ICorRuntimeHost::CreateDomainEx – metoda
Vytvoří doménu aplikace. Volající obdrží ukazatele rozhraní, typu <xref:System._AppDomain>, do instance typu <xref:System.AppDomain?displayProperty=nameWithType>. Tato metoda umožňuje volajícímu předat instanci iappdomainsetup – Chcete-li konfigurovat další funkce vrácený <xref:System._AppDomain> instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzFriendlyName`  
 [v] Volitelný parametr dávat popisný název domény. Tento popisný název zobrazený ve uživatelského rozhraní, jako je například ladicí programy k identifikaci domény.  
  
 `pSetup`  
 [v] Ukazatele volitelné rozhraní typu `IAppDomainSetup`, získaných voláním [icorruntimehost::createdomainsetup –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) metoda.  
  
 `pIdentityArray`  
 [v] Volitelné pole ukazatele na `IIdentity` instancí, které představují důkaz namapovat prostřednictvím zásad zabezpečení pro vytvoření sady oprávnění. `IIdentity` Objektu je možné získat volání [createevidence –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) metoda.  
  
 `pAppDomain`  
 [out] Ukazatele rozhraní typu <xref:System._AppDomain> na instanci <xref:System.AppDomain?displayProperty=nameWithType> který lze použít k podrobnějšímu řízení domény.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Operace byla úspěšná.|  
|S_FALSE|Operaci se nepodařilo dokončit.|  
|E_FAIL|Došlo k neznámé, závažnou chybu. Pokud metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v procesu. Následující volání žádné hostování rozhraní API vrací HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
  
## <a name="remarks"></a>Poznámky  
 `CreateDomainEx` rozšiřuje možnosti [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) tím, že volající předávat `IAppDomainSetup` instance s hodnoty vlastností pro konfigurace domény aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Viz také  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [CreateDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)  
 [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
