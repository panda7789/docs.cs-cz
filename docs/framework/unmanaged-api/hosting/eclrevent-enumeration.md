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
ms.openlocfilehash: ee749fd40f440e92f1d1b09c2ea5e7bdd51f1cbe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131137"
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
|`Event_DomainUnload`|Určuje uvolnění konkrétní <xref:System.AppDomain>.|  
|`Event_MDAFired`|Určuje, že se vygenerovala zpráva pomocníka spravovaného ladění (MDA).|  
|`Event_StackOverflow`|Určuje, že došlo k chybě přetečení zásobníku.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel může zaregistrovat zpětná volání pro jakýkoli typ události popsanou `EClrEvent` voláním metod rozhraní [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) . Hostitel získá ukazatel na toto rozhraní voláním metody [ICLRControl:: GetCLRManager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .  
  
 Události `Event_CLRDisabled` a `Event_DomainUnload` lze vyvolat více než jednou a z různých vláken k signalizaci uvolnění nebo zakázání CLR.  
  
 Událost `Event_MDAFired` vyvolává vytvoření instance [MDAInfo –](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) , která obsahuje podrobnosti zprávy MDA. Další informace o MDA najdete v tématu [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IActionOnCLREvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
