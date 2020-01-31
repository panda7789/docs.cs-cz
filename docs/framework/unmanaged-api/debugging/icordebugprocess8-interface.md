---
title: Rozhraní ICorDebugProcess8
ms.date: 03/30/2017
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
ms.openlocfilehash: 813afc047f9fda060f1cf1af780336ff8b7c18be
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792153"
---
# <a name="icordebugprocess8-interface"></a>Rozhraní ICorDebugProcess8
[Podporováno v .NET Framework 4,6 a novějších verzích]  
  
 Logicky rozšiřuje rozhraní ICorDebugProcess a povoluje nebo zakazuje určité typy zpětných volání výjimek [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnableExceptionCallbacksOutsideOfMyCode – metoda](icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|Povolí nebo zakáže určité typy zpětných volání výjimek [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
