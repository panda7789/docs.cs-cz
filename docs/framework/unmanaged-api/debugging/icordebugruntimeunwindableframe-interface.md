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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf6bc73683a6c37ceaaffc635a58803b71c3b6cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134196"
---
# <a name="icordebugruntimeunwindableframe-interface"></a>ICorDebugRuntimeUnwindableFrame – rozhraní
Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugRuntimeUnwindableFrame` je specializované verze icordebugframe – rozhraní. Používá se nespravované metody, které vyžadují modul runtime k uvolnění rámce aktuálního zásobníku. Existující odvíjení konvence nefungují, protože nepoužívají kód zkompilovaný kompilátorem JIT. Pokud ladicí program zobrazí neuvolnitelných rámce, měla by používat [icordebugstackwalk::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) metody k provedení operace unwind ji, ale měli provést kontrolu, samotného. Když ladicí program dostane `ICorDebugRuntimeUnwindableFrame`, může zavolat [icordebugstackwalk::getcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody k získání kontextu rámce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
