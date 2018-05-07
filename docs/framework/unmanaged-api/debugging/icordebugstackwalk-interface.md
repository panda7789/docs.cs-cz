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
ms.openlocfilehash: 612e0f84302d5bee6479264ef2dbba4c7152657e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk – rozhraní
Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|Vrátí kontext pro aktuální rámec v `ICorDebugStackWalk` objektu.|  
|[SetContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|Nastaví `ICorDebugStackWalk` aktuální kontext objektu, který má platný kontext pro vlákno.|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|Přesune `ICorDebugStackWalk` objektu na další snímek.|  
|[GetFrame – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|Získá aktuální rámec v `ICorDebugStackWalk` objektu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
