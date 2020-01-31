---
title: ICorDebugManagedCallback3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
ms.openlocfilehash: b97f29b94ed4fad6892697ca1c7ed4a20c99c03e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793269"
---
# <a name="icordebugmanagedcallback3-interface"></a>ICorDebugManagedCallback3 – rozhraní
Poskytuje metodu zpětného volání, která určuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CustomNotification – metoda](icordebugmanagedcallback3-customnotification-method.md)|Indikuje, že se aktivovalo oznámení o povoleném vlastním ladicím programu.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je logické rozšíření rozhraní [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) a [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
- [ICorDebugManagedCallback2 – rozhraní](icordebugmanagedcallback2-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
