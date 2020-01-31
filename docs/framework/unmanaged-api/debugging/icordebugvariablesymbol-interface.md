---
title: ICorDebugVariableSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 9d17bc92dcae9e906dfe18d7665fbf489d278234
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790861"
---
# <a name="icordebugvariablesymbol-interface"></a>ICorDebugVariableSymbol – rozhraní
Načte informace o ladicím symbolu pro proměnnou.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetName – metoda](icordebugvariablesymbol-getname-method.md)|Získá název proměnné.|  
|[GetSize – metoda](icordebugvariablesymbol-getsize-method.md)|Získá velikost proměnné v bajtech.|  
|[GetSlotIndex – metoda](icordebugvariablesymbol-getslotindex-method.md)|Načte index spravovaného slotu místní proměnné.|  
|[GetValue – metoda](icordebugvariablesymbol-getvalue-method.md)|Získá hodnotu proměnné jako bajtové pole.|  
|[SetValue – metoda](icordebugvariablesymbol-setvalue-method.md)|Přiřadí hodnotu bajtového pole proměnné.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní je dostupné jenom pro .NET Native. Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
