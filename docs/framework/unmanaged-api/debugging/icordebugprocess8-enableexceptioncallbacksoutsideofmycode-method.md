---
title: Metoda ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f08f24e16b34d911793b5c8d4a28168f7677b22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418965"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>Metoda ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
[V podporované [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] a novější verze]  
  
 Povolí nebo zakáže určité typy [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) zpětná volání výjimek.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `enableExceptionsOutsideOfJMC`  
 [v]  
  
## <a name="remarks"></a>Poznámky  
 Pokud hodnota `enableExceptionsOutsideOfJMC` je `false`:  
  
-   Výjimka DEBUG_EXCEPTION_FIRST_CHANCE nebude způsobit zpětné volání pro ladicí program.  
  
-   Výjimka DEBUG_EXCEPTION_CATCH_HANDLER_FOUND nebude za následek zpětné volání pro ladicí program Pokud výjimka řídicí sekvence nikdy do uživatelského kódu (tedy cesty z počátek výjimky na obslužnou rutinu výjimky nemá žádné metody označené jako JustMyCode nebo SVK).  
  
 Výchozí hodnota `enableExceptionsOutsideOfJMC` je `true`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugProcess8 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
