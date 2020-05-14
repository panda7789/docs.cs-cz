---
title: Rozhraní ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 59ecf3da4b44af7b04dec26fbc3ea182c185d04a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396456"
---
# <a name="icordebugvirtualunwinder-interface"></a>Rozhraní ICorDebugVirtualUnwinder
Poskytuje metody, které vám pomůžou při odvíjení zásobníku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Name|  
|------------|----------|  
|[GetContext – metoda](icordebugvirtualunwinder-getcontext-method.md)|Získá aktuální kontext tohoto unwind.|  
|[Next – metoda](icordebugvirtualunwinder-next-method.md)|Přejde do kontextu volajícího.|  
  
## <a name="remarks"></a>Poznámky  
 Členové `ICorDebugVirtualUnwinder` rozhraní jsou implementováni pomocí ladicího programu, aby mohli pomáhat při uvolňování zásobníku.  
  
> [!NOTE]
> Toto rozhraní je dostupné jenom pro .NET Native. Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
