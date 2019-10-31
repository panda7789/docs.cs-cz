---
title: Rozhraní ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 532052aa4f869861fbdb40ba0126bfd800eba942
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121866"
---
# <a name="icordebugvirtualunwinder-interface"></a>Rozhraní ICorDebugVirtualUnwinder
Poskytuje metody, které vám pomůžou při odvíjení zásobníku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Name|  
|------------|----------|  
|[GetContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|Získá aktuální kontext tohoto unwind.|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|Přejde do kontextu volajícího.|  
  
## <a name="remarks"></a>Poznámky  
 Členy rozhraní `ICorDebugVirtualUnwinder` jsou implementovány pomocí ladicího programu, aby bylo možné v zásobníku převinout zpět.  
  
> [!NOTE]
> Toto rozhraní je dostupné jenom pro .NET Native. Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
