---
title: ICorDebugStaticFieldSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f4e245e96ac9d47db10072e50a5b3c516d5dd27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962682"
---
# <a name="icordebugstaticfieldsymbol-interface"></a>ICorDebugStaticFieldSymbol – rozhraní
Představuje informace o symbolech ladění pro statické pole.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetAddress – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|Získá adresu statického pole.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|Získá název statického pole.|  
|[GetSize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|Získá velikost statického pole v bajtech.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugStaticFieldSymbol` Rozhraní se používá k načtení informací o ladicím symbolu pro statické pole.  
  
> [!NOTE]
> Toto rozhraní je dostupné jenom pro .NET Native. Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugInstanceFieldSymbol – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
