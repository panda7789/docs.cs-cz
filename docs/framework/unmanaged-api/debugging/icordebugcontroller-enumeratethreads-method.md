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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a4bb4072c574edeac1c531978fac75595c252e0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481596"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a>ICorDebugController::EnumerateThreads – metoda
Získá enumerátor pro aktivní spravovaná vlákna v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppThreads`  
 [out] Ukazatel na adresu objektu "icordebugthreadenum –", který představuje enumerátor pro všechna spravovaná vlákna, které jsou aktivní v procesu.  
  
## <a name="remarks"></a>Poznámky  
 Vlákno se považuje za aktivní po [icordebugmanagedcallback::CreateThread –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) byly odeslány zpětného volání a před [icordebugmanagedcallback::ExitThread –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) zpětného volání byly odeslány. . Spravované vlákno nemusí mít nutně žádné spravované bloky na svůj zásobník. Vlákna mohou být ještě před uvedené [icordebugmanagedcallback::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) zpětného volání. Výčet přirozeně bude prázdný.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

