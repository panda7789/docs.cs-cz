---
title: ICLROnEventManager::UnregisterActionOnEvent – metoda
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.UnregisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type:
- apiref
ms.openlocfilehash: 0f952978a2591c82b2ad3f5059070124b7873c94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140822"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a>ICLROnEventManager::UnregisterActionOnEvent – metoda
Zruší registraci dříve registrovaného ukazatele zpětného volání pro zadanou událost.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `event`  
 pro Jedna z hodnot [EClrEvent –](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) , která označuje událost, pro kterou má být odregistrován ukazatel zpětného volání popsaný `pAction`.  
  
 `pAction`  
 pro Ukazatel na objekt [IActionOnCLREvent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) , který byl předán jako parametr metodě [RegisterActionOnEvent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`UnregisterActionOnEvent` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EClrEvent – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [IActionOnCLREvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLROnEventManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
