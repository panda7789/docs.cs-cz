---
title: IHostAutoEvent::Wait – metoda
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Wait
helpviewer_keywords:
- Wait method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Wait method [.NET Framework hosting]
ms.assetid: 535d51c5-9112-401b-8c36-85f35d7ee609
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7921f0361d7369cddf14dd1ab477529d1bbac481
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ihostautoeventwait-method"></a>IHostAutoEvent::Wait – metoda
Způsobí, že aktuální [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance počkat, dokud je vlastněná nebo zadaného množství času po uplynutí předem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwMilliseconds`  
 [v] Počet milisekund, po aktuální `IHostAutoEvent` instance čekat před vrácením, pokud žádný přístup z více vláken nebo fiber trvá vlastnictví.  
  
 `option`  
 [v] Jeden z [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty, zadání akce hostitele provést v případě, že tato operace bloky.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`Wait` úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_DEADLOCK|Hostitel zjistil vzájemné zablokování během intervalu čekání a zvolili události, které aktuální `IHostAutoEvent` instance jako oběť vzájemného zablokování.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostAutoEvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [IHostManualEvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
