---
title: Rozhraní ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550cb6379ef0d5d17a3446b3f21120208b5a3dad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989162"
---
# <a name="icordebugdebugevent-interface"></a>Rozhraní ICorDebugDebugEvent
Definuje základní rozhraní, ze kterého jsou všechny `ICorDebug` výjimky ladění jsou odvozeny.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetEventKind – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|Jaký druh událostí označuje to `ICorDebugDebugEvent` objekt představuje.|  
|[GetThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|Získá vlákno, na kterém došlo k události.|  
  
## <a name="remarks"></a>Poznámky  
 Následující rozhraní jsou odvozeny z `ICorDebugDebugEvent` rozhraní:  
  
- [ICorDebugExceptionDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
- [Icordebugmoduledebugevent –](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  Rozhraní je pouze k dispozici s .NET Native. Pokus o volání `QueryInterface` načíst ukazatel rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
