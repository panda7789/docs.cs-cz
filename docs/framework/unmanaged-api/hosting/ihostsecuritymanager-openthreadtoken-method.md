---
title: "IHostSecurityManager::OpenThreadToken – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.OpenThreadToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d3b5ec31944b58bec6268de6e54503141880e6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken – metoda
Otevře se volitelného přístupový token, který je přidružený k aktuálně prováděné podprocesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwDesiredAccess`  
 [v] Maska hodnot přístupu, které určují požadovaný typy přístup k tokenu vlákna. Tyto hodnoty jsou definovány v Win32 `OpenThreadToken` funkce. Požadovaný přístup typy jsou souhlasí proti tokenu volitelného seznamu řízení přístupu (DACL) Chcete-li určit, jaké typy přístupu k udělit nebo odepřít.  
  
 `bOpenAsSelf`  
 [v] `true` k určení, že má být provedena kontrola přístupu v kontextu zabezpečení procesu pro volající vlákno; `false` k určení, by měl provede kontrolu přístupu v kontextu zabezpečení pro volající vlákno sám sebe. Pokud vlákno zosobňuje klienta, může být kontext zabezpečení, která procesu klienta.  
  
 `phThreadToken`  
 [out] Ukazatel na nově otevřené přístupový token.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostSecurityManager::OpenThreadToken`chová podobně jako odpovídající funkce Win32 se stejným názvem, s tím rozdílem, že funkce Win32 umožňuje předat libovolný vláken v popisovač volajícímu, při `IHostSecurityManager::OpenThreadToken` otevře pouze token přidružené volající vlákno.  
  
 `HANDLE` Typ není kompatibilní se standardem COM, který je jeho velikost je specifické pro operační systém a vyžaduje vlastní zařazování. Tento token je proto pro použití pouze v rámci procesu mezi modulu CLR a hostitelem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Ihostsecuritycontext – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [Ihostsecuritymanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
