---
title: ICorRuntimeHost::CreateDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
ms.openlocfilehash: 7c3e37fdb8a5afc973c913b1cfa56ab2e9f4fa52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127733"
---
# <a name="icorruntimehostcreatedomain-method"></a>ICorRuntimeHost::CreateDomain – metoda
Vytvoří doménu aplikace. Volající obdrží ukazatel rozhraní typu <xref:System._AppDomain> do instance typu <xref:System.AppDomain?displayProperty=nameWithType>.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzFriendlyName`  
 pro Volitelný parametr, který slouží k poskytnutí popisného názvu doméně. Tento popisný název lze zobrazit v uživatelských rozhraních, jako jsou například ladicí programy, a identifikovat doménu.  
  
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
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** 1,0, 1,1  
  
## <a name="see-also"></a>Viz také:

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
