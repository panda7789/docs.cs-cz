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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c933389e1398d294d79f82a69a609a77aa820f3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779823"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a>ICLRMemoryNotificationCallback::OnMemoryNotification – metoda
Zatížení paměti v počítači upozorní common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `eMemoryAvailable`  
 [in] Jeden z [ememoryavailable –](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) hodnoty, která přetížení paměti v počítači je právě se registruje.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`OnMemoryNotification` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Zaregistruje zpětné volání, aby modul CLR `OnMemoryNotification` pomocí volání [ihostmemorymanager::registermemorynotificationcallback –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) metoda. Modul runtime používá informace vrácené při zpětném volání další paměť uvolnit, když hostitele hlásí, že prostředky jsou spuštěné nízké paměti.  
  
> [!NOTE]
>  Volání `OnMemoryNotification` není nikdy blokována. Vždy vrátí okamžitě.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [RegisterMemoryNotificationCallback – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)
- [ICLRMemoryNotificationCallback – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
