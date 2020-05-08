---
title: ICorDebugController::EnumerateThreads – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
ms.openlocfilehash: 4d69f13d4716b43c815148ff0fe4aa087b57c6e5
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892759"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a>ICorDebugController::EnumerateThreads – metoda
Získá enumerátor pro aktivní spravovaná vlákna v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppThreads`  
 mimo Ukazatel na adresu objektu "ICorDebugThreadEnum", který představuje enumerátor pro všechna spravovaná vlákna, která jsou v procesu aktivní.  
  
## <a name="remarks"></a>Poznámky  
 Vlákno je považováno za aktivní po odeslání zpětného volání [ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) a před odesláním zpětného volání [ICorDebugManagedCallback:: ExitThread –](icordebugmanagedcallback-exitthread-method.md) . Spravované vlákno nemusí mít nutně žádné spravované snímky v zásobníku. Vlákna lze vyčíslit i před zpětným voláním [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) . Výčet bude přirozeně prázdný.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také
