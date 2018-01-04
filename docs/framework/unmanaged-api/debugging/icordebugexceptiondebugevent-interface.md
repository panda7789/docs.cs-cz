---
title: "Rozhraní ICorDebugExceptionDebugEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97bbd9374b8a3f938f42b8ddd001049a2e7a324c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugevent-interface"></a>Rozhraní ICorDebugExceptionDebugEvent
Rozšiřuje [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) rozhraní pro podporu událostí výjimky.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetFlags – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|Získá a příznak, který určuje, zda výjimku může zachytit.|  
|[GetNativeIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|Získá ukazatel nativní rozhraní pro tuto událost výjimky ladění.|  
|[GetStackPointer – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|Získá ukazatel zásobníku pro tuto událost výjimky ladění.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugExceptionDebugEvent` Rozhraní je implementováno modulem následující typy událostí:  
  
-   [MANAGED_EXCEPTION_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [MANAGED_EXCEPTION_USER_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [MANAGED_EXCEPTION_UNHANDLED](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
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
