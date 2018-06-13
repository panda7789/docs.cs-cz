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
ms.openlocfilehash: 3e2edc64cd9067ed89ae0e309c6a5630319ce835
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420596"
---
# <a name="icordebugruntimeunwindableframe-interface"></a>ICorDebugRuntimeUnwindableFrame – rozhraní
Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugRuntimeUnwindableFrame` je specializovanou verzi rozhraní ICorDebugFrame. Používá se nespravované metody, které vyžadují modulu runtime unwind rámce v aktuální zásobníku. Existující unwinding konvence nefungují, protože nepoužívají kompilována kódu. Když ladicí program zobrazí unwindable rámečku, měla by používat [icordebugstackwalk::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) metodu unwind ji, ale měli provést kontroly sám sebe. Když obdrží ladicí program `ICorDebugRuntimeUnwindableFrame`, může zavolat [icordebugstackwalk::getcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metoda pro načtení kontextu rámce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
