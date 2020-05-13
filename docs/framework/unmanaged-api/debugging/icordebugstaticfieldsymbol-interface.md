---
title: ICorDebugStaticFieldSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: f9b82f0f98a668555a8096d7575c049c31cae93a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379443"
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
 `ICorDebugStaticFieldSymbol`Rozhraní se používá k načtení informací o ladicím symbolu pro statické pole.  
  
> [!NOTE]
> Toto rozhraní je dostupné jenom pro .NET Native. Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugInstanceFieldSymbol – rozhraní](icordebuginstancefieldsymbol-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
