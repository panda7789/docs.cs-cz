---
title: IHostMAlloc::DebugAlloc – metoda
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
ms.openlocfilehash: 20ad5485b8603cc7de1c27c00d53c8939871d525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178028"
---
# <a name="ihostmallocdebugalloc-method"></a>IHostMAlloc::DebugAlloc – metoda
Požaduje, aby hostitel přidělit zadané množství paměti z haldy a navíc sledovat, kde byla přidělena paměť.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cbSize`  
 [v] Velikost aktuálního požadavku na přidělení paměti v bajtech.  
  
 `dwCriticalLevel`  
 [v] Jedna z hodnot [EMemoryCriticalLevel,](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) označující dopad selhání přidělení.  
  
 `pszFileName`  
 [v] Soubor kódu odladěného spustitelného souboru.  
  
 `iLineNo`  
 [v] Číslo řádku, `pszFileName` ve kterém byla požadována alokace.  
  
 `ppMem`  
 [out] Ukazatel na přidělenou paměť nebo hodnotu null, pokud požadavek nelze dokončit.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`DebugAlloc`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|CLR nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Časový čas hovoru byl vypován.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.|  
|E_fail|Došlo k neznámému katastrofickému selhání. Když metoda vrátí E_FAIL CLR již není použitelný v rámci procesu. Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|K dokončení požadavku na přidělení nebylo k dispozici dostatek paměti.|  
  
## <a name="remarks"></a>Poznámky  
 CLR získá ukazatel rozhraní na instanci [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) voláním metody [IHostMemoryManager::CreateMalloc.](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) `DebugAlloc`umožňuje runtime získat informace o souboru kódu pro použití při ladění.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [IHostMalloc – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
