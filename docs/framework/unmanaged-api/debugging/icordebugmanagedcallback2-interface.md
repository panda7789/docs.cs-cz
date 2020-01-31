---
title: ICorDebugManagedCallback2 – rozhraní
ms.date: 03/30/2017
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
ms.openlocfilehash: 43982ebb634843c0130c3321aa84c90b84e8c786
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793317"
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 – rozhraní
Poskytuje metody pro podporu zpracování výjimek ladicího programu a spravované pomocníky ladění (MDA). `ICorDebugManagedCallback2` je logické rozšíření rozhraní [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ChangeConnection – metoda](icordebugmanagedcallback2-changeconnection-method.md)|Oznamuje ladicímu programu, že se změnila sada úloh přidružených k zadanému připojení.|  
|[CreateConnection – metoda](icordebugmanagedcallback2-createconnection-method.md)|Oznamuje ladicímu programu, že bylo vytvořeno nové připojení.|  
|[DestroyConnection – metoda](icordebugmanagedcallback2-destroyconnection-method.md)|Oznamuje ladicímu programu, že zadané připojení bylo ukončeno.|  
|[Exception – metoda](icordebugmanagedcallback2-exception-method.md)|Oznamuje ladicímu programu, že bylo zahájeno hledání obslužné rutiny výjimky.|  
|[ExceptionUnwind – metoda](icordebugmanagedcallback2-exceptionunwind-method.md)|Poskytuje oznámení o stavu během procesu odvíjení výjimky.|  
|[FunctionRemapComplete – metoda](icordebugmanagedcallback2-functionremapcomplete-method.md)|Oznamuje ladicímu programu, že provádění kódu se přepnulo na novou verzi upravované funkce.|  
|[FunctionRemapOpportunity – metoda](icordebugmanagedcallback2-functionremapopportunity-method.md)|Oznamuje ladicímu programu, že provádění kódu dosáhlo bodu sekvence ve starší verzi upravované funkce.|  
|[MDANotification – metoda](icordebugmanagedcallback2-mdanotification-method.md)|Poskytuje oznámení o tom, že při provádění kódu došlo ke zprávě pomocníka spravovaného ladění (MDA).|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugManagedCallback2` rozšiřuje rozhraní `ICorDebugManagedCallback`, aby zpracovávala nové události ladění představené ve verzi .NET Framework 2,0.  
  
 Ladicí program musí implementovat `ICorDebugManagedCallback2`, pokud ladí aplikace .NET Framework 2,0. Instance `ICorDebugManagedCallback` nebo `ICorDebugManagedCallback2` je předána jako objekt zpětného volání do [ICorDebug:: SetManagedHandler –](icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
