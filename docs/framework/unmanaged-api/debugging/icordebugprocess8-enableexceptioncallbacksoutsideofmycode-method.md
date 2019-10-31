---
title: Metoda ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: b6bfd258f35f19719be5e5169a1edc22a358371c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123377"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>Metoda ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
[Podporováno v .NET Framework 4,6 a novějších verzích]  
  
 Povolí nebo zakáže určité typy zpětných volání výjimek [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `enableExceptionsOutsideOfJMC`  
 pro  
  
## <a name="remarks"></a>Poznámky  
 Pokud je hodnota `enableExceptionsOutsideOfJMC` `false`:  
  
- Výjimka DEBUG_EXCEPTION_FIRST_CHANCE nebude mít za následek zpětné volání ladicího programu.  
  
- Výjimka DEBUG_EXCEPTION_CATCH_HANDLER_FOUND nebude mít za následek zpětné volání ladicího programu, pokud výjimka nikdy neřídí kód uživatele (to znamená, že cesta z původ výjimky do obslužné rutiny výjimky nemá žádné metody označené jako JustMyCode nebo JMC).  
  
 Výchozí hodnota `enableExceptionsOutsideOfJMC` je `true`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess8 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
