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
ms.openlocfilehash: 264f16fc9e767584229376e67f5aee6db1069025
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501609"
---
# <a name="icorruntimehostcreateevidence-method"></a>ICorRuntimeHost::CreateEvidence – metoda
Načte ukazatel rozhraní typu <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> , který umožňuje hostiteli vytvořit legitimaci zabezpečení, která bude předána metodě [CreateDomain –](icorruntimehost-createdomain-method.md) nebo [CreateDomainEx –](icorruntimehost-createdomainex-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pEvidence`  
 mimo Ukazatel rozhraní, který <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> slouží k vytvoření legitimace zabezpečení. Tento ukazatel je typu `IUnknown` , takže volající by obvykle volali `QueryInterface` na toto rozhraní, aby získal ukazatel na <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Operace byla úspěšná.|  
|S_FALSE|Operaci se nepodařilo dokončit.|  
|E_FAIL|Došlo k neznámému a závažnému selhání. Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit. Následná volání všech hostitelských rozhraní API vrací HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrací prázdnou kolekci, kterou nelze naplnit z nativního kódu. Místo toho byste měli použít <xref:System.Security.Policy.Evidence> metodu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** 1,0, 1,1  
  
## <a name="see-also"></a>Viz také:

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost – rozhraní](icorruntimehost-interface.md)
