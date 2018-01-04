---
title: "ICorRuntimeHost::CreateEvidence – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateEvidence
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 754b254fb9a41ab8bb900fdb5d0c10a126b804c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcreateevidence-method"></a>ICorRuntimeHost::CreateEvidence – metoda
Získá ukazatele rozhraní typu <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, což umožňuje na hostiteli a poté vytvořit důkaz zabezpečení mají být předány [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) nebo [createdomainex –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pEvidence`  
 [out] Ukazatel rozhraní <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance použitý k vytvoření důkaz zabezpečení. Tento ukazatel je zadán `IUnknown`, takže volající by měly volat obvykle `QueryInterface` na tomto rozhraní k získání ukazatele na <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Operace byla úspěšná.|  
|S_FALSE|Operaci se nepodařilo dokončit.|  
|E_FAIL|Došlo k neznámé, závažnou chybu. Pokud metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v procesu. Následující volání žádné hostování rozhraní API vrací HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí prázdnou kolekci, která nelze načíst z nativního kódu. Měli byste použít <xref:System.Security.Policy.Evidence> metoda místo.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Viz také  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
