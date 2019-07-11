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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3b17ca32051cd5fc0673ef26124b855a66f9785
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779980"
---
# <a name="icorruntimehostcreateevidence-method"></a>ICorRuntimeHost::CreateEvidence – metoda
Získá ukazatel rozhraní typu <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, který umožňuje hostiteli vytvořit legitimace zabezpečení k předání do [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) nebo [createdomainex –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pEvidence`  
 [out] Ukazatel rozhraní <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance použitý k vytvoření legitimace zabezpečení. Je zadán ukazatel this `IUnknown`, aby volající by měl obvykle zavolat `QueryInterface` na tomto rozhraní pro získání ukazatele na <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Operace byla úspěšná.|  
|S_FALSE|Operaci se nepodařilo dokončit.|  
|E_FAIL|Došlo k neznámé, katastrofických selhání. Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu. Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí prázdnou kolekci, která nelze naplnit z nativního kódu. Měli byste použít <xref:System.Security.Policy.Evidence> metoda místo.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Viz také:

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
