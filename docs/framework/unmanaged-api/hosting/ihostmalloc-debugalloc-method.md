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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 00fa0fb7c257500eb0bc24c6c43bd0dd265bc00b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481635"
---
# <a name="ihostmallocdebugalloc-method"></a>IHostMAlloc::DebugAlloc – metoda
Požadavky, že hostitel přidělit zadaného množství paměti z haldy a také sledovat, kde byla přidělena paměť.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Velikost v bajtech, aktuální požadavek na přidělení paměti.  
  
 `dwCriticalLevel`  
 [in] Jeden z [ememorycriticallevel –](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) hodnoty určující dopad selhání přidělení.  
  
 `pszFileName`  
 [in] Soubor kódu laděnému spustitelnému souboru.  
  
 `iLineNo`  
 [in] Číslo řádku v `pszFileName` kde byl vyžádán přidělení.  
  
 `ppMem`  
 [out] Ukazatel do přidělené paměti nebo hodnota null, pokud požadavek nešlo dokončit.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`DebugAlloc` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Nedostatek paměti nebyly k dispozici k dokončení požadavek na přidělení.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR načte ukazatel rozhraní k [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance voláním [ihostmemorymanager::createmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metoda. `DebugAlloc` umožňuje načíst informace o souboru kódu pro použití během ladění modulu runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [IHostMalloc – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
