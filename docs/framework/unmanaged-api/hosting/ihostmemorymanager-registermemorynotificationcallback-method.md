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
ms.openlocfilehash: 0c20df85560f715e829fe02be599788854fcb0f1
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804481"
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
 pro Ukazatel rozhraní na instanci [ICLRMemoryNotificationCallback –](iclrmemorynotificationcallback-interface.md) , která je implementována modulem CLR.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`RegisterMemoryNotificationCallback`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Vzhledem k tomu `ICLRMemoryNotificationCallback` , že rozhraní definuje pouze jednu metodu ([ICLRMemoryNotificationCallback –:: OnMemoryNotification –](iclrmemorynotificationcallback-onmemorynotification-method.md)) a protože `pCallback` je ukazatel na `ICLRMemoryNotificationCallback` instanci poskytovanou modulem CLR, je registrace pro samotnou funkci zpětného volání efektivní. Hostitel vyvolá `OnMemoryNotification` hlášení stavů paměti místo použití standardní `CreateMemoryResourceNotification` funkce Win32. Další informace najdete v dokumentaci k platformě Windows.  
  
> [!NOTE]
> Volání `OnMemoryNotification` nikdy neblokuje. Vždycky se vrátí hned.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRMemoryNotificationCallback – rozhraní](iclrmemorynotificationcallback-interface.md)
- [IHostMemoryManager – rozhraní](ihostmemorymanager-interface.md)
