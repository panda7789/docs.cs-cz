---
title: Rozhraní ICorDebugLoadedModule
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8f3a881a1beceb7d4aa35e2bd9a5e9e5419a391
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654864"
---
# <a name="icordebugloadedmodule-interface"></a>Rozhraní ICorDebugLoadedModule
Poskytuje informace o u načteného modulu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetBaseAddress – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|Získá základní adresu načteného modulu.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|Získá název načteného modulu.|  
|[GetSize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|Získá velikost v bajtech načteného modulu.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugLoadedModule` Rozhraní je implementováno ladicím programem a používá modul CLR rozhraní pro ladění a získat informace o modulu načteny z ladicího programu.  
  
> [!NOTE]
>  Toto rozhraní je pouze k dispozici s .NET Native. Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
