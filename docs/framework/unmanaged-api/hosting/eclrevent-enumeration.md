---
title: EClrEvent – výčet
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
ms.openlocfilehash: 388f0de26983f8bb876f40a527f60d8bc59191a3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616343"
---
# <a name="eclrevent-enumeration"></a>EClrEvent – výčet
Popisuje události modulu CLR (Common Language Runtime), pro které může hostitel registrovat zpětná volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`Event_ClrDisabled`|Určuje závažnou chybu modulu CLR.|  
|`Event_DomainUnload`|Určuje odložení konkrétního <xref:System.AppDomain> .|  
|`Event_MDAFired`|Určuje, že se vygenerovala zpráva pomocníka spravovaného ladění (MDA).|  
|`Event_StackOverflow`|Určuje, že došlo k chybě přetečení zásobníku.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel může registrovat zpětná volání pro jakýkoli typ události, který je popsán `EClrEvent` voláním metod rozhraní [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) . Hostitel získá ukazatel na toto rozhraní voláním metody [ICLRControl:: GetCLRManager –](iclrcontrol-getclrmanager-method.md) .  
  
 `Event_CLRDisabled`Události a `Event_DomainUnload` mohou být vyvolány více než jednou a z různých vláken k signalizaci uvolnění nebo zakázání CLR.  
  
 `Event_MDAFired`Událost vyvolává vytvoření instance [MDAInfo –](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) , která obsahuje podrobnosti zprávy MDA. Další informace o MDA najdete v tématu [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IActionOnCLREvent – rozhraní](iactiononclrevent-interface.md)
- [ICLRControl – rozhraní](iclrcontrol-interface.md)
- [Výčty hostování](hosting-enumerations.md)
