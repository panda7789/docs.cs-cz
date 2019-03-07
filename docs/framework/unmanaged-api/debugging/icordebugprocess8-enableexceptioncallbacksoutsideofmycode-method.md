---
title: Metoda ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fc7f34059660c273055c3ee24fb6722fda1ef3f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466554"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>Metoda ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
[Podporované v [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] a novější verze]  
  
 Povolí nebo zakáže určité typy [icordebugmanagedcallback2 –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) zpětných volání výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `enableExceptionsOutsideOfJMC`  
 [in]  
  
## <a name="remarks"></a>Poznámky  
 Pokud hodnota `enableExceptionsOutsideOfJMC` je `false`:  
  
-   S výjimkou DEBUG_EXCEPTION_FIRST_CHANCE opozdí ve zpětném volání k ladicímu programu.  
  
-   S výjimkou DEBUG_EXCEPTION_CATCH_HANDLER_FOUND opozdí ve zpětném volání k ladicímu programu Pokud výjimka nikdy řídicí sekvence do uživatelského kódu (to znamená, cesty z výjimky původ na obslužnou rutinu výjimky nemá žádné metody označené jako JustMyCode nebo JMC).  
  
 Výchozí hodnota `enableExceptionsOutsideOfJMC` je `true`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugProcess8 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
