---
title: IActionOnCLREvent::OnEvent – metoda
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
ms.openlocfilehash: 98807717fc913052dae15f9f3cbd462d4f537ad4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126916"
---
# <a name="iactiononclreventonevent-method"></a>IActionOnCLREvent::OnEvent – metoda
Provádí zpětná volání pro události, které byly zaregistrovány pomocí volání metody [ICLROnEventManager:: RegisterActionOnEvent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `event`  
 pro Jedna z hodnot [EClrEvent –](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) , která označuje typ události.  
  
 `data`  
 pro Ukazatel na objekt, který obsahuje podrobnosti o `event`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`OnEvent` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vláknu.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání libovolné metody hostování vrátí HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Parametr `data` je ukazatel na objekt neurčeného typu. Pokud je parametr `event` `Event_DomainUnload`, `data` číselným identifikátorem <xref:System.AppDomain>, který byl uvolněn. Hostitel může provést odpovídající akci s použitím tohoto identifikátoru jako klíče.  
  
 Pokud je `event` `Event_MDAFired`, `data` je ukazatel na instanci [MDAInfo –](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) , která obsahuje výstup zprávy z pomocníka spravovaného ladění (MDA). MDA jsou funkcí CLR, které vývojářům umožňují ladit, generováním zpráv XML o událostech, které jsou jinak obtížné zachytit. Tyto zprávy mohou být obzvláště užitečné při ladění přechodů mezi spravovaným a nespravovaným kódem. Další informace najdete v tématu [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [EClrEvent – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [IActionOnCLREvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLROnEventManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [MDAInfo – struktura](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
