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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06ce2da435df9458ca59d76fa426becbede2e619
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959677"
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk – rozhraní
Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|Vrátí kontext pro aktuální rámec v `ICorDebugStackWalk` objektu.|  
|[SetContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|Nastaví aktuální kontext objektu na platný kontext pro vlákno. `ICorDebugStackWalk`|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|`ICorDebugStackWalk` Přesune objekt k dalšímu snímku.|  
|[GetFrame – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|Získá aktuální rámec v `ICorDebugStackWalk` objektu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
