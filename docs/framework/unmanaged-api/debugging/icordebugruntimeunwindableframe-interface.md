---
title: ICorDebugRuntimeUnwindableFrame – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
ms.openlocfilehash: 2902744b6af3c7b2bd4def73b04807ce3333a8a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131889"
---
# <a name="icordebugruntimeunwindableframe-interface"></a>ICorDebugRuntimeUnwindableFrame – rozhraní
Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugRuntimeUnwindableFrame` je specializovaná verze rozhraní ICorDebugFrame. Používá je nespravované metody, které vyžadují, aby modul runtime odvíjí snímek v aktuálním zásobníku. Existující konvence unwindy nefungují, protože nepoužívají kód zkompilovaný JIT. Pokud se ladicí program dohlíží na nejenom nejenomný snímek, měl by použít metodu [ICorDebugStackWalk:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) k jejímu unwind, ale měla by provádět kontrolu. Když ladicí program obdrží `ICorDebugRuntimeUnwindableFrame`, může volat metodu [ICorDebugStackWalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) pro načtení kontextu rámce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
