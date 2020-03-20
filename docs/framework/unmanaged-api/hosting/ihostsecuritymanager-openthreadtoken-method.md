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
ms.openlocfilehash: 11d042ea9eecc8d428761da6eaa15f7c2907ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176263"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken – metoda
Otevře diskreční přístupový token přidružený k aktuálně spuštěnépodprocesu.  
  
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
 [v] Maska přístupových hodnot, které určují požadované typy přístupu k tokenu vlákna. Tyto hodnoty jsou definovány `OpenThreadToken` ve funkci Win32. Požadované typy přístupu jsou odsouhlaseny proti seznamu volitelného řízení přístupu tokenu (DACL) k určení, které typy přístupu k udělení nebo zamítnutí.  
  
 `bOpenAsSelf`  
 [v] `true` upřesnit, že kontrola přístupu by měla být provedena pomocí kontextu zabezpečení procesu pro volající vlákno; `false` určit, že kontrola přístupu by měla být provedena pomocí kontextu zabezpečení pro volající vlákno samotné. Pokud vlákno je zosobnění klienta, kontext zabezpečení může být, že klientského procesu.  
  
 `phThreadToken`  
 [out] Ukazatel na nově otevřený přístupový token.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Běžný jazyk runtime (CLR) nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Časový čas hovoru byl vypován.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.|  
|E_fail|Došlo k neznámému katastrofickému selhání. Když metoda vrátí E_FAIL CLR již není použitelný v rámci procesu. Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostSecurityManager::OpenThreadToken`chová podobně jako odpovídající Win32 funkce se stejným názvem, s tím rozdílem, že Win32 funkce umožňuje `IHostSecurityManager::OpenThreadToken` volajícímu předat popisovač libovolné vlákno, zatímco otevře pouze token přidružený k volající vlákno.  
  
 Typ `HANDLE` není kompatibilní s com, to znamená, že jeho velikost je specifická pro operační systém a vyžaduje vlastní zařazování. Proto tento token je určen pro použití pouze v rámci procesu, mezi CLR a hostitele.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IHostSecurityContext – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
