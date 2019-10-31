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
ms.openlocfilehash: a3a2d1827774ddedc00eb849f64256e3f425b3fa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127715"
---
# <a name="icorruntimehostcreatedomainex-method"></a>ICorRuntimeHost::CreateDomainEx – metoda
Vytvoří doménu aplikace. Volající obdrží ukazatel rozhraní typu <xref:System._AppDomain>do instance typu <xref:System.AppDomain?displayProperty=nameWithType>. Tato metoda umožňuje volajícímu předat instanci IAppDomainSetup – ke konfiguraci dalších funkcí vrácené instance <xref:System._AppDomain>.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzFriendlyName`  
 pro Volitelný parametr, který slouží k poskytnutí popisného názvu doméně. Tento popisný název lze zobrazit v uživatelských rozhraních, jako jsou například ladicí programy, a identifikovat doménu.  
  
 `pSetup`  
 pro Volitelný ukazatel rozhraní typu `IAppDomainSetup`, získaný voláním metody [ICorRuntimeHost:: createdomainsetup –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) .  
  
 `pIdentityArray`  
 pro Volitelné pole ukazatelů `IIdentity` instancí, které reprezentují legitimace namapované prostřednictvím zásad zabezpečení pro vytvoření sady oprávnění. Objekt `IIdentity` lze získat voláním metody [createevidence –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) .  
  
 `pAppDomain`  
 mimo Ukazatel rozhraní typu <xref:System._AppDomain> k instanci <xref:System.AppDomain?displayProperty=nameWithType>, kterou lze použít k další kontrole domény.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Operace byla úspěšná.|  
|S_FALSE|Operaci se nepodařilo dokončit.|  
|E_FAIL|Došlo k neznámému a závažnému selhání. Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit. Následná volání všech hostitelských rozhraní API vrátí HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
  
## <a name="remarks"></a>Poznámky  
 `CreateDomainEx` rozšiřuje možnosti [CreateDomain –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) tím, že volajícímu předává instanci `IAppDomainSetup` s hodnotami vlastností pro konfiguraci domény aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** 1,0, 1,1  
  
## <a name="see-also"></a>Viz také:

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [CreateDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)
- [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
