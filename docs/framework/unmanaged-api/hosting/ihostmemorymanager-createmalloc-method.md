---
title: "IHostMemoryManager::CreateMAlloc – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.CreateMAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::CreateMAlloc
helpviewer_keywords:
- CreateAlloc method [.NET Framework hosting]
- IHostMemoryManager::CreateMAlloc method [.NET Framework hosting]
ms.assetid: 9ee6e052-bef7-4350-9e4f-edfffd99ad6f
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 19b43ccf7cb2429c28c052ab8ab3a009ec4a30a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagercreatemalloc-method"></a>IHostMemoryManager::CreateMAlloc – metoda
Získá ukazatele rozhraní k [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instanci, která se používá k zajištění požadavků na přidělení z haldy vytvořené hostitele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwMallocType`  
 [v] Kombinace [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) příznaky, které určuje charakteristiky paměti, které je právě přiděleno.  
  
 `ppMAlloc`  
 [out] Ukazatel na adresu `IHostMAlloc` instance od hostitele.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`CreateMAlloc`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Není dostatek fyzické paměti nebylo k dispozici k dokončení požadavek na přidělení.|  
  
## <a name="remarks"></a>Poznámky  
 `CreateMAlloc`Vrátí objekt, který umožňuje provádět požadavky na přidělení prostřednictvím hostitele místo použití standardní Win32 funkce modulu CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IHostMalloc – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
