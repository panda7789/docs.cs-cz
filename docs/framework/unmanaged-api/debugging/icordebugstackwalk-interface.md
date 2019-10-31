---
title: ICorDebugStackWalk – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
ms.openlocfilehash: 48f1b485b6dfa8fd898f6ea00eee2d7b397deba6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131859"
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk – rozhraní
Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|Vrátí kontext pro aktuální rámec v objektu `ICorDebugStackWalk`.|  
|[SetContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|Nastaví aktuální kontext objektu `ICorDebugStackWalk` na platný kontext vlákna.|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|Přesune objekt `ICorDebugStackWalk` k dalšímu snímku.|  
|[GetFrame – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|Získá aktuální rámec v objektu `ICorDebugStackWalk`.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
