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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63d79b0c1fed0178f8463174fe981f250d6f6fb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430704"
---
# <a name="eclrevent-enumeration"></a>EClrEvent – výčet
Najdete popis obvyklých událostí modulu runtime (CLR) jazyk, pro které hostitele může registrace zpětných volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`Event_ClrDisabled`|Určuje závažné chybě CLR.|  
|`Event_DomainUnload`|Určuje uvolnění konkrétní <xref:System.AppDomain>.|  
|`Event_MDAFired`|Určuje, že byla vygenerována zprávu spravované ladění Assistant (MDA).|  
|`Event_StackOverflow`|Určuje, že došlo k chybu přetečení zásobníku.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel může registrace zpětných volání pro všechny typy událostí popsaného `EClrEvent` voláním metod [iclroneventmanager –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) rozhraní. Hostitel voláním získá ukazatel toto rozhraní [iclrcontrol::getclrmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metoda.  
  
 `Event_CLRDisabled` a `Event_DomainUnload` události mohou být vyvolány více než jednou a z různých vláknech signál uvolnění nebo zakázání modulu CLR.  
  
 `Event_MDAFired` Událost se vyvolá vytvoření [mdainfo –](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance, který obsahuje podrobnosti zprávy (mda). Další informace o mda najdete v tématu [diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IActionOnCLREvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
