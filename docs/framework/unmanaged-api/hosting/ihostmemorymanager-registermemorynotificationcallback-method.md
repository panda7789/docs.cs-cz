---
title: IHostMemoryManager::RegisterMemoryNotificationCallback – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
ms.openlocfilehash: 4400fab27ed82e540230ce4196844285e8e37d16
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128638"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a>IHostMemoryManager::RegisterMemoryNotificationCallback – metoda
Registruje ukazatel na funkci zpětného volání, kterou hostitel vyvolá, aby upozornil na modul CLR (Common Language Runtime) aktuálního zatížení paměti v počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCallback`  
 pro Ukazatel rozhraní na instanci [ICLRMemoryNotificationCallback –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) , která je implementována modulem CLR.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`RegisterMemoryNotificationCallback` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Vzhledem k tomu, že rozhraní `ICLRMemoryNotificationCallback` definuje pouze jednu metodu ([ICLRMemoryNotificationCallback –:: OnMemoryNotification –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)) a protože `pCallback` je ukazatel na instanci `ICLRMemoryNotificationCallback` POSKYTNUTou modulem CLR, registrace je pro zpětné volání efektivně. funkce. Hostitel vyvolá `OnMemoryNotification` pro hlášení stavů paměti, místo použití standardní funkce Win32 `CreateMemoryResourceNotification`. Další informace najdete v dokumentaci k platformě Windows.  
  
> [!NOTE]
> Volání `OnMemoryNotification` nikdy neblokují. Vždycky se vrátí hned.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRMemoryNotificationCallback – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
