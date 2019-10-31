---
title: ICorRuntimeHost::CreateEvidence – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
ms.openlocfilehash: 429ce0510162b3256cdf58f4820b04dd80243e29
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139631"
---
# <a name="icorruntimehostcreateevidence-method"></a>ICorRuntimeHost::CreateEvidence – metoda
Získá ukazatel rozhraní typu <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, který umožňuje hostiteli vytvořit legitimaci zabezpečení, která bude předána metodě [CreateDomain –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) nebo [CreateDomainEx –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pEvidence`  
 mimo Ukazatel rozhraní na instanci <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, která se používá k vytvoření legitimace zabezpečení. Tento ukazatel je typu `IUnknown`, takže volající by obvykle měli volat `QueryInterface` na tomto rozhraní, aby získal ukazatel na <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Operace byla úspěšná.|  
|S_FALSE|Operaci se nepodařilo dokončit.|  
|E_FAIL|Došlo k neznámému a závažnému selhání. Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit. Následná volání všech hostitelských rozhraní API vrátí HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrací prázdnou kolekci, kterou nelze naplnit z nativního kódu. Místo toho byste měli použít metodu <xref:System.Security.Policy.Evidence>.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** 1,0, 1,1  
  
## <a name="see-also"></a>Viz také:

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
