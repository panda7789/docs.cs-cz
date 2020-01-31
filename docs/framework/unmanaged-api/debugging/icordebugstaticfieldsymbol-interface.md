---
title: ICorDebugStaticFieldSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: b50b9c8435f19e1a77229f01dc85514f5f75c9f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791806"
---
# <a name="icordebugstaticfieldsymbol-interface"></a>ICorDebugStaticFieldSymbol – rozhraní
Představuje informace o symbolech ladění pro statické pole.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetAddress – metoda](icordebugstaticfieldsymbol-getaddress-method.md)|Získá adresu statického pole.|  
|[GetName – metoda](icordebugstaticfieldsymbol-getname-method.md)|Získá název statického pole.|  
|[GetSize – metoda](icordebugstaticfieldsymbol-getsize-method.md)|Získá velikost statického pole v bajtech.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugStaticFieldSymbol` slouží k načtení informací o ladicím symbolu pro statické pole.  
  
> [!NOTE]
> Toto rozhraní je dostupné jenom pro .NET Native. Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugInstanceFieldSymbol – rozhraní](icordebuginstancefieldsymbol-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
