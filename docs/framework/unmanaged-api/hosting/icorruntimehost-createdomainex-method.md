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
ms.openlocfilehash: 5ed45c3975c58331490f89d8ca705f080d01d74e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466801"
---
# <a name="icorruntimehostcreatedomainex-method"></a>ICorRuntimeHost::CreateDomainEx – metoda
Vytvoří doménu aplikace. Volající přijímá ukazatel rozhraní, typu <xref:System._AppDomain>, do instance typu <xref:System.AppDomain?displayProperty=nameWithType>. Tato metoda umožňuje volajícímu předejte instanci iappdomainsetup – ke konfiguraci dalších funkcí vráceného <xref:System._AppDomain> instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzFriendlyName`  
 [in] Volitelný parametr, který slouží k pojmenování k doméně popisným názvem. Tento popisný název lze zobrazit v uživatelských rozhraních, jako je například ladicí programy k identifikaci domény.  
  
 `pSetup`  
 [in] Ukazatel volitelné rozhraní typu `IAppDomainSetup`, získaný voláním [icorruntimehost::createdomainsetup –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) metody.  
  
 `pIdentityArray`  
 [in] Volitelné pole ukazatelů na `IIdentity` instancí, které představují důkazy mapovaný prostřednictvím zásad zabezpečení sadu oprávnění. `IIdentity` Objektu lze získat voláním [createevidence –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) metody.  
  
 `pAppDomain`  
 [out] Ukazatel rozhraní typu <xref:System._AppDomain> do instance <xref:System.AppDomain?displayProperty=nameWithType> , který slouží k podrobnějšímu řízení domény.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Operace byla úspěšná.|  
|S_FALSE|Operaci se nepodařilo dokončit.|  
|E_FAIL|Došlo k neznámé, katastrofických selhání. Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu. Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
  
## <a name="remarks"></a>Poznámky  
 `CreateDomainEx` rozšiřuje možnosti [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) tím, že volající a zajistěte tak předání `IAppDomainSetup` instance s hodnotami vlastností konfigurace domény aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Viz také:
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [CreateDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)
- [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
