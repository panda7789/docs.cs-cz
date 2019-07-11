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
ms.openlocfilehash: f1e003ba23f680c4a5525a956d758aac6b823eb9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769705"
---
# <a name="eclrevent-enumeration"></a>EClrEvent – výčet
Najdete popis obvyklých událostí modulu runtime (CLR) jazyk, pro které hostitele může registrace zpětných volání.  
  
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
|`Event_ClrDisabled`|Určuje závažná chyba CLR.|  
|`Event_DomainUnload`|Určuje uvolnění konkrétní <xref:System.AppDomain>.|  
|`Event_MDAFired`|Určuje, zda byl vytvořen zprávu spravované ladění Assistant (MDA).|  
|`Event_StackOverflow`|Určuje, že došlo k chybě přetečení zásobníku.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel může registrace zpětných volání pro všechny typy událostí popsal `EClrEvent` voláním metod [iclroneventmanager –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) rozhraní. Hostitel získá ukazatel na toto rozhraní voláním [iclrcontrol::getclrmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody.  
  
 `Event_CLRDisabled` a `Event_DomainUnload` události mohou být vyvolány více než jednou a z různých vláken, který signalizuje, že uvolnění z paměti nebo vypnutí CLR.  
  
 `Event_MDAFired` Vyvolává událost vytvoření [mdainfo –](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance, která obsahuje podrobnosti o zprávě MDA. Další informace o mda najdete v tématu [diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IActionOnCLREvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
