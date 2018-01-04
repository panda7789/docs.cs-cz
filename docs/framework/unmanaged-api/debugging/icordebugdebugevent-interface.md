---
title: "Rozhraní ICorDebugDebugEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c4d777d601866ca9600a7e2b88aca8854f32a17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdebugevent-interface"></a>Rozhraní ICorDebugDebugEvent
Definuje základní rozhraní, ze kterého jsou všechny `ICorDebug` odvozena ladění událostí.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetEventKind – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|Určuje, jaký druh událostí to `ICorDebugDebugEvent` objekt představuje.|  
|[GetThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|Získá vláken, na kterém došlo k události.|  
  
## <a name="remarks"></a>Poznámky  
 Následující rozhraní jsou odvozeny od `ICorDebugDebugEvent` rozhraní:  
  
-   [ICorDebugExceptionDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [ICorDebugModuleDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  Rozhraní je k dispozici s .NET Native pouze. Probíhá pokus o volání `QueryInterface` načíst ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
