---
title: ICLRMemoryNotificationCallback::OnMemoryNotification – metoda
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
ms.openlocfilehash: 11b9b500e16917498856888c437c58c0df2edafb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140985"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a>ICLRMemoryNotificationCallback::OnMemoryNotification – metoda
Upozorňuje modul CLR (Common Language Runtime) na zatížení paměti v počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `eMemoryAvailable`  
 pro Jedna z hodnot [EMemoryAvailable –](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) , která označuje tlak na paměť, na kterém je počítač v současné době.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`OnMemoryNotification` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR zaregistruje zpětné volání do `OnMemoryNotification` pomocí volání metody [IHostMemoryManager:: RegisterMemoryNotificationCallback –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) . Modul runtime používá informace vrácené ve zpětném volání k uvolnění další paměti, pokud hostitel hlásí, že paměťové prostředky mají nízký provoz.  
  
> [!NOTE]
> Volání `OnMemoryNotification` nikdy neblokují. Vždycky se vrátí hned.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [RegisterMemoryNotificationCallback – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)
- [ICLRMemoryNotificationCallback – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
