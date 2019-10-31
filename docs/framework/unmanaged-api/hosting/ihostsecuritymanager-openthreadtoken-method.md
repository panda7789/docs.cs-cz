---
title: IHostSecurityManager::OpenThreadToken – metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
ms.openlocfilehash: 2ced153798355aff882f0244f3dd946c39dea2bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121473"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken – metoda
Otevře volitelný přístupový token přidružený k aktuálně spuštěnému vláknu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwDesiredAccess`  
 pro Maska přístupových hodnot, které určují požadované typy přístupu k tokenu vlákna. Tyto hodnoty jsou definovány ve funkci Win32 `OpenThreadToken`. Požadované typy přístupu jsou odsouhlaseny proti volitelnému seznamu řízení přístupu (DACL) tokenu, aby bylo možné určit, které typy přístupu udělit nebo odepřít.  
  
 `bOpenAsSelf`  
 [in] `true` pro určení, že by měla být provedena kontroly přístupu pomocí kontextu zabezpečení procesu pro volající vlákno; `false` pro určení, že by měla být provedena kontroly přístupu pomocí kontextu zabezpečení pro samotné volající vlákno. Pokud vlákno zosobňuje klienta, může být kontextem zabezpečení klientským procesem.  
  
 `phThreadToken`  
 mimo Ukazatel na nově otevřený přístupový token.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostSecurityManager::OpenThreadToken` se chová podobně jako odpovídající funkce Win32 stejného názvu, s tím rozdílem, že funkce Win32 umožňuje volajícímu předat popisovač do libovolného vlákna, zatímco `IHostSecurityManager::OpenThreadToken` otevírá pouze token přidružený k volajícímu vláknu.  
  
 Typ `HANDLE` není kompatibilní s modelem COM, to znamená, že jeho velikost je specifická pro operační systém a vyžaduje vlastní zařazování. Proto je tento token určen pouze pro použití v rámci procesu, mezi CLR a hostitelem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostSecurityContext – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
