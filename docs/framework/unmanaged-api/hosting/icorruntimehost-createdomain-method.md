---
title: "ICorRuntimeHost::CreateDomain – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0da99f05b09d44338a5f4d695fb2a4114f0e1f30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcreatedomain-method"></a>ICorRuntimeHost::CreateDomain – metoda
Vytvoří doménu aplikace. Volající obdrží ukazatele rozhraní typu <xref:System._AppDomain> na instanci typu <xref:System.AppDomain?displayProperty=nameWithType>.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzFriendlyName`  
 [v] Volitelný parametr dávat popisný název domény. Tento popisný název zobrazený ve uživatelského rozhraní, jako je například ladicí programy k identifikaci domény.  
  
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
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Viz také  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [Icorruntimehost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
