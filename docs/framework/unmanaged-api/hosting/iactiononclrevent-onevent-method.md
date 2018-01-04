---
title: "IActionOnCLREvent::OnEvent – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IActionOnCLREvent.OnEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfba70cb1e0daf230abd16af6e24b4671334f20d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iactiononclreventonevent-method"></a>IActionOnCLREvent::OnEvent – metoda
Zpětná volání provádí události, které byly zaregistrovány pomocí volání [iclroneventmanager::registeractiononevent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `event`  
 [v] Jeden z [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) hodnoty, které určuje typ události.  
  
 `data`  
 [v] Ukazatel na objekt, který obsahuje podrobnosti o `event`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`OnEvent`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu. Následující volání žádné hostování metoda vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `data` Parametr je ukazatel na objekt neurčeného typu. Pokud `event` parametr `Event_DomainUnload`, `data` je číselný identifikátor <xref:System.AppDomain> , který byl odpojen. Hostitel moci provést vhodnou akci pomocí tento identifikátor jako klíč.  
  
 Pokud `event` je `Event_MDAFired`, `data` je ukazatel na [mdainfo –](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instanci, která obsahuje zprávy výstup z a spravované ladění Assistant (MDA). Mda jsou funkce modulu CLR, který pomoci vývojářům s laděním vygenerováním XML zprávy o událostech, které jsou jinak obtížné depeše. Takové zprávy může být obzvláště užitečný při ladění přechodů mezi spravovanými a nespravovanými kódu. Další informace najdete v tématu [diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [EClrEvent – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [IActionOnCLREvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [ICLROnEventManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [MDAInfo – struktura](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
