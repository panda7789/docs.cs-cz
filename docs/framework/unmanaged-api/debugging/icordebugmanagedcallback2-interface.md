---
title: "ICorDebugManagedCallback2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2a46e8e4f23c57391877d8cb6ba6b35d50de151b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 – rozhraní
Poskytuje metody pro podporu zpracování výjimek ladicího programu a spravované pomocníky ladění (MDA). `ICorDebugManagedCallback2`je logické rozšíření [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) rozhraní.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ChangeConnection – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|Upozorní ladicí program, že se změnila sadu úloh, které jsou přidružené k zadané připojení.|  
|[CreateConnection – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|Upozorní ladicího programu vytvořený nové připojení.|  
|[DestroyConnection – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|Upozorní ladicí program, že zadané připojení se ukončilo.|  
|[Exception – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|Aby bylo zahájeno hledání pro obslužnou rutinu výjimky upozorní ladicího programu.|  
|[ExceptionUnwind – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|Poskytuje oznámení o stavu během procesu unwinding výjimka.|  
|[FunctionRemapComplete – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|Upozorní ladicí program, že provádění kódu přepnul na novou verzi upravená funkce.|  
|[FunctionRemapOpportunity – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|Upozorní ladicí program, že provádění kódu dosáhl bod sekvence ve starší verzi upravená funkce.|  
|[MDANotification – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|Poskytuje oznámení, že provádění kódu se vyskytla spravované ladění zprávy pomocníka (MDA).|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugManagedCallback2` Rozšiřuje rozhraní `ICorDebugManagedCallback` rozhraní pro zpracování nové události ladění byla zavedená v rozhraní .NET Framework verze 2.0.  
  
 Ladicí program musí implementovat `ICorDebugManagedCallback2` pokud ho je ladění aplikací rozhraní .NET Framework 2.0. Instance `ICorDebugManagedCallback` nebo `ICorDebugManagedCallback2` se předá jako objekt zpětného volání, který má [icordebug::setmanagedhandler –](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
