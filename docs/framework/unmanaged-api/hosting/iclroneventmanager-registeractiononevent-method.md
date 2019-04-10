---
title: ICLROnEventManager::RegisterActionOnEvent – metoda
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.RegisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::RegisterActionOnEvent
helpviewer_keywords:
- ICLROnEventManager::RegisterActionOnEvent method [.NET Framework hosting]
- RegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: b944cf49-918d-4c4e-993b-77d097a52550
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68a8493a9eb5177844e81ef7a9612f979ffe89c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216493"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a>ICLROnEventManager::RegisterActionOnEvent – metoda
Zaregistruje zpětné volání ukazatel zadané události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `event`  
 [in] Jeden z [eclrevent –](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) hodnoty určující událost, pro kterou se má registrovat zpětné volání ukazatel popsal `pAction`.  
  
 `pAction`  
 [in] Ukazatel [iactiononclrevent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) objektu, která je volána, když se aktivuje registrované události.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`RegisterActionOnEvent` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel může registrace zpětných volání pro jednu nebo obě dvě události typy popsal `EClrEvent`. Získá hostitele `ICLROnEventManager` rozhraní voláním [iclrcontrol::getclrmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody.  
  
> [!NOTE]
>  Události, která `RegisterActionOnEvent` registrů můžete vyvoláno více než jednou a z různých vláken, který signalizuje, že uvolnění z paměti nebo vypnutí CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EClrEvent – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [IActionOnCLREvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLROnEventManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
