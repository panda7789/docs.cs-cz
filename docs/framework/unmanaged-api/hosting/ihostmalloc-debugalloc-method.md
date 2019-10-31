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
ms.openlocfilehash: a2a752f23ed64795f9208b9101c21bc585d5f431
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136819"
---
# <a name="ihostmallocdebugalloc-method"></a>IHostMAlloc::DebugAlloc – metoda
Požaduje, aby hostitel přidělil určenou velikost paměti z haldy a dále sledoval, kde byla paměť přidělena.  
  
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
 pro Velikost aktuální žádosti o přidělení paměti (v bajtech).  
  
 `dwCriticalLevel`  
 pro Jedna z hodnot [EMemoryCriticalLevel –](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) , která indikuje dopad selhání přidělení.  
  
 `pszFileName`  
 pro Soubor kódu spustitelného souboru, který se má ladit.  
  
 `iLineNo`  
 pro Číslo řádku v `pszFileName`, kde bylo přidělení požadováno.  
  
 `ppMem`  
 mimo Ukazatel na přidělenou paměť nebo hodnotu null, pokud požadavek nebylo možné dokončit.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`DebugAlloc` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|K dokončení žádosti o přidělení není k dispozici dostatek paměti.|  
  
## <a name="remarks"></a>Poznámky  
 CLR získá ukazatel rozhraní na instanci [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) voláním metody [IHostMemoryManager:: CreateMalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) . `DebugAlloc` umožňuje modulu runtime získat informace o souboru kódu pro použití během ladění.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [IHostMalloc – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
