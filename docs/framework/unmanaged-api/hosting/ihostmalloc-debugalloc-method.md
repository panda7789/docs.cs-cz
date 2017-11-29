---
title: "IHostMAlloc::DebugAlloc – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc.DebugAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 18759aa319bf39c49418e3b9388d96829ed52f7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmallocdebugalloc-method"></a>IHostMAlloc::DebugAlloc – metoda
Požadavky, přidělit zadaného množství paměti z haldy hostitel a dále sledovat, kdy byl přidělen paměť.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `cbSize`  
 [v] Velikost v bajtech aktuální požadavek na přidělení paměti.  
  
 `dwCriticalLevel`  
 [v] Jeden z [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) hodnoty, která určuje dopad došlo k chybě přidělení.  
  
 `pszFileName`  
 [v] K souboru kódu laděné spustitelného souboru.  
  
 `iLineNo`  
 [v] Číslo řádku v `pszFileName` kde obdržel požadavek přidělení.  
  
 `ppMem`  
 [out] Ukazatel na přidělené paměti, nebo hodnota null, pokud požadavek nebylo možné dokončit.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`DebugAlloc`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Nedostatek paměti nebylo k dispozici k dokončení požadavek na přidělení.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR získá ukazatele rozhraní k [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance voláním [ihostmemorymanager::createmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metoda. `DebugAlloc`umožňuje získat informace o souboru kódu pro použití během ladění modulu runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Ihostmemorymanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [Ihostmalloc – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
