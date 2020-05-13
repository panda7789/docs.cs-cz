---
title: ICorDebugInstanceFieldSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 092f2a8acdffa9f91176bdf0ca10b8db9cff6d37
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209926"
---
# <a name="icordebuginstancefieldsymbol-interface"></a>ICorDebugInstanceFieldSymbol – rozhraní
Představuje informace o symbolech ladění pro pole instance.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetName – metoda](icordebuginstancefieldsymbol-getname-method.md)|Získá název pole instance.|  
|[GetOffset – metoda](icordebuginstancefieldsymbol-getoffset-method.md)|Získá posun v bajtech tohoto pole instance v nadřazené třídě.|  
|[GetSize – metoda](icordebuginstancefieldsymbol-getsize-method.md)|Získá velikost pole instance v bajtech.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugInstanceFieldSymbol`Rozhraní se používá k načtení informací o ladicím symbolu pro pole instance.  
  
> [!NOTE]
> Toto rozhraní je dostupné jenom pro .NET Native. Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugStaticFieldSymbol – rozhraní](icordebugstaticfieldsymbol-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
