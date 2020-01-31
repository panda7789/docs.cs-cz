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
ms.openlocfilehash: 26b0c78d5b34b920decc8c549d90ba8147e3f323
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791921"
---
# <a name="icordebugruntimeunwindableframe-interface"></a>ICorDebugRuntimeUnwindableFrame – rozhraní
Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugRuntimeUnwindableFrame` je specializovaná verze rozhraní ICorDebugFrame. Používá je nespravované metody, které vyžadují, aby modul runtime odvíjí snímek v aktuálním zásobníku. Existující konvence unwindy nefungují, protože nepoužívají kód zkompilovaný JIT. Pokud se ladicí program dohlíží na nejenom nejenomný snímek, měl by použít metodu [ICorDebugStackWalk:: Next](icordebugstackwalk-next-method.md) k jejímu unwind, ale měla by provádět kontrolu. Když ladicí program obdrží `ICorDebugRuntimeUnwindableFrame`, může volat metodu [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) pro načtení kontextu rámce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
