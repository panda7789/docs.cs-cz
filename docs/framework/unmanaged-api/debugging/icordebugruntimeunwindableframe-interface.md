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
ms.openlocfilehash: a7b0608e85411844828cebea34c0ce5ef5b1bd11
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379388"
---
# <a name="icordebugruntimeunwindableframe-interface"></a>ICorDebugRuntimeUnwindableFrame – rozhraní
Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugRuntimeUnwindableFrame`je specializovaná verze rozhraní ICorDebugFrame. Používá je nespravované metody, které vyžadují, aby modul runtime odvíjí snímek v aktuálním zásobníku. Existující konvence unwindy nefungují, protože nepoužívají kód zkompilovaný JIT. Pokud se ladicí program dohlíží na nejenom nejenomný snímek, měl by použít metodu [ICorDebugStackWalk:: Next](icordebugstackwalk-next-method.md) k jejímu unwind, ale měla by provádět kontrolu. Když ladicí program obdrží `ICorDebugRuntimeUnwindableFrame` , může zavolat metodu [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) pro načtení kontextu rámce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
