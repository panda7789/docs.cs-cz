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
ms.openlocfilehash: 85c7308f794929d753b50f58f69168f67a31cb85
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803879"
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
 pro Maska přístupových hodnot, které určují požadované typy přístupu k tokenu vlákna. Tyto hodnoty jsou definovány ve funkci Win32 `OpenThreadToken` . Požadované typy přístupu jsou odsouhlaseny proti volitelnému seznamu řízení přístupu (DACL) tokenu, aby bylo možné určit, které typy přístupu udělit nebo odepřít.  
  
 `bOpenAsSelf`  
 [in] `true` Chcete-li určit, že by měla být provedena kontroly přístupu pomocí kontextu zabezpečení procesu pro volající vlákno; `false`Chcete-li určit, že by měla být provedena kontroly přístupu pomocí kontextu zabezpečení pro samotné volající vlákno. Pokud vlákno zosobňuje klienta, může být kontextem zabezpečení klientským procesem.  
  
 `phThreadToken`  
 mimo Ukazatel na nově otevřený přístupový token.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostSecurityManager::OpenThreadToken`se chová podobně jako odpovídající funkce Win32 se stejným názvem, s tím rozdílem, že funkce Win32 umožňuje volajícímu předat popisovač do libovolného vlákna, zatímco `IHostSecurityManager::OpenThreadToken` otevře pouze token přidružený k volajícímu vláknu.  
  
 `HANDLE`Typ není kompatibilní s modelem COM, to znamená, že jeho velikost je specifická pro operační systém a vyžaduje vlastní zařazování. Proto je tento token určen pouze pro použití v rámci procesu, mezi CLR a hostitelem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IHostSecurityContext – rozhraní](ihostsecuritycontext-interface.md)
- [IHostSecurityManager – rozhraní](ihostsecuritymanager-interface.md)
